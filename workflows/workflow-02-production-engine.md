# MR.ONE Workflow 02 — Production Engine

**Status:** DRAFT / UNTESTED  
**Versi:** 0.1  
**Fungsi:** Ruang kerja untuk produksi, pengolahan, dan pengujian materi MR.ONE sebelum materi dinyatakan siap diteruskan ke workflow berikutnya.

## 1. Prinsip Utama

Workflow 02 adalah **ruang produksi**, bukan tempat menetapkan app/tool hanya berdasarkan asumsi.

Pola kerja dasar:

**PERMINTAAN PRODUKSI → IDENTIFIKASI MATERI → UJI TUNTAS KOMPONEN → PRODUKSI/REVISI → QC → HASIL NYATA → STATUS**

Tidak ada app, connector, metode produksi, atau jenis materi baru yang menjadi metode resmi hanya karena terlihat cocok.

## 2. Aturan Uji Tuntas

Setiap **app/platform/connector/fungsi baru** yang akan dipakai dalam Production Engine wajib melalui uji tuntas sebelum dijadikan komponen resmi.

Minimal diperiksa:

- fungsi sebenarnya;
- akses/koneksi yang tersedia;
- fungsi connector yang benar-benar tersedia;
- input yang diterima;
- output yang dihasilkan;
- batas penggunaan;
- biaya/free limit bila relevan;
- kebutuhan akun/API key;
- kemampuan upload/download/retrieve bila relevan;
- kemampuan automation/API bila relevan;
- watermark atau batas hasil bila relevan;
- lisensi/commercial use bila relevan;
- ketergantungan terhadap app lain;
- risiko kegagalan atau lock-in;
- bukti penggunaan nyata.

**Informasi promosi atau klaim situs bukan bukti kemampuan operasional MR.ONE.**

## 3. Uji Tuntas Materi Baru

Setiap **jenis materi baru** yang akan diproduksi juga harus diuji sebelum dijadikan pola produksi resmi.

Periksa minimal:

- tujuan materi;
- input yang diperlukan;
- format output;
- kualitas minimum;
- ukuran/dimensi/durasi bila relevan;
- apakah dapat disimpan di storage yang ditetapkan;
- apakah dapat diteruskan ke workflow berikutnya;
- apakah dapat dipakai pada platform tujuan;
- apakah ada watermark atau batas lisensi;
- apakah hasil dapat diverifikasi;
- apakah proses dapat diulang secara konsisten.

Jenis materi tidak boleh dianggap cocok hanya karena secara teori dapat dibuat.

## 4. Tahapan Uji

### Tahap A — Identifikasi

Tentukan:

- apa yang ingin diproduksi;
- untuk tujuan apa;
- input apa yang tersedia;
- output apa yang dibutuhkan;
- dependency yang mungkin diperlukan.

### Tahap B — Audit Kandidat

Petakan kandidat app/tool/connector/metode.

**Belum memilih pemenang.**

Status awal setiap kandidat:

- CANDIDATE
- UNTESTED

### Tahap C — Uji Nyata

Lakukan pengujian dengan input kecil dan terkontrol terlebih dahulu.

Bukti harus berasal dari hasil nyata, bukan hanya dokumentasi atau klaim.

### Tahap D — Verifikasi

Periksa:

- output benar;
- format benar;
- kualitas memenuhi kebutuhan;
- asset/reference dapat digunakan;
- hasil dapat dibaca/retrieve kembali;
- dependency bekerja;
- tidak ada kegagalan tersembunyi.

### Tahap E — Penetapan Status

Gunakan status:

- **PASS** — terbukti bekerja sesuai kebutuhan.
- **FAIL** — sudah diuji dan tidak memenuhi kebutuhan.
- **BLOCKED** — pengujian tidak dapat dilanjutkan karena akses, koneksi, izin, limit, atau dependency.
- **UNTESTED** — belum diuji.
- **CANDIDATE** — kandidat yang belum ditetapkan sebagai metode resmi.

Hanya **PASS** yang boleh dimasukkan sebagai metode resmi Production Engine.

## 5. Aturan Proof Before Build

Production Engine tidak boleh membangun pipeline besar sebelum satu metode kecil terbukti.

Urutan:

**AUDIT → TEST KECIL → VERIFIKASI → PASS → BARU FORMALKAN → BARU PERLUAS**

Jika pengujian gagal, jangan menyembunyikan kegagalan dengan mengganti definisi hasil.

## 6. Pemisahan App dan Fungsi

Nama app bukan bukti bahwa fungsinya tersedia.

Untuk setiap app yang diuji, catat secara terpisah:

| Komponen | Yang harus dibuktikan |
|---|---|
| App/platform | App benar-benar dapat diakses |
| Connector | Connector benar-benar tersedia |
| Fungsi | Read/Write/Create/Upload/Retrieve/Generate/dll. |
| Input | Input yang diterima |
| Output | Output yang dihasilkan |
| Limit | Batas nyata yang ditemukan |
| Dependency | Ketergantungan |
| Hasil uji | Bukti nyata |
| Status | PASS/FAIL/BLOCKED/UNTESTED |

Satu app dapat memiliki satu fungsi yang PASS dan fungsi lain yang UNTESTED atau FAIL. Status tidak boleh digeneralisasi ke seluruh app.

## 7. Jalur Materi

Production Engine menghasilkan **materi siap untuk tahap berikutnya**, tetapi tidak mengasumsikan workflow tujuan secara permanen.

Pola umum:

**INPUT → PRODUCTION ENGINE → MATERI HASIL → QC → ASSET/REFERENCE → HANDOFF**

Identitas workflow tujuan ditentukan saat handoff diperlukan. Production Engine tidak perlu menghafal seluruh workflow downstream.

## 8. QC Minimum

Sebelum materi dinyatakan siap:

1. file/hasil benar-benar ada;
2. output dapat dibuka atau diakses;
3. format sesuai kebutuhan;
4. isi sesuai permintaan;
5. asset/reference tercatat;
6. tidak ada error yang diketahui;
7. status pengujian jelas.

Jika salah satu bukti penting belum ada, jangan menyatakan **PASS**.

## 9. Penyimpanan dan Handoff

Production Engine bukan storage utama.

Jika hasil berupa media/content, gunakan storage yang memang telah terbukti dan ditetapkan oleh Workflow 00.

Jika hasil berupa file/document, gunakan jalur file yang telah terbukti.

Production Engine hanya menghasilkan dan menyerahkan reference/asset yang telah diverifikasi.

## 10. Fallback

Jika metode utama:

- tidak tersedia → cari kandidat lain yang sudah diaudit;
- gagal → tandai FAIL dan uji kandidat lain;
- terblokir → tandai BLOCKED;
- belum terbukti → tetap UNTESTED.

Jangan mengganti metode secara diam-diam.

## 11. Catatan Pengujian

Setiap pengujian resmi minimal mencatat:

- tanggal;
- tujuan pengujian;
- app/platform;
- connector/fungsi;
- input;
- metode;
- output;
- bukti/reference;
- hasil;
- masalah;
- status PASS/FAIL/BLOCKED/UNTESTED.

## 12. Batas Workflow 02

Workflow 02 **tidak**:

- menjadi Publisher;
- menjadi storage utama;
- menganggap semua app yang tersedia otomatis boleh digunakan;
- menganggap semua jenis materi otomatis siap diproduksi;
- mengunci nama tool atau platform sebelum diuji;
- mengklaim hasil berhasil tanpa bukti.

## 13. Status Dokumen

**DRAFT / UNTESTED.**

Dokumen ini baru menetapkan kerangka kerja Production Engine dan metode uji tuntas.  
App, connector, jenis materi, dan jalur produksi resmi harus ditambahkan **satu per satu setelah pengujian nyata**.
