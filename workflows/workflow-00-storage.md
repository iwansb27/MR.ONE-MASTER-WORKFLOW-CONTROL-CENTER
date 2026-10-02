# Workflow 00 — Storage

**Status: IMPLEMENTED / E2E PARTIAL**

## Tujuan
Menetapkan jalur penyimpanan berdasarkan jenis output sebelum aset diteruskan ke workflow berikutnya.

## Aturan utama

- **Cloudinary = konten/media dan asset delivery yang membutuhkan URL asset publik**
- **Adobe Express = storage/master workspace untuk desain/dokumen yang memang dapat dipertahankan di Adobe dan delivery-nya melalui link Adobe yang sesuai**
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
    |                                      +--> Adobe editor/preview/published reference
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

Gunakan sebagai **storage/master workspace tambahan**, bukan pengganti universal Cloudinary.

Cocok untuk:
- desain;
- planner;
- checklist/worksheet;
- printable;
- dokumen visual;
- template;
- aset desain lain yang tetap dikelola di Adobe Express.

Yang sudah terbukti melalui connector:
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

**Reference:** Adobe Express menghasilkan editor URL dan preview URL pada operasi desain yang diuji.

**PENTING:** Published/share link Adobe belum dianggap sebagai **direct-download delivery link** sampai diuji secara nyata sebagai pengguna publik. Jadi untuk saat ini:
- Adobe Published/Share Link = **REFERENCE / ACCESS candidate**
- Direct download customer = **UNTESTED**
- Cloudinary delivery URL = tetap digunakan bila delivery file/media langsung memang dibutuhkan dan batas storage terpenuhi.

**Batas Adobe yang telah diaudit:** Adobe Express Free memiliki 5 GB account storage. Batas input PDF yang telah diverifikasi adalah hingga 99 MB; ini berbeda dari storage 5 GB. Karena Cloudinary raw yang diuji memiliki batas 10 MB, PDF Adobe di atas batas Cloudinary tersebut tidak otomatis dapat dipindahkan ke Cloudinary tanpa transformasi/optimasi atau storage lane lain.

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
- Jangan menyamakan Adobe Published/Share Link dengan direct-download URL tanpa uji.
- Jangan menjadikan Cloudinary sebagai satu-satunya storage jika Adobe Express sudah terbukti cocok untuk kelas aset tertentu.
- Jangan menganggap lane yang belum E2E tested sebagai PASS.
- Jangan menambahkan publisher atau platform baru ke workflow Storage.

## Acceptance criteria

1. Jenis output dapat diklasifikasikan.
2. MEDIA diarahkan ke Cloudinary bila sesuai.
3. Adobe-native design/document dapat diarahkan ke Adobe Express bila persistence dan delivery requirement terpenuhi.
4. FILE diarahkan ke Box bila lane tersebut terbukti sesuai.
5. MR.ONE Agent hanya mengorkestrasi dan meneruskan reference.
6. Status setiap lane membedakan **terbukti** dan **belum terbukti**.

## Checkpoint

**Patched:** 2026-10-02  
**Evidence basis:** Cloudinary media E2E; Box text-file E2E; Adobe Express design/export E2E dan Adobe Express → Cloudinary E2E.
