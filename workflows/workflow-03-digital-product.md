# WORKFLOW 03 — DIGITAL PRODUCT / PRODUCT & MATERIAL REGISTRY

**Version:** 0.3  
**Status:** ACTIVE CHECKPOINT / PROVEN ENGINES REGISTERED  
**Peran:** Registry untuk mencatat **apa yang akan dibuat**, bukan cara membuatnya.
**Relasi:** Workflow 03 (WHAT TO MAKE) → Workflow 02 (HOW TO MAKE) → produksi → QC → storage handoff → kembali ke Workflow 03.

## 1. Prinsip
Workflow 03 menentukan produk, material, kebutuhan capability, dan status produk. Workflow 02 adalah sumber kebenaran untuk HOW TO MAKE.

Logika: KANDIDAT → MATERIAL → CAPABILITY REQUIRED → WORKFLOW 02 → ENGINE/METHOD PASS → PRODUKSI → QC → STATUS.

## 2. Status Produk
- CANDIDATE
- RESEARCHED
- READY TO TEST
- IN PRODUCTION
- QC
- QC PASS
- READY TO SELL
- LISTED
- ACTIVE
- FAILED
- BLOCKED
- ARCHIVED

## 3. Registry Kandidat dan Engine PASS
| ID | Produk | Material | Engine PASS saat ini | Status capability |
|---|---|---|---|---|
| DP-01 | Budget Planner / Personal Finance Tracker | Design/PDF; Spreadsheet bila diperlukan | Adobe Express untuk Design/PDF | Design/PDF PASS; Spreadsheet belum otomatis PASS |
| DP-02 | UMKM Bookkeeping / Financial Tracker | Data/Formula | Airtable | PASS engine |
| DP-03 | Life Planner | Design/PDF; Spreadsheet bila diperlukan | Adobe Express untuk Design/PDF | Design/PDF PASS; Spreadsheet belum otomatis PASS |
| DP-04 | Wedding Planner | Design/PDF; Data/Formula bila diperlukan | Adobe Express + Airtable sesuai output | capability dinilai per output |
| DP-05 | Small Business Sales / Inventory Tracker | Data/Formula | Airtable | PASS engine |
| DP-06 | Selling Price / Profit Calculator | Data/Formula | Airtable | PASS engine |
| DP-07 | To-Do / Productivity Tracker | Design/PDF | Adobe Express | PASS engine |
| DP-08 | Invoice / Payment Tracker | Design/PDF; Data/Formula bila diperlukan | Adobe Express + Airtable sesuai output | capability dinilai per output |
| DP-09 | Reusable Video Template / Short Video | Video transformation | Cloudinary | PASS untuk proven transformation; AI video UNTESTED |
| DP-10 | Daily Expense Tracker | Data/Formula | Airtable | PASS engine |

## 4. Capability Proven
### Adobe Express
PASS: free template search/select, text editing, background color, animation, PDF export/download, dan Adobe Express PDF → Cloudinary → retrieve/verify.

### Airtable
PASS: table/field/record creation, data write, formula creation, calculated-result readback, serta engine tests DP-02, DP-05, DP-06, dan DP-10.

### Cloudinary
PASS: 9:16 resize/crop, trim, chained transformation, text overlay, image overlay, public secure video reference, dan simple short-video recipe.
Batas: bukan full timeline editor; AI/generative video = UNTESTED.

## 5. Aturan Engine Selection
1. Workflow 03 menentukan WHAT TO MAKE.
2. Workflow 02 menentukan capability dan method.
3. Hanya capability PASS yang menjadi engine resmi.
4. Satu produk boleh memakai beberapa engine jika setiap capability/output memiliki jalur PASS.
5. Jika capability belum PASS, status tetap UNTESTED/CANDIDATE atau BLOCKED; jangan dipaksakan.
6. Hasil produksi wajib kembali dicatat pada Workflow 03.
7. Nama aplikasi tidak cukup sebagai dasar routing.

## 6. Alur Gabungan Workflow 03 + Workflow 02
PRODUCT IDEA / MARKET SIGNAL
↓
WORKFLOW 03 — WHAT TO MAKE
↓
CAPABILITY REQUIRED
↓
WORKFLOW 02 — CEK PASS
↓
PRODUCTION RECIPE
↓
PRODUCE
↓
QC / VERIFY
↓
MASTER ASSET / OUTPUT
↓
WORKFLOW 00 — STORAGE HANDOFF
↓
REFERENCE + STATUS KEMBALI KE WORKFLOW 03
↓
READY TO SELL → LISTED → ACTIVE

## 7. Product Test Record
Setiap DP yang benar-benar diuji mencatat: Test ID, Product ID, Capability, Engine/App, Method/Recipe, Input, Output, Output Reference, QC, Result, Notes, Date.

## 8. Batas
Workflow 03 tidak menyimpan aset master, tidak menjadi production engine, tidak mengarang recipe, tidak menganggap kandidat pasar sebagai produk terbukti, dan tidak menyatakan READY TO SELL tanpa QC.

## 9. Checkpoint Terkunci Saat Ini
Produksi yang sudah terbukti sampai tahap video sederhana menggunakan tiga engine yang jelas:
**Adobe Express = Design/PDF**
**Airtable = Data/Formula/Tracker**
**Cloudinary = Media/Video Transformation**

Checkpoint ini menjadi dasar sebelum menambah kandidat produk baru. Produk berikutnya harus masuk dari kebutuhan/market signal, lalu dipetakan ke capability PASS sebelum produksi.