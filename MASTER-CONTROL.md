# MR.ONE MASTER CONTROL

**Status:** ACTIVE — MASTER INDEX  
**Versi:** 1.0  
**Fungsi:** Peta utama MR.ONE untuk menemukan paket pekerjaan, aturan, tools/connectors, checkpoint, dan lokasi pekerjaan tanpa mencampur pekerjaan antar-domain.

## 1. Prinsip

**MASTER CONTROL = PETA, BUKAN TEMPAT PRODUKSI.**

Master Control tidak menjadi production center, storage aset, atau tempat mencampur seluruh pekerjaan. Pekerjaan nyata tetap berada di aplikasi/repository/storage masing-masing.

Struktur:

**MASTER CONTROL → PAKET PEKERJAAN → ATURAN PAKET → WORKFLOW → PEKERJAAN NYATA**

Setiap paket berdiri sebagai domain kerja terpisah. Paket baru dapat ditambahkan tanpa mengubah paket yang sudah ada.

## 2. Paket Pekerjaan

| Paket | Nama | Fungsi | Status | Isi utama |
|---|---|---|---|---|
| 01 | Digital Product + Marketing | Produk digital dari WHAT TO MAKE sampai marketing/publishing | ACTIVE | WF-00–WF-04 |
| 02 | Recording / Meeting / Bar Files | Rekaman, meeting, bar files, dan pengelolaan hasil rekaman | PLANNED | Akan diisi setelah audit |
| 03 | Building / App & Tool Development | Pembuatan dan pengembangan aplikasi/tool | PLANNED | Akan diisi setelah audit |
| 04 | Content / Video | Pekerjaan konten/video yang berdiri sebagai domain tersendiri | PLANNED | Akan diisi setelah audit |
| 05+ | Paket tambahan | Domain baru sesuai kebutuhan | EXTENSIBLE | Dibuat hanya bila diperlukan |

**Catatan penting:** WF-00–WF-04 tetap satu kesatuan di **Paket 01**. Tidak dipecah menjadi paket terpisah.

## 3. Paket 01 — Digital Product + Marketing

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

## 4. Cara Menggunakan Master Control

Saat GPT menerima pekerjaan MR.ONE:

1. Masuk melalui **STARTUP-GATE.md**.
2. Baca **MASTER-CONTROL.md** untuk mengetahui paket/domain.
3. Tentukan paket berdasarkan jenis pekerjaan.
4. Buka dokumen paket tersebut.
5. Ikuti workflow lokal yang dirujuk paket.
6. Baca checkpoint yang relevan.
7. Verifikasi tools/connectors sebelum eksekusi.
8. Untuk perubahan teknis yang memerlukan persetujuan owner, tunggu **LANJUTKAN**.

Jika pekerjaan tidak cocok dengan paket yang tersedia, **jangan memasukkannya secara diam-diam** ke paket lain. Tandai sebagai kebutuhan paket baru atau minta keputusan owner.

## 5. Informasi yang Wajib Dimiliki Setiap Paket

Setiap dokumen paket harus menjelaskan:

- tujuan paket;
- jenis pekerjaan;
- batas paket;
- workflow yang termasuk;
- tools/apps;
- connectors;
- storage;
- checkpoint;
- lokasi pekerjaan nyata;
- status PASS / FAIL / UNTESTED / BLOCKED / PLANNED;
- aturan lintas-paket bila ada.

## 6. Aturan Pemisahan

- Satu paket = satu domain pekerjaan.
- Workflow di dalam paket tidak boleh dipindahkan hanya untuk merapikan tampilan.
- Aset tidak dipindahkan ke Master Control hanya karena terdaftar di sana.
- Tool/connector hanya dicatat bila relevan dan statusnya dapat diverifikasi.
- Master Control menunjuk lokasi pekerjaan; Master Control bukan lokasi pekerjaan itu sendiri.
- Penambahan paket dilakukan secara terkontrol.

## 7. Checkpoint Master Control

**Tanggal:** 2026-10-03

**Status pekerjaan:** DESAIN MASTER CONTROL DITERAPKAN.

**Sudah dibuat:**
- Master Control index.
- Registry Paket 01–04 + struktur extensible 05+.
- Paket 01 mengikat WF-00–WF-04 sebagai satu kesatuan.
- Paket 02–04 ditandai PLANNED agar pekerjaan baru tidak tercampur ke Paket 01.

**Belum dilakukan:**
- Rename repository.
- Pembangunan UI dashboard final.
- Pengisian detail Paket 02–04.
- Pemindahan/penyusunan ulang workflow lama.

**Aturan:** jangan rename repo sebelum struktur Master Control dan UI terbukti sesuai.
