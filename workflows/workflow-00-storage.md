# Workflow 00 — Storage

**Status: IMPLEMENTED / E2E PARTIAL**

## Tujuan
Menetapkan jalur penyimpanan berdasarkan jenis output sebelum aset diteruskan ke workflow berikutnya.

## Aturan utama

- **Cloudinary = konten/media dan asset delivery yang membutuhkan URL asset publik**
- **Adobe Express = storage/master workspace untuk desain/dokumen yang memang dapat dipertahankan di Adobe; Published Link dipakai untuk preview/promosi**
- **Box = file/dokumen yang memang membutuhkan lane file umum dan telah terbukti**
- **MR.ONE Agent = orchestrator**; bukan tempat penyimpanan.

## Routing logic

```
MR.ONE Agent
    |
    +-- MEDIA / KONTEN -----------------> Cloudinary
    |                                      |
    |                                      +--> asset URL / reference
    |
    +-- ADOBE DESIGN / DOCUMENT --------> Adobe Express
    |                                      |
    |                                      +--> master/editor/preview
    |                                      +--> Published Link -> public preview/promotion
    |                                      +--> separate delivery file -> customer download
    |
    +-- FILE / DOKUMEN -----------------> Box
                                           |
                                           +--> file ID / content reference
```

## Cloudinary lane

Gunakan untuk:
- gambar
- video
- thumbnail
- cover
- promo media
- asset marketing
- media lain yang membutuhkan asset URL publik dan sesuai batas Cloudinary.

Alur:

```
GPT -> Cloudinary -> stored asset -> URL/reference -> next workflow
```

**Terbukti:** upload aset gambar kecil, penyimpanan, pengambilan metadata, dan URL publik berhasil E2E.

**Belum terbukti E2E:** upload video nyata melalui connector dan konsumsi video oleh publisher.

**Batas yang telah diaudit:** image/raw max 10 MB; video max 100 MB pada konfigurasi Cloudinary yang diuji. Batas ini tidak boleh dicampur dengan batas Adobe Express.

## Adobe Express lane

Gunakan sebagai **storage/master workspace tambahan** untuk desain/dokumen yang cocok dikelola di Adobe Express.

Cocok untuk:
- desain;
- planner;
- checklist/worksheet;
- printable;
- dokumen visual;
- template;
- aset desain lain yang tetap dikelola di Adobe Express.

### Capability yang sudah PASS melalui connector

- search template;
- membuat instance desain dari template melalui fill_text (PASS pada pengujian sebelumnya);
- perubahan background;
- animasi desain;
- export PDF;
- hasil export PDF dapat dikirim ke Cloudinary dan diambil kembali E2E.

**E2E terbukti:**

```
Adobe Express
    -> Export PDF
    -> Cloudinary
    -> Retrieve/Verify
    = PASS
```

### Published Link: preview/promosi

Published Link Adobe Express telah diuji nyata:

```
Adobe document
    -> Published Link
    -> dibuka tanpa login
    -> halaman publik tampil
    = PASS E2E
```

Hasil tes:
- Published Link dapat dibuat: **PASS**
- dapat dibuka tanpa login: **PASS E2E**
- tampil sebagai halaman publik: **PASS E2E**
- digunakan untuk preview/promosi: **PASS**
- direct-download file asli dari halaman publik: **TIDAK TERBUKTI / TIDAK DIGUNAKAN**

Karena halaman publik yang diuji tidak menyediakan jalur download file produk asli, **Published Link tidak boleh diperlakukan sebagai customer-download URL**.

### Pemisahan master, preview, dan delivery

Untuk produk digital:

```
ADOBE EXPRESS
    |
    +--> MASTER / WORKSPACE
    |
    +--> PUBLISHED LINK
    |      +--> PREVIEW / PROMOSI
    |
    +--> SEPARATE DELIVERY FILE
           +--> CUSTOMER DOWNLOAD
```

Manual ringan untuk membuat Published Link diperbolehkan karena hanya satu langkah publikasi/berbagi dan tidak mengubah fungsi utama storage. MR.ONE tetap mencatat reference/link dan statusnya.

**Reference:** editor URL, preview URL, dan Published Link dapat digunakan sebagai reference sesuai hasil operasi. Published Link adalah reference publik/preview, bukan pengganti file delivery.

**Batas Adobe yang telah diaudit:** Adobe Express Free memiliki 5 GB account storage. Batas input PDF yang telah diverifikasi adalah hingga 99 MB; ini berbeda dari storage 5 GB. Karena Cloudinary raw yang diuji memiliki batas 10 MB, PDF Adobe di atas batas Cloudinary tersebut tidak otomatis dapat dipindahkan ke Cloudinary tanpa transformasi/optimasi atau storage lane lain.

## Standar identitas aset Adobe

Setiap produk yang memakai Adobe Express sebagai master harus membedakan minimal:
- **Product ID**
- **Master title / nama produk**
- **Master file/document**
- **Version**
- **Preview/Published Link**
- **Delivery file**
- **Delivery reference/link**
- **QC status**

Jangan menggunakan Published Link sebagai pengganti file delivery.

## Box lane

Gunakan untuk:
- PDF
- ZIP
- dokumen
- file produk
- berkas lain yang diperlakukan sebagai file

Alur:

```
GPT -> Box -> stored file -> file ID/content reference -> next workflow
```

**Terbukti:** penyimpanan dan pembacaan file teks melalui connector.

**Belum terbukti E2E:** upload binary otomatis (mis. PDF/ZIP) melalui connector.

## Batasan

- Jangan menyimpan semua file secara otomatis di satu storage.
- Pilih storage berdasarkan jenis materi, kebutuhan delivery, batas ukuran, dan capability yang sudah PASS.
- Jangan menyamakan Adobe Published Link dengan direct-download URL.
- Adobe Published Link = **preview/promosi**.
- File delivery pembeli = **aset/file terpisah**.
- Jangan menjadikan Cloudinary sebagai satu-satunya storage jika Adobe Express sudah terbukti cocok untuk kelas aset tertentu.
- Jangan menganggap lane yang belum E2E tested sebagai PASS.
- Jangan menambahkan publisher atau platform baru ke workflow Storage.

## Acceptance criteria

1. Jenis output dapat diklasifikasikan.
2. MEDIA diarahkan ke Cloudinary bila sesuai.
3. Adobe-native design/document dapat diarahkan ke Adobe Express sebagai master/workspace.
4. Published Link Adobe dapat digunakan untuk preview/promosi.
5. Customer download menggunakan delivery file/reference terpisah.
6. FILE diarahkan ke Box bila lane tersebut terbukti sesuai.
7. MR.ONE Agent hanya mengorkestrasi dan meneruskan reference.
8. Status setiap lane membedakan **terbukti** dan **belum terbukti**.

## Checkpoint

**Patched:** 2026-10-02  
**Evidence basis:** Cloudinary media E2E; Box text-file E2E; Adobe Express design/export E2E; Adobe Express → Cloudinary E2E; Adobe Published Link public-access E2E.
