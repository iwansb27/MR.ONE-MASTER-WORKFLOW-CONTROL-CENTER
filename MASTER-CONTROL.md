# MR.ONE MASTER CONTROL

**Status:** ACTIVE — MASTER INDEX  
**Versi:** 1.1  
**Fungsi:** Peta utama MR.ONE untuk menemukan paket pekerjaan, aturan, tools/connectors, checkpoint, dan lokasi pekerjaan tanpa mencampur pekerjaan antar-domain.

## 1. Prinsip

**MASTER CONTROL = PETA, BUKAN TEMPAT PRODUKSI.**

Master Control tidak menjadi production center, storage aset, atau tempat mencampur seluruh pekerjaan. Pekerjaan nyata tetap berada di aplikasi/repository/storage masing-masing.

Struktur:

**MASTER CONTROL → PAKET PEKERJAAN → ATURAN PAKET → WORKFLOW → PEKERJAAN NYATA**

Setiap paket berdiri sebagai domain kerja terpisah. Paket baru dapat ditambahkan tanpa mengubah paket yang sudah ada.

## 2. Paket Pekerjaan

| Paket | Nama | Fungsi | Status | Isi utama | Auto Checkpoint |
|---|---|---|---|---|---|
| 01 | Digital Product + Marketing | Produk digital dari WHAT TO MAKE sampai marketing/publishing | ACTIVE | WF-00–WF-04 | `packages/P01-AUTO-CHECKPOINT.md` |
| 02 | Recording / Meeting / Bar Files | Rekaman, meeting, bar files, dan pengelolaan hasil rekaman | PLANNED | Akan diisi setelah audit | `packages/P02-AUTO-CHECKPOINT.md` |
| 03 | Building / App & Tool Development | Pembuatan dan pengembangan aplikasi/tool | PLANNED | Akan diisi setelah audit | `packages/P03-AUTO-CHECKPOINT.md` |
| 04 | Content / Video | Pekerjaan konten/video yang berdiri sebagai domain tersendiri | PLANNED | Akan diisi setelah audit | `packages/P04-AUTO-CHECKPOINT.md` |
| 05+ | Paket tambahan | Domain baru sesuai kebutuhan | EXTENSIBLE | Dibuat hanya bila diperlukan | Wajib dibuat bersama paket |

**Catatan penting:** WF-00–WF-04 tetap satu kesatuan di **Paket 01**. Tidak dipecah menjadi paket terpisah.

## 3. Auto Checkpoint Per Paket

**Checkpoint operasional utama berada di dalam masing-masing paket.**

Setiap paket memiliki satu file **AUTO CHECKPOINT** yang menyimpan posisi terakhir paket tersebut secara mandiri.

Aturan:
- Status Paket 01 tidak mengubah status Paket 02.
- Pekerjaan Paket 03 tidak menimpa checkpoint Paket 04.
- Jika satu paket tertunda, status tertundanya tetap terlihat sampai paket itu dilanjutkan.
- Saat pekerjaan dalam suatu paket berubah, **AUTO CHECKPOINT paket tersebut** yang diperbarui.
- Master Control hanya menunjuk ke checkpoint paket; tidak mengambil alih detailnya.

### Global checkpoint

`CHECKPOINT-HARIAN.md` di root sekarang berfungsi sebagai **GLOBAL SNAPSHOT / INDEX STATUS**, bukan sebagai tempat detail checkpoint setiap pekerjaan.

Global snapshot boleh merangkum status paket, tetapi detail posisi, pekerjaan terakhir, yang tertunda, hambatan, dan langkah berikutnya berada di AUTO CHECKPOINT paket masing-masing.

## 4. Paket 01 — Digital Product + Marketing

**Tujuan:** mengelola alur produk digital dan pemasaran berdasarkan workflow yang sudah terbukti/didokumentasikan.

### Workflow di dalam Paket 01

- **WF-00 Storage** → aturan routing storage.
- **WF-01 Publisher** → publishing dan verifikasi status.
- **WF-02 Production Engine** → HOW TO MAKE, capability, recipe, produksi, QC.
- **WF-03 Digital Product** → WHAT TO MAKE, product/material registry.
- **WF-04 Product Marketing / Explainer** → menjelaskan dan memasarkan produk jadi.

### Rantai utama

**WF-03 WHAT TO MAKE → WF-02 HOW TO MAKE → QC → WF-00 STORAGE → WF-04 MARKETING → WF-01 PUBLISHER**

### Capability yang saat ini tercatat PASS

- **Adobe Express** → Design/PDF.
- **Airtable** → Data/Formula/Tracker.
- **Cloudinary** → Media/Video Transformation.
- **Metricool** → Publisher pada jalur yang sudah terbukti.

Detail dan status resmi tetap berada di file workflow masing-masing.

## 5. Cara Menggunakan Master Control

Saat GPT menerima pekerjaan MR.ONE:

1. Masuk melalui **STARTUP-GATE.md**.
2. Baca **MASTER-CONTROL.md** untuk mengetahui paket/domain.
3. Tentukan paket berdasarkan jenis pekerjaan.
4. Buka dokumen paket tersebut.
5. Baca **AUTO CHECKPOINT paket tersebut**.
6. Ikuti workflow lokal yang dirujuk paket.
7. Verifikasi tools/connectors sebelum eksekusi.
8. Untuk perubahan teknis yang memerlukan persetujuan owner, tunggu **LANJUTKAN**.

Jika pekerjaan tidak cocok dengan paket yang tersedia, **jangan memasukkannya secara diam-diam** ke paket lain. Tandai sebagai kebutuhan paket baru atau minta keputusan owner.

## 6. Informasi yang Wajib Dimiliki Setiap Paket

Setiap dokumen paket harus menjelaskan:
- tujuan paket;
- jenis pekerjaan;
- batas paket;
- workflow yang termasuk;
- tools/apps;
- connectors;
- storage;
- **AUTO CHECKPOINT**;
- lokasi pekerjaan nyata;
- status PASS / FAIL / UNTESTED / BLOCKED / PLANNED;
- aturan lintas-paket bila ada.

## 7. Aturan Pemisahan

- Satu paket = satu domain pekerjaan.
- Satu paket = satu AUTO CHECKPOINT operasional.
- Workflow di dalam paket tidak boleh dipindahkan hanya untuk merapikan tampilan.
- Aset tidak dipindahkan ke Master Control hanya karena terdaftar di sana.
- Tool/connector hanya dicatat bila relevan dan statusnya dapat diverifikasi.
- Master Control menunjuk lokasi pekerjaan; Master Control bukan lokasi pekerjaan itu sendiri.
- Penambahan paket dilakukan secara terkontrol.

## 8. Checkpoint Master Control

**Tanggal:** 2026-10-03

**Status pekerjaan:** STRUKTUR AUTO CHECKPOINT PER PAKET DITERAPKAN.

**Sudah dibuat:**
- Master Control index.
- Registry Paket 01–04 + struktur extensible 05+.
- AUTO CHECKPOINT terpisah untuk Paket 01–04.
- Paket 01 mengikat WF-00–WF-04 sebagai satu kesatuan.
- Root `CHECKPOINT-HARIAN.md` ditetapkan sebagai global snapshot/index.
- Paket 02–04 tetap terpisah dan tidak tercampur ke Paket 01.

**Belum dilakukan:**
- Rename repository.
- Pengisian detail workflow Paket 02–04.
- Perubahan struktur workflow lama.

**Aturan:** jangan rename repo sebelum struktur Master Control dan UI terbukti sesuai.
