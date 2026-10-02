# WORKFLOW 03 — DIGITAL PRODUCT / PRODUCT & MATERIAL REGISTRY

**Version:** 0.2  
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

| ID | Produk | Material Type | Subtype | Status Awal | Capability yang dibutuhkan | Engine PASS saat ini | Hasil |
|---|---|---|---|---|---|---|---|
| DP-01 | Budget Planner / Personal Finance Tracker | TEMPLATE | Spreadsheet / PDF | READY TO TEST | Design/PDF; Spreadsheet bila versi spreadsheet | Adobe Express — Design/PDF | 🟢 Design/PDF PASS; Spreadsheet UNTESTED |
| DP-02 | UMKM Bookkeeping / Financial Tracker | TEMPLATE | Spreadsheet | READY TO TEST | Spreadsheet generation + formula | — | 🟡 UNTESTED |
| DP-03 | Life Planner | TEMPLATE | PDF / Spreadsheet | READY TO TEST | Design/PDF; Spreadsheet bila versi spreadsheet | Adobe Express — Design/PDF | 🟢 Design/PDF PASS; Spreadsheet UNTESTED |
| DP-04 | Wedding Planner | TEMPLATE | PDF / Spreadsheet | READY TO TEST | Design/PDF; Spreadsheet bila versi spreadsheet | Adobe Express — Design/PDF | 🟢 Design/PDF PASS; Spreadsheet UNTESTED |
| DP-05 | Small Business Sales / Inventory Tracker | TEMPLATE | Spreadsheet | READY TO TEST | Spreadsheet + formula/data logic | — | 🟡 UNTESTED |
| DP-06 | Selling Price / Profit Calculator | TEMPLATE | Spreadsheet | READY TO TEST | Spreadsheet + formula/data logic | — | 🟡 UNTESTED |
| DP-07 | To-Do / Productivity Tracker | TEMPLATE | Spreadsheet / PDF | READY TO TEST | Design/PDF; Spreadsheet bila versi spreadsheet | Adobe Express — Design/PDF | 🟢 Design/PDF PASS; Spreadsheet UNTESTED |
| DP-08 | Invoice / Payment Tracker | TEMPLATE | Spreadsheet / PDF | READY TO TEST | Design/PDF; Spreadsheet bila versi spreadsheet | Adobe Express — Design/PDF | 🟢 Design/PDF PASS; Spreadsheet UNTESTED |
| DP-09 | Reusable Video Template | TEMPLATE | VIDEO | READY TO TEST | Reusable-template capability | — | 🟡 UNTESTED |

### 3.1 Capability Adobe Express yang sudah terbukti

Adobe Express saat ini **bukan engine untuk semua DP**. Yang sudah terbukti melalui pengujian nyata:

- Search free template → **PASS**
- Fill text pada template → **PASS** pada pengujian yang berhasil
- Change background color → **PASS**
- Animate design → **PASS**
- Export/download PDF → **PASS**
- Adobe Express PDF → Cloudinary → retrieve/verify → **PASS E2E**
- Published Link public preview/promosi tanpa login → **PASS E2E**
- Published Link sebagai customer-download file → **TIDAK terbukti / bukan jalur delivery**
- Replace Image → **UNTESTED**; tool sementara unavailable saat pengujian
- PNG/JPG export melalui connector → **UNTESTED**; connector mengarahkan ke converter web, bukan menghasilkan file melalui connector
- Reusable Video Template → **UNTESTED**

Karena itu, untuk produk yang hanya membutuhkan **design/PDF**, Adobe Express dapat menjadi engine PASS. Untuk kebutuhan **Spreadsheet + Formula**, **Reusable Video Template**, atau capability lain yang belum PASS, Workflow 03 **tidak boleh mengarahkan produksi ke Adobe Express hanya karena aplikasinya tersedia**.

### 3.2 Pemetaan capability → engine

Pemetaan dilakukan berdasarkan **capability**, bukan nama aplikasi.

Contoh:
- `Design/PDF` → Adobe Express (**PASS**)
- `Spreadsheet + Formula` → belum ada engine PASS → **cari dan uji engine**
- `Reusable Video Template` → belum ada engine PASS → **cari dan uji engine**
- `PNG/JPG melalui connector` → belum ada engine PASS → **cari/uji bila capability diperlukan**

Jika sebuah DP memiliki beberapa material/output, setiap capability dinilai terpisah. Satu DP boleh menggunakan lebih dari satu engine jika seluruh capability yang dibutuhkan memiliki jalur PASS.

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
5. Jika tidak ada capability PASS, DP menjadi **BLOCKED/UNTESTED** untuk capability tersebut dan tidak dipaksakan produksinya.
6. Setelah uji nyata, hasil produksi dan capability reference ditulis kembali ke registry DP.
7. **Jangan mengarahkan DP ke engine hanya berdasarkan nama aplikasi.** Routing harus berdasarkan capability yang dibutuhkan dan status PASS-nya.

## 5. Urutan Uji

Urutan kerja untuk setiap kandidat:

`DP → CAPABILITY REQUIRED → WORKFLOW 02 TEST → ENGINE/METHOD → SAMPLE OUTPUT → QC → PASS/FAIL/BLOCKED → UPDATE DP`

Contoh:

`DP-06 Selling Price / Profit Calculator`
→ membutuhkan Spreadsheet + Formula  
→ cek Workflow 02  
→ belum ada capability PASS  
→ **jangan arahkan ke Adobe Express**  
→ cari engine Spreadsheet + Formula  
→ uji sample  
→ QC  
→ hanya jika PASS, catat engine + recipe + hasil  
→ kemudian DP-06 memiliki jalur produksi resmi.

## 6. Batas Workflow

Workflow 03 **tidak**:
- menyimpan aset master;
- menjadi production engine;
- mengarang recipe;
- menganggap nama aplikasi sebagai capability;
- menyatakan produk siap jual tanpa QC;
- menganggap kandidat pasar sebagai produk terbukti.

Workflow 02 tetap menjadi sumber kebenaran untuk **HOW TO MAKE** dan capability engine.

Workflow 03 menjadi sumber kebenaran untuk **WHAT TO MAKE / STATUS PRODUK / KEBUTUHAN CAPABILITY**.

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

**Checkpoint saat ini:** capability yang sudah terbukti untuk pemetaan produk adalah **Adobe Express → Design/PDF**. Capability yang belum memiliki engine PASS tetap menjadi target pencarian dan pengujian berikutnya.
