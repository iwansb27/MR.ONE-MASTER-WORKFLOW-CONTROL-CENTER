# PAKET 01 — KATALOG PRODUK AWAL MR.ONE

**Versi:** 1.0
**Status:** INITIAL CATALOG / ENGINE-CONSTRAINED
**Tanggal:** 04 Oktober 2026

## Aturan Katalog

Katalog ini mengikuti ketentuan Workflow 02 — Production Engine:
- Hanya engine/capability yang berstatus **PASS** yang boleh menjadi jalur produksi resmi.
- **Adobe Express** = Design/PDF.
- **Airtable** = Data/Formula/Tracker.
- **Cloudinary** = Media/Video Transformation.
- Hasil produksi tetap wajib QC sebelum READY TO SELL.
- Katalog/WHAT TO MAKE berada di Workflow 03; HOW TO MAKE berasal dari Workflow 02.
- Kandidat tidak otomatis berarti produk sudah jadi atau terbukti laku.

## Katalog Awal

| ID | Produk | Output awal | Engine Flow 02 | Status jalur |
|---|---|---|---|---|
| DP-01 | Budget Planner / Personal Finance Tracker | PDF planner | Adobe Express | READY TO TEST |
| DP-02 | UMKM Bookkeeping / Financial Tracker | Tracker data/formula | Airtable | READY TO TEST |
| DP-03 | Life Planner | PDF planner | Adobe Express | READY TO TEST |
| DP-04 | Wedding Planner | PDF planner + tracker bila diperlukan | Adobe Express; Airtable hanya untuk bagian data/formula | READY TO TEST |
| DP-05 | Small Business Sales / Inventory Tracker | Tracker data/formula | Airtable | READY TO TEST |
| DP-06 | Selling Price / Profit Calculator | Calculator data/formula | Airtable | READY TO TEST |
| DP-07 | To-Do / Productivity Tracker | PDF planner | Adobe Express | READY TO TEST |
| DP-08 | Invoice / Payment Tracker | PDF template; Airtable bila diperlukan untuk tracker | Adobe Express; Airtable sesuai output | READY TO TEST |
| DP-09 | Reusable Video Template / Short Video | Video transformasi sederhana | Cloudinary | READY TO TEST |
| DP-10 | Daily Expense Tracker | Tracker data/formula | Airtable | READY TO TEST |

## Jalur Produksi Resmi

### Design/PDF
**WF-03 → Adobe Express → QC → WF-00 Storage → READY TO SELL**

### Data/Formula/Tracker
**WF-03 → Airtable → readback/QC → WF-00 Storage → READY TO SELL**

### Short Video
**WF-03 → Cloudinary transformation → QC → WF-00 Storage → READY TO SELL**

## Constraint

- Tidak menggunakan engine yang belum PASS sebagai engine resmi.
- AI/generative video belum PASS dan tidak digunakan untuk produksi resmi.
- Spreadsheet otomatis di luar capability yang tercatat belum PASS.
- Katalog ini tidak menyatakan adanya permintaan pasar atau penjualan. Validasi pasar tetap harus dilakukan sebelum memperbanyak produksi.
- Setelah satu produk selesai dan QC PASS, metadata/output/reference harus dikembalikan ke Workflow 03.

## Prioritas Uji Awal

Prioritas teknis ditentukan oleh engine yang sudah PASS, bukan oleh asumsi bahwa semua kandidat harus dibuat sekaligus:

1. **DP-02 — UMKM Bookkeeping / Financial Tracker** → Airtable
2. **DP-05 — Small Business Sales / Inventory Tracker** → Airtable
3. **DP-06 — Selling Price / Profit Calculator** → Airtable
4. **DP-10 — Daily Expense Tracker** → Airtable
5. **DP-01 — Budget Planner** → Adobe Express
6. **DP-03 — Life Planner** → Adobe Express
7. **DP-07 — To-Do / Productivity Tracker** → Adobe Express
8. DP-04 / DP-08 → setelah output spesifik ditetapkan
9. DP-09 → Cloudinary transformation sederhana

**Catatan:** urutan ini adalah urutan uji produksi, bukan klaim ranking pasar.

## Status

**CATALOG CREATED — ENGINE-CONSTRAINED**

Langkah berikutnya: pilih kandidat pertama dari katalog untuk produksi kecil → QC → storage handoff → evaluasi READY TO SELL.
