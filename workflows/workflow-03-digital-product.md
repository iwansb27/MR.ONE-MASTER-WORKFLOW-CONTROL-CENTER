# WORKFLOW 03 — DIGITAL PRODUCT / PRODUCT & MATERIAL REGISTRY

**Version:** 0.1  
**Status:** DRAFT / UNTESTED  
**Peran:** Registry untuk mencatat *apa yang akan dibuat/dibuat*, bukan cara membuatnya.  
**Relasi utama:** Workflow 03 (WHAT TO MAKE) → Workflow 02 (HOW TO MAKE) → hasil produksi → kembali ke Workflow 03 untuk status/QC/storage/marketplace.

## 1. Prinsip

Workflow 03 adalah daftar kendali produk/material digital MR.ONE. Setiap kandidat mendapat ID permanen sementara, metadata, status, dan jalur uji.

Workflow 03 **tidak mengarang kemampuan engine**. Pemilihan engine dilakukan berdasarkan capability yang sudah PASS di Workflow 02.

Logika:
`KANDIDAT → TENTUKAN MATERIAL → CARI CAPABILITY WORKFLOW 02 → PILIH ENGINE/METHOD YANG TERBUKTI → UJI → QC → CATAT HASIL`

Jika capability belum terbukti:
- jangan menyatakan engine cocok;
- status engine = CANDIDATE / UNTESTED;
- uji capability di Workflow 02 terlebih dahulu.

## 2. Status Produk

- CANDIDATE — kandidat masuk registry
- RESEARCHED — sudah memiliki bukti/sinyal pasar
- READY TO TEST — siap diuji produksinya
- IN PRODUCTION — sedang dibuat
- QC — menunggu pemeriksaan
- QC PASS — lolos pemeriksaan
- READY TO SELL — siap masuk marketplace
- LISTED — sudah terdaftar
- ACTIVE — sedang dijual
- FAILED — gagal produksi/QC
- BLOCKED — tertahan dependency/capability
- ARCHIVED — tidak dilanjutkan

## 3. Registry Kandidat Awal

| ID | Produk | Material Type | Subtype | Status Awal | Capability/Engine yang perlu diuji | Hasil |
|---|---|---|---|---|---|---|
| DP-01 | Budget Planner / Personal Finance Tracker | TEMPLATE | Spreadsheet / PDF | READY TO TEST | Spreadsheet/PDF generation | UNTESTED |
| DP-02 | UMKM Bookkeeping / Financial Tracker | TEMPLATE | Spreadsheet | READY TO TEST | Spreadsheet generation + formula | UNTESTED |
| DP-03 | Life Planner | TEMPLATE | PDF / Spreadsheet | READY TO TEST | PDF/Spreadsheet generation | UNTESTED |
| DP-04 | Wedding Planner | TEMPLATE | PDF / Spreadsheet | READY TO TEST | PDF/Spreadsheet generation | UNTESTED |
| DP-05 | Small Business Sales / Inventory Tracker | TEMPLATE | Spreadsheet | READY TO TEST | Spreadsheet + formula/data logic | UNTESTED |
| DP-06 | Selling Price / Profit Calculator | TEMPLATE | Spreadsheet | READY TO TEST | Spreadsheet + formula/data logic | UNTESTED |
| DP-07 | To-Do / Productivity Tracker | TEMPLATE | Spreadsheet / PDF | READY TO TEST | Spreadsheet/PDF generation | UNTESTED |
| DP-08 | Invoice / Payment Tracker | TEMPLATE | Spreadsheet / PDF | READY TO TEST | Spreadsheet/PDF generation | UNTESTED |
| DP-09 | Reusable Video Template | TEMPLATE | VIDEO | READY TO TEST | Reusable-template capability | UNTESTED |

**Catatan:** daftar ini adalah *candidate registry*, bukan klaim bahwa seluruh produk sudah terbukti laku atau sudah dipilih untuk dijual.

## 4. Kolom Engine Selection

Setiap DP harus mempunyai pemetaan berikut sebelum produksi:

- **Product ID**
- **Material Type**
- **Subtype**
- **Production Capability ID** dari Workflow 02
- **Engine / App**
- **Connector / Function**
- **Production Method / Recipe ID**
- **Input**
- **Expected Output**
- **Format**
- **QC Requirement**
- **Storage Target**
- **Marketplace Target**
- **Capability Status**
- **Production Status**
- **QC Status**
- **Evidence / Test Reference**

### Aturan pemilihan engine

1. Workflow 03 menentukan **produk apa**.
2. Workflow 02 menentukan **kemampuan apa yang tersedia**.
3. Hanya capability **PASS** yang boleh menjadi engine resmi.
4. Jika lebih dari satu engine PASS, pilihan dicatat sebagai **Engine A / Engine B**, bukan diputuskan secara otomatis.
5. Jika tidak ada capability PASS, DP menjadi **BLOCKED/UNTESTED** dan tidak dipaksakan produksinya.
6. Setelah uji nyata, hasil produksi dan capability reference ditulis kembali ke registry DP.

## 5. Urutan Uji

Urutan kerja untuk setiap kandidat:

`DP → CAPABILITY REQUIRED → WORKFLOW 02 TEST → ENGINE/METHOD → SAMPLE OUTPUT → QC → PASS/FAIL/BLOCKED → UPDATE DP`

Contoh:

`DP-01 Budget Planner`
→ membutuhkan spreadsheet generation  
→ cari capability spreadsheet di Workflow 02  
→ jika ada capability PASS, gunakan engine tersebut  
→ buat sample  
→ QC  
→ catat engine + recipe + hasil  
→ lanjut ke kandidat berikutnya.

## 6. Batas Workflow

Workflow 03 **tidak**:
- menyimpan aset master;
- menjadi production engine;
- mengarang recipe;
- menganggap nama aplikasi sebagai capability;
- menyatakan produk siap jual tanpa QC;
- menganggap kandidat pasar sebagai produk terbukti.

Workflow 02 tetap menjadi sumber kebenaran untuk **HOW TO MAKE** dan capability engine.

Workflow 03 menjadi sumber kebenaran untuk **WHAT TO MAKE / STATUS PRODUK**.

## 7. Test Record

Setiap DP yang benar-benar diuji harus mendapatkan record:

- Test ID
- Product ID
- Capability ID
- Engine/App
- Method/Recipe
- Input
- Output
- Output Reference
- QC
- Result: PASS / FAIL / BLOCKED
- Notes
- Date

**Status dokumen:** DRAFT / UNTESTED sampai registry ini dipakai dalam uji capability nyata.
