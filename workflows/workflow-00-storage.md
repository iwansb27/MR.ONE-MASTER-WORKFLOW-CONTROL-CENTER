# Workflow 00 — Storage

**Status: IMPLEMENTED / E2E PARTIAL**

## Tujuan
Menetapkan jalur penyimpanan berdasarkan jenis output sebelum aset diteruskan ke workflow berikutnya.

## Aturan utama

- **Cloudinary = konten/media**
- **Box = file/dokumen**
- **MR.ONE Agent = orchestrator**; bukan tempat penyimpanan.

## Routing logic

```
MR.ONE Agent
    |
    +-- MEDIA / KONTEN ------> Cloudinary
    |                           |
    |                           +--> asset URL / reference
    |
    +-- FILE / DOKUMEN ------> Box
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

Alur:

```
GPT -> Cloudinary -> stored asset -> URL/reference -> next workflow
```

**Terbukti:** upload aset gambar kecil, penyimpanan, pengambilan metadata, dan URL publik berhasil E2E.

**Belum terbukti E2E:** upload video nyata melalui connector dan konsumsi video oleh publisher.

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

- Jangan menyimpan media di Box hanya karena formatnya adalah file.
- Jangan menjadikan Cloudinary sebagai penyimpanan dokumen/file produk.
- Jangan menganggap lane yang belum E2E tested sebagai PASS.
- Jangan menambahkan publisher atau platform baru ke workflow Storage.

## Acceptance criteria

1. Jenis output dapat diklasifikasikan sebagai **MEDIA** atau **FILE**.
2. MEDIA diarahkan ke Cloudinary.
3. FILE diarahkan ke Box.
4. MR.ONE Agent hanya mengorkestrasi dan meneruskan reference.
5. Status setiap lane membedakan **terbukti** dan **belum terbukti**.

## Checkpoint

**Implemented:** 2026-10-02  
**Evidence basis:** Cloudinary media E2E dan Box text-file E2E yang telah diuji sebelumnya.
