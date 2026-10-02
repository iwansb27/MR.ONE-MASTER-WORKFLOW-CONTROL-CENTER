# MR.ONE Workflow 02 — Production Engine

**Status:** DRAFT / UNTESTED  
**Versi:** 0.4  
**Fungsi:** Ruang produksi dan pengujian materi MR.ONE, sekaligus pusat memori prosedural untuk kemampuan produksi yang sudah terbukti.

## 1. Prinsip Utama

Workflow 02 adalah **ruang produksi**, bukan sekadar daftar app/tool.

Ia memahami hubungan antar-komponen yang diperlukan untuk menghasilkan materi, tetapi tetap menjaga batas:
- Workflow 00 = storage;
- Workflow 01 = publishing;
- Workflow 02 = produksi, operasi file/media, QC produksi, provenance, dan handoff.

Pola kerja:

**PERMINTAAN → IDENTIFIKASI MATERI → PETAKAN KEBUTUHAN → UJI TUNTAS KOMPONEN → PRODUKSI → OPERASI FILE/MEDIA → QC → STORAGE HANDOFF → HASIL/REFERENCE**

Tidak ada app, connector, fungsi, metode produksi, atau jenis materi baru yang menjadi metode resmi hanya karena terlihat cocok.

## 2. Arsitektur Memori Production Engine

Production Engine menyimpan **pengetahuan prosedural dan registry kemampuan**, bukan menyalin fungsi workflow lain.

### 2.1 Lima objek utama

| Objek | Fungsi |
|---|---|
| APP / PLATFORM | Tempat kemampuan produksi berada |
| CONNECTOR | Jalur akses MR.ONE ke app/platform |
| FUNCTION | Operasi nyata yang terbukti, mis. generate/read/write/upload/retrieve |
| PRODUCTION METHOD / RECIPE | Urutan fungsi yang terbukti untuk menghasilkan materi tertentu |
| MATERIAL TYPE | Kelas hasil, mis. image, video, document, template, audio |

Hubungan:

**APP → CONNECTOR → FUNCTION → METHOD/RECIPE → MATERIAL TYPE**

Nama app saja tidak cukup untuk menyatakan kemampuan.

### 2.2 Kelas Kemampuan Operasional

Kemampuan Production Engine mencakup bukan hanya **membuat materi**, tetapi juga kemampuan nyata untuk menangani hasil dan input produksi.

| Kelas operasi | Arti operasional |
|---|---|
| CREATE / GENERATE | Membuat materi baru |
| READ / OPEN | Membaca atau membuka materi/data |
| UPLOAD / INGEST | Mengirim materi/data ke app/platform |
| SAVE / STORE | Menyimpan secara persisten pada tujuan yang didukung |
| DOWNLOAD / EXPORT | Mengeluarkan atau mengambil file/data ke lingkungan lain |
| RETRIEVE / FETCH | Mengambil kembali asset/data berdasarkan ID, URL, atau reference |
| UPDATE / EDIT | Mengubah materi/data yang sudah ada |
| DELETE | Menghapus materi/data |
| MOVE / COPY | Memindahkan atau menggandakan materi/data |
| PREVIEW | Menampilkan hasil sebelum finalisasi |
| SHARE / REFERENCE | Menghasilkan atau menggunakan ID/URL/reference yang dapat dipakai proses berikutnya |
| TRANSFORM / CONVERT | Mengubah format, ukuran, dimensi, durasi, atau bentuk materi |
| API / AUTOMATION | Menjalankan operasi melalui API/otomasi yang benar-benar tersedia |
| VERIFY / STATUS | Memeriksa keberadaan, status, hasil, atau keberhasilan operasi |

**Setiap operasi adalah capability terpisah dan harus dibuktikan melalui uji nyata.**

### 2.3 Production Capability Registry

Workflow 02 memiliki **Production Capability Registry** yang mencatat:
- app/platform;
- connector;
- fungsi spesifik;
- kelas operasi;
- arah data/input-output;
- input;
- output;
- limit/free limit yang terbukti;
- persistence/save behavior;
- retrieval method;
- reference type (ID/URL/path atau lainnya);
- file/media constraints;
- dependency;
- kebutuhan akun/API key;
- watermark/license/commercial-use bila relevan;
- bukti uji;
- tanggal uji;
- status PASS/FAIL/BLOCKED/UNTESTED/CANDIDATE.

**Status berlaku per operasi/fungsi, bukan otomatis ke seluruh app.**

Satu app boleh memiliki:
- Generate Image = PASS
- Generate Video = UNTESTED
- Upload = BLOCKED
- Retrieve Asset = PASS
- Delete Asset = UNTESTED

### 2.4 Aturan Istilah Operasional

Agar tidak terjadi kekeliruan antara fungsi yang terlihat mirip:

- **Save/Store** = data/file benar-benar dipersistenkan pada tujuan penyimpanan yang didukung.
- **Upload** = data/file dikirim masuk ke app/platform.
- **Download/Export** = file/data dikeluarkan dari app/platform ke lingkungan lain.
- **Retrieve/Fetch** = asset/data yang sudah ada diambil kembali melalui ID, URL, reference, atau mekanisme resmi lainnya.
- **Delete** = data/file benar-benar dihapus dan hasil penghapusan dapat diverifikasi.
- **Share/Reference** = sistem menghasilkan atau menyediakan reference yang dapat digunakan proses berikutnya.
- **Preview** = hasil dapat dilihat/diperiksa sebelum finalisasi.
- **API/Automation** = operasi dapat dijalankan melalui jalur API/otomasi yang tersedia dan telah diuji.

Klaim bahwa sebuah app “bisa menyimpan”, “bisa upload”, atau “bisa download” belum menjadi PASS sampai jalur operasional MR.ONE terbukti.

## 3. Material Production Registry

Setiap jenis materi yang benar-benar akan diproduksi mempunyai profil.

Minimal:
- nama kelas materi;
- tujuan penggunaan;
- input wajib;
- output;
- format;
- ukuran/dimensi/durasi bila relevan;
- kualitas minimum;
- metadata wajib;
- QC profile;
- storage handoff;
- downstream compatibility;
- watermark/license;
- repeatability;
- status.

**Jenis materi adalah kelas produksi, bukan nama file individual.**

Konsep:

**MATERIAL TYPE → PRODUCTION RECIPE → OUTPUT → QC PROFILE → STORAGE HANDOFF**

Nama file, judul file, dan asset ID tertentu tidak menjadi memori permanen workflow.

## 4. Metadata Contract

Production Engine harus mengetahui **metadata yang wajib dibawa bersama materi**, tanpa mengambil alih penyimpanan atau publishing.

Metadata minimal:
- Job/Production ID;
- material type;
- production purpose;
- input/source reference;
- production method;
- app/platform;
- connector/function;
- operation type bila ada operasi file/media;
- output format;
- dimensions/duration bila relevan;
- QC status;
- asset/reference;
- storage status;
- handoff status;
- notes/issues.

Metadata adalah **kontrak informasi**, bukan storage.

## 5. Provenance / Jejak Produksi

Setiap hasil produksi yang dinyatakan siap harus dapat ditelusuri:

**INPUT/SOURCE → METHOD → APP/CONNECTOR/FUNCTION → OPERATION → OUTPUT → QC → STORAGE REFERENCE → HANDOFF**

Tujuan:
- mengetahui bagaimana materi dibuat;
- mengetahui tool/fungsi yang digunakan;
- mengetahui bagaimana file/media dipindahkan atau disimpan;
- mengulang produksi;
- mencari titik kegagalan;
- membedakan hasil nyata dari asumsi.

Jika provenance penting belum tersedia, hasil tidak boleh dianggap PASS final.

## 6. QC Profile

QC tidak dibuat sebagai daftar umum saja. Setiap material type dapat memiliki **QC Profile**.

QC minimum:
1. hasil benar-benar ada;
2. hasil dapat dibuka/diakses;
3. format benar;
4. isi sesuai permintaan;
5. kualitas minimum terpenuhi;
6. metadata wajib ada;
7. asset/reference dapat digunakan;
8. tidak ada error yang diketahui;
9. status pengujian jelas.

QC tambahan ditentukan berdasarkan jenis materi.

## 7. Jalur Produksi Lengkap

**PERMINTAAN PRODUKSI**  
↓  
**PRODUCTION INTAKE**  
↓  
**IDENTIFIKASI MATERIAL TYPE**  
↓  
**CEK CAPABILITY REGISTRY**  
↓  
**PILIH METHOD/RECIPE YANG SUDAH PASS**  
↓  
**JALANKAN APP + CONNECTOR + FUNCTION**  
↓  
**OPERASI INPUT/OUTPUT FILE ATAU MEDIA BILA DIPERLUKAN**  
↓  
**HASIL PRODUKSI**  
↓  
**QC PROFILE**  
↓  
**METADATA CONTRACT**  
↓  
**WORKFLOW 00 STORAGE HANDOFF**  
↓  
**ASSET + REFERENCE**  
↓  
**HANDOFF**

Jika belum ada method yang PASS, jangan membangun pipeline besar. Masuk ke jalur uji tuntas.

## 8. Production Intake

Sebelum produksi, tentukan:
- apa yang ingin dibuat;
- material type;
- tujuan;
- input yang tersedia;
- output yang dibutuhkan;
- operasi file/media yang dibutuhkan;
- metadata wajib;
- QC profile;
- storage requirement;
- dependency;
- capability yang dibutuhkan.

Kemudian cari **kemampuan yang sudah PASS**.

Jika tidak ada:

**CANDIDATE/UNTESTED → UJI KECIL → VERIFIKASI → PASS atau FAIL/BLOCKED**

## 9. Uji Tuntas Komponen

Setiap app/platform/connector/function baru wajib diperiksa:
- fungsi sebenarnya;
- akses/koneksi;
- input/output;
- limit/free limit;
- akun/API key;
- kemampuan create/read/upload/save/download/retrieve/update/delete/preview/reference/transform bila relevan;
- automation/API;
- watermark;
- lisensi/commercial use;
- dependency;
- risiko lock-in/kegagalan;
- bukti nyata.

Informasi promosi atau klaim situs bukan bukti kemampuan operasional MR.ONE.

## 10. Uji Tuntas Material

Setiap material type baru diperiksa:
- tujuan;
- input;
- output;
- format;
- kualitas;
- ukuran/dimensi/durasi;
- metadata;
- operasi file/media yang diperlukan;
- storage compatibility;
- downstream compatibility;
- watermark/license;
- verifiability;
- repeatability.

## 11. Tahapan Uji

### A — Identifikasi
Tentukan kebutuhan produksi dan capability yang diperlukan.

### B — Audit Kandidat
Petakan kandidat app/platform/connector/function/method dan operasi yang dibutuhkan.

Status awal:
- CANDIDATE
- UNTESTED

### C — Uji Nyata
Gunakan input kecil dan terkontrol.

### D — Verifikasi
Periksa output, format, kualitas, reference, persistence, retrieval, dependency, dan error.

### E — Penetapan Status
- **PASS** — terbukti sesuai kebutuhan.
- **FAIL** — diuji dan tidak memenuhi kebutuhan.
- **BLOCKED** — terhenti karena akses, izin, limit, koneksi, atau dependency.
- **UNTESTED** — belum diuji.
- **CANDIDATE** — kandidat belum resmi.

Hanya **PASS** yang boleh menjadi capability/method resmi.

## 12. Proof Before Build

Urutan wajib:

**AUDIT → TEST KECIL → VERIFIKASI → PASS → FORMALKAN → PERLUAS**

Jangan membangun pipeline besar sebelum satu metode kecil terbukti.

## 13. Storage Handoff

Production Engine **bukan storage utama**.

Jika hasil berupa media/content, gunakan jalur storage yang telah terbukti di Workflow 00.

Jika hasil berupa file/document, gunakan jalur file yang telah terbukti.

### 13.1 Adobe Express — capability yang sudah terbukti

Adobe Express melalui connector MR.ONE telah diuji nyata untuk:
- **SEARCH DESIGN** = PASS
- **FILL TEXT** = PASS pada pengujian awal
- **CHANGE BACKGROUND COLOR** = PASS
- **ANIMATE DESIGN** = PASS
- **DOWNLOAD/EXPORT PDF** = PASS
- **EDITOR/PREVIEW REFERENCE** = PASS
- **Adobe Express → Export PDF → Cloudinary → Retrieve/Verify** = PASS E2E

Adobe Express dapat dipakai sebagai **storage/master workspace tambahan untuk kelas desain/dokumen yang sesuai**, tetapi status storage persisten dan delivery harus dicatat berdasarkan operasi yang benar-benar terbukti.

**Tidak boleh disimpulkan:**
- semua format export Adobe tersedia melalui connector;
- semua jenis file dapat di-upload ke Adobe melalui connector;
- Published/Share Link adalah direct-download link.

### 13.2 Adobe reference vs direct download

Untuk Adobe Express:
- editor URL = REFERENCE / ACCESS;
- preview URL = REFERENCE / PREVIEW;
- exported PDF URL = DOWNLOAD/EXPORT output;
- Published/Share Link sebagai customer access = **CANDIDATE/UNTESTED untuk direct-download delivery** sampai diuji sebagai pengguna publik.

Jika customer delivery membutuhkan file download langsung dan Adobe belum terbukti memenuhi requirement tersebut, gunakan storage/delivery lane lain yang sudah PASS, misalnya Cloudinary bila batas file terpenuhi.

### 13.3 File-size constraints

Batas ukuran harus dicatat **per engine dan per storage**, bukan digabung.

Untuk Adobe Express yang sudah diaudit:
- Free account storage: **5 GB**
- PDF input/import: hingga **99 MB**
- image import desktop web: hingga **80 MB** untuk format gambar selain SVG; SVG hingga **250 KB**
- beberapa video quick actions: hingga **1 GB**, dengan batas durasi yang bergantung pada operasi.

Untuk Cloudinary yang sudah diaudit:
- image/raw: **10 MB**
- video: **100 MB**

Karena itu file Adobe yang lebih besar dari batas Cloudinary tidak otomatis dapat dipindahkan ke Cloudinary. Pilihan harus ditentukan setelah QC dan pengecekan ukuran.

Production Engine mencatat constraint ini; Workflow 00 tetap memiliki aturan routing storage.

## 14. Batas dengan Workflow Lain

### Workflow 00 — Storage
Memegang penyimpanan dan reference storage.

### Workflow 02 — Production Engine
Memegang produksi, capability registry, operasi file/media yang terbukti, material recipe, provenance, QC produksi, metadata contract, dan storage handoff.

### Workflow 01 — Publisher
Memegang publikasi dan verifikasi status publikasi.

Production Engine tidak perlu menghafal nama/nomor workflow downstream untuk setiap material. Ia hanya harus menghasilkan **handoff contract yang lengkap**.

## 15. Fallback

Jika method utama:
- tidak tersedia → cari capability kandidat yang sudah diaudit;
- gagal → FAIL dan uji kandidat lain;
- terblokir → BLOCKED;
- belum terbukti → UNTESTED.

Jangan mengganti metode secara diam-diam.

## 16. Catatan Pengujian

Setiap pengujian resmi minimal mencatat:
- tanggal;
- tujuan;
- material type;
- app/platform;
- connector/function;
- operation type;
- method/recipe;
- input;
- output;
- metadata;
- provenance;
- QC;
- evidence/reference;
- masalah;
- status.

## 17. Batas Workflow 02

Workflow 02 tidak:
- menjadi Publisher;
- menjadi storage utama;
- menganggap semua app otomatis boleh digunakan;
- menganggap semua material otomatis siap;
- mengunci tool sebelum diuji;
- mengklaim keberhasilan tanpa bukti;
- menyimpan nama file/asset individual sebagai prosedur permanen.

## 18. Status Dokumen

**DRAFT / UNTESTED.**

Versi 0.4 menambahkan registry konkret untuk capability Adobe Express yang telah diuji, jalur Adobe Express sebagai storage/master workspace tambahan untuk kelas desain/dokumen yang sesuai, pembedaan reference vs direct-download delivery, serta pencatatan batas ukuran Adobe Express secara terpisah dari batas Cloudinary.

Komponen konkret tetap harus ditambahkan **satu per satu setelah pengujian nyata**.
