# MR.ONE STARTUP GATE — WAJIB

**Fungsi:** pintu teknis/prosedural pembukaan sesi MR.ONE.  
**Status:** ACTIVE — STARTUP READ GATE  
**Versi:** 1.0

## Tujuan

Setiap GPT/model yang masuk untuk bekerja di MR.ONE wajib melewati gate ini sebelum melakukan pekerjaan teknis.

Gate ini menyatukan urutan pembacaan agar tidak bergantung pada ingatan percakapan.

## Urutan WAJIB

1. Baca **MASTER WORKSPACE** terbaru bila tersedia.
2. Baca **PROSEDUR-UMUM.md**.
3. Baca **CHECKPOINT-HARIAN.md**.
4. Baca seluruh:
   - `workflows/workflow-01-publisher.md`
   - `workflows/workflow-02-production-engine.md`
   - `workflows/workflow-03-digital-product.md`
   - `workflows/workflow-04-marketing-explainer.md`
5. Pahami hubungan antar-workflow.
6. Baru identifikasi pekerjaan aktif dan masuk ke workflow lokal yang relevan.
7. Untuk perubahan teknis yang membutuhkan persetujuan owner, tunggu **LANJUTKAN**.

## Aturan model

Gate berlaku untuk **semua GPT/model yang masuk atau digunakan untuk pekerjaan MR.ONE**, termasuk model utama, model fallback/pengganti, dan model lain yang mengambil alih sesi.

Tidak boleh ada silent bypass.

## Kondisi BLOCKED

Jika gate tidak dapat dibaca, file wajib hilang, atau prosedur/checkpoint yang diperlukan tidak dapat diverifikasi:

**STARTUP GATE = BLOCKED**

Model tidak boleh melanjutkan pekerjaan teknis yang bergantung pada prosedur MR.ONE sampai sumber yang diperlukan tersedia.

## Batas teknis

GitHub Actions dapat memvalidasi bahwa gate dan seluruh file wajib tersedia serta konsisten di repository.

GitHub Actions **tidak dapat secara native memaksa aplikasi ChatGPT menjalankan pembacaan file tepat pada detik sesi baru dibuka**.

Karena itu mekanisme ini terdiri dari dua lapis:

**REPOSITORY VALIDATION → memastikan pintu startup utuh**  
**GPT STARTUP RULE → mewajibkan GPT membaca pintu sebelum bekerja**

## PASS

Startup dianggap siap bila:
- semua file wajib ada;
- gate dapat dibaca;
- prosedur global dapat dibaca;
- checkpoint dapat dibaca;
- Workflow 01–04 dapat dibaca;
- GitHub Action validasi berhasil.

**PASS repository gate tidak berarti percakapan otomatis dibaca.** Pembacaan oleh GPT tetap diwajibkan oleh prosedur startup.
