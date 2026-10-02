# MR.ONE Workflow 02 — Production Engine

**Status:** ACTIVE CHECKPOINT / PROVEN CAPABILITIES REGISTERED  
**Versi:** 0.5  
**Fungsi:** Ruang produksi dan pengujian materi MR.ONE, sekaligus pusat memori prosedural untuk kemampuan produksi yang sudah terbukti.

## 1. Peran Workflow 02
Workflow 02 adalah **HOW TO MAKE**.
- Workflow 00 = storage;
- Workflow 01 = publishing;
- Workflow 02 = produksi, capability registry, recipe/method, operasi file/media, provenance, QC produksi, metadata contract, dan handoff.

Alur: **PRODUK/MATERIAL DARI WORKFLOW 03 → CEK CAPABILITY → PILIH METHOD PASS → PRODUKSI → QC → STORAGE HANDOFF → HASIL/REFERENCE → KEMBALI KE WORKFLOW 03**

## 2. Prinsip Wajib
1. Proof Before Build.
2. App ≠ Capability.
3. Status PASS berlaku per operasi/fungsi yang benar-benar diuji.
4. AUDIT → TEST KECIL → VERIFIKASI → PASS → FORMALKAN → PERLUAS.
5. Jika capability belum terbukti: UNTESTED/CANDIDATE; jangan dipaksakan.
6. Jika gagal: FAIL. Jika akses/izin/limit menghalangi: BLOCKED.
7. Tidak membangun pipeline besar sebelum metode kecil terbukti.
8. Tidak mengganti tool/method secara diam-diam.
9. Hasil produksi belum otomatis READY TO SELL; tetap wajib QC dan status Workflow 03.
10. Jika capability PASS yang ada sudah cukup, jangan mencari app baru tanpa kebutuhan nyata.

## 3. Capability Registry — PASS Resmi Saat Ini

### 3.1 Adobe Express — Design/PDF
Terbukti: search/select free template, fill/edit text, change background color, animate design, export/download PDF, dan Adobe Express PDF → Cloudinary → retrieve/verify = PASS E2E.
Peran: engine produksi desain/dokumen/PDF yang sesuai.
Catatan: editor/preview reference ≠ direct-download customer delivery; tidak semua format/export Adobe otomatis PASS.

### 3.2 Airtable — Data / Formula / Tracker
Terbukti: membuat table/field/record, menulis data, membuat formula, membaca hasil perhitungan, serta engine DP-02, DP-05, DP-06, dan DP-10 = PASS.
Contoh uji: DP-02 net balance 65000; DP-05 current stock 23 dan stock value 230000; DP-06 net profit 50000 dan margin 50%; DP-10 remaining 65000.
Catatan: attachment storage/read = PASS; temporary attachment URL retrieval = PASS; Airtable → GPT → Cloudinary direct automated handoff = BLOCKED pada uji safety check.

### 3.3 Cloudinary — Video / Media Transformation
Cloudinary telah diuji sebagai **media engine**, bukan full timeline editor.
Terbukti: video 9:16/resize-crop, trim/duration, chained transformation, text overlay, image overlay, dan public secure video URL/reference = PASS.
Contoh final MR.ONE: 0–3 detik MR.ONE | VIDEO TEST; 3–7 detik VIDEO PENDEK | CONTOH MR.ONE; 7–10 detik CEK LINK DI DESKRIPSI; output MP4 1080×1920 = PASS.
Batas: bukan editor timeline kreatif penuh. Multi-clip storytelling kompleks, musik/SFX/voice-over, dan AI text-to-video belum PASS. Splice/transition syntax belum dianggap sebagai bukti penuh multi-asset composition. AI/generative video = UNTESTED.

## 4. Production Recipe Registry
1. Design/PDF recipe → Adobe Express → export PDF → QC → handoff.
2. Data/Formula recipe → Airtable → table/fields/formula/records → readback calculation → QC.
3. Short Video recipe → Cloudinary → 9:16/trim/overlay/transformation → MP4 → QC → public reference.
Recipe kreatif yang belum diuji tetap UNTESTED.

## 5. QC Minimum
1. hasil benar-benar ada; 2. dapat dibuka/diakses; 3. format benar; 4. isi sesuai; 5. kualitas minimum; 6. metadata/reference tersedia; 7. handoff dapat dilakukan atau status jelas; 8. tidak ada error diketahui; 9. status PASS/FAIL/BLOCKED/UNTESTED jelas.

## 6. Provenance
INPUT/SOURCE → METHOD → APP/CONNECTOR/FUNCTION → OPERATION → OUTPUT → QC → STORAGE REFERENCE → HANDOFF.

## 7. Metadata Contract
Minimal: Job/Production ID, material type, purpose, input/source reference, method/recipe, app/platform, connector/function, operation, output format, dimensions/duration bila relevan, QC status, asset/reference, storage status, handoff status, notes/issues.

## 8. Jalur Produksi Gabungan dengan Workflow 03
WORKFLOW 03 — WHAT TO MAKE → CEK CAPABILITY WORKFLOW 02 → PILIH RECIPE PASS → PRODUKSI → QC/VERIFY → MASTER ASSET/OUTPUT → STORAGE HANDOFF WORKFLOW 00 → HASIL + REFERENCE KEMBALI KE WORKFLOW 03 → READY TO SELL/LISTING setelah syarat Workflow 03 terpenuhi.

## 9. Fallback
Unavailable → candidate teraudit; gagal → FAIL; blocked → BLOCKED; belum diuji → UNTESTED. Tidak ada silent substitution.

## 10. Batas
Workflow 02 tidak menjadi Publisher, storage utama, pengunci app tanpa uji, atau penentu bahwa engine PASS berarti produk siap jual.

## 11. Status Dokumen
**ACTIVE CHECKPOINT / PROVEN CAPABILITIES REGISTERED.** Checkpoint ini mencatat hasil nyata yang sudah terbukti sampai tahap video sederhana: Adobe Express + Airtable + Cloudinary. Capability baru mengikuti lifecycle uji yang sama.