# WORKFLOW 04 — PRODUCT MARKETING / EXPLAINER VIDEO

**Version:** 0.1
**Status:** ACTIVE CHECKPOINT / TECHNICAL TEST PASSED / REAL PRODUCT TEST PENDING
**Peran:** Menjelaskan produk yang sudah jadi kepada calon pengguna/pembeli melalui materi marketing, terutama explainer video.
**Relasi:** Workflow 03 (WHAT TO MAKE) → produk selesai/QC PASS → Workflow 04 (EXPLAIN & MARKET) → Cloudinary → Workflow 01 Publisher.

## 1. Tujuan

Workflow 04 menjawab pertanyaan calon pengguna:

> **“Apakah produk ini berguna untuk saya, dan bagaimana saya menggunakannya?”**

Workflow 04 bukan production engine. Workflow 04 tidak menjelaskan cara membuat produk.

## 2. Batas / Rahasia Dapur

Workflow 04 **dilarang membocorkan**:
- Workflow 02 atau recipe produksi.
- Prompt produksi internal.
- App/tool yang dipakai untuk membuat produk.
- Prosedur automation internal.
- Struktur internal MR.ONE yang tidak relevan bagi calon pembeli.
- Rahasia metode produksi.

Materi marketing harus berfokus pada **produk jadi dan pengalaman pengguna**, bukan proses pembuatannya.

## 3. Input

Minimal:
- Product ID.
- Nama produk.
- Deskripsi/fungsi produk.
- Masalah pengguna yang diselesaikan.
- Target pengguna.
- Cara penggunaan.
- Manfaat utama.
- CTA.
- Visual produk jadi bila tersedia.
- Asset/reference produk yang sudah QC PASS.

Metadata utama berasal dari Workflow 03 dan hasil produk aktual. Workflow 04 tidak mengarang fakta produk.

## 4. Output

Workflow 04 dapat menghasilkan:
- Script/explainer structure.
- Scene order.
- Visual direction.
- On-screen text.
- CTA.
- Caption/title/description untuk publishing.
- Marketing video final.
- Marketing Asset ID, misalnya `DP-02-MKT-001`.
- Cloudinary asset reference/URL setelah QC.

**Product ID tetap menjadi penghubung utama dengan produk.**

## 5. Dua Jalur Marketing

### A. AUTO — Explainer Generator

Produk jadi + informasi produk + visual yang tersedia
→ Explain Video Generator
→ explainer video
→ QC
→ Cloudinary
→ Workflow 01 Publisher.

**Status teknis:** TEST BERHASIL.

Pengujian Scrimba Explain/Explain Video Generator berhasil menghasilkan explainer dengan:
- struktur video,
- visual,
- narasi Bahasa Indonesia,
- beberapa blok narration,
- link hasil video.

**Batas bukti saat ini:** pengujian teknis menggunakan materi contoh. Konten yang benar-benar berasal dari produk final dan visual produk final belum diuji.

### B. SEMI-MANUAL — Marketing Preparation

Produk jadi
→ MR.ONE menyiapkan:
  - script,
  - urutan scene,
  - visual direction,
  - on-screen text,
  - CTA,
  - metadata,
  - Product ID
→ user membuat/edit video di tool eksternal yang sesuai
→ video final dikembalikan
→ QC
→ Cloudinary
→ Workflow 01 Publisher.

Tool eksternal seperti CapCut, Adobe Express, atau Google Flow hanya menjadi pilihan semi-manual bila diperlukan. Tidak ada yang ditetapkan sebagai core engine sebelum diuji.

## 6. Visual Produk

Prioritas visual:
1. Visual produk digital yang benar-benar sudah selesai.
2. Screenshot/preview halaman produk.
3. Visual pendukung yang relevan bila visual produk belum cukup.

Marketing tidak boleh menggunakan visual yang membuat calon pembeli salah memahami isi produk.

## 7. Asset dan Storage

- **Product Master** = aset produk yang siap dijual; bukan marketing video biasa.
- **Marketing Asset** = video/gambar/copy promosi yang menjelaskan atau mempromosikan produk.
- Marketing video disimpan di Cloudinary setelah QC.
- Marketing Asset ID harus dapat dikaitkan kembali ke Product ID.

Pola:
**PRODUCT MASTER → MARKETING ASSET → QC → CLOUDINARY → PUBLIC MEDIA URL → WORKFLOW 01**

## 8. QC Marketing

Sebelum handoff ke Publisher, periksa:
- Produk yang ditampilkan benar.
- Visual sesuai produk aktual.
- Klaim sesuai fungsi/manfaat yang benar-benar ada.
- Tidak membocorkan rahasia produksi.
- Format video sesuai kebutuhan channel.
- CTA jelas.
- Product ID/Marketing Asset ID benar.
- Asset final dapat diakses dari Cloudinary.
- Public media URL valid bila akan dipakai Publisher.

Jika gagal:
**FAILED / BLOCKED**, bukan READY.

## 9. Hubungan dengan Metricool

Workflow 04 **tidak menggantikan Workflow 01**.

Setelah marketing asset siap:
**Cloudinary → Workflow 01 Publisher → Metricool / jalur publisher lain yang sudah PASS.**

Metricool tetap dipertahankan sebagai publisher yang sudah terbukti. Batas kuota Metricool tidak mengubah fungsi Workflow 04.

Jika publisher belum tersedia karena kuota/limit:
**Marketing Asset tetap dapat selesai dan masuk antrian READY TO PUBLISH.**
Jangan menganggap produksi produk harus berhenti hanya karena publisher sedang menunggu kuota.

## 10. Status

Status yang relevan:
- MARKETING INPUT READY
- SCRIPT READY
- VIDEO IN PRODUCTION
- QC
- QC PASS
- READY TO PUBLISH
- SCHEDULED/PENDING
- PUBLISHED
- FAILED
- BLOCKED

**READY TO PUBLISH ≠ PUBLISHED.**

Workflow 01 tetap menjadi sumber kebenaran untuk status publikasi.

## 11. Prinsip Anti-Overbuild

Jangan membangun:
- editor video baru,
- production engine baru,
- automation besar,
- publisher baru,
- database marketing baru,

sebelum kebutuhan dan kemampuan tersebut terbukti diperlukan.

Urutan:
**TEST KECIL → VERIFIKASI → PASS → FORMALKAN → PERLUAS.**

## 12. Checkpoint Saat Ini

**TERBUKTI:**
- Konsep Flow 04 sebagai product explainer/marketing.
- Explain Video Generator dapat menghasilkan explainer berbahasa Indonesia.
- Marketing asset dapat diarahkan ke Cloudinary.
- Publisher tetap berada di Workflow 01.

**BELUM TERBUKTI:**
- Explainer dari produk digital final nyata.
- Penggunaan visual produk final sebagai input explainer.
- End-to-end final: produk READY TO SELL → Flow 04 → Cloudinary → Metricool → PUBLISHED.

**Langkah berikutnya:**
Buat **1 produk digital nyata sampai READY TO SELL**, kemudian gunakan produk tersebut sebagai pengujian pertama Flow 04 secara nyata.

## 13. Kalimat Pengingat Inti

> **Workflow 04 menjual dengan menjelaskan produk, bukan menjelaskan cara membuat produk.**

> **Cara membuat produk = rahasia dapur Workflow 02.**

> **Flow 04 hanya menunjukkan masalah, kegunaan, cara penggunaan, manfaat, visual produk, dan CTA kepada calon pengguna.**

> **Produk dibuat dulu sampai benar-benar jadi; setelah itu baru marketing dibuat berdasarkan produk yang nyata.**
