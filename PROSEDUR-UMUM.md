# PROSEDUR UMUM — MR.ONE Workflow Control Center

**Berlaku untuk:** Workflow 01–04 dan workflow berikutnya yang ditambahkan  
**Status:** MASTER PROCEDURE / DRAFT — menunggu pengujian nyata  
**Versi:** 0.3

Dokumen ini adalah **prosedur penggunaan sistem yang berlaku untuk semua workflow MR.ONE**. Prosedur ini berada di luar workflow. Setiap workflow hanya menyimpan **aturan detail pekerjaan dan komponen yang sudah terbukti melalui pengujian**.

## 1. Peran sistem
- **GPT** adalah executor/orchestrator yang membaca aturan dan menjalankan pekerjaan melalui connector.
- **MR.ONE** adalah arsitektur/sistem kerja.
- **GitHub** adalah procedural memory / workflow library sekaligus panel check-and-balance.
- **Workflow** adalah sumber aturan detail untuk jenis pekerjaan tertentu.


## 2. Aturan global — pintu masuk MR.ONE
Dokumen ini adalah **aturan di depan pintu rumah**. Setiap kali GPT memasuki sistem MR.ONE, aturan global ini menjadi titik awal sebelum masuk ke workflow tertentu.

Prinsipnya:

**RUMAH MR.ONE → ATURAN GLOBAL → PILIH WORKFLOW → BUKA ATURAN RUANGAN → JALANKAN PROSEDUR RUANGAN**

Artinya:
- GPT harus memahami bahwa setiap workflow adalah **ruangan kerja yang terpisah** dan memiliki prosedur lokalnya sendiri.
- Aturan global berlaku lintas-workflow dan tidak boleh hilang hanya karena percakapan, sesi, hari, atau konteks berganti.
- Setelah workflow ditentukan, GPT harus membaca aturan workflow tersebut sebelum menjalankan pekerjaan.
- Aturan workflow yang sudah terdokumentasi menjadi **ingatan prosedural** untuk workflow tersebut; pengguna tidak perlu mengulang seluruh prosedurnya setiap kali meminta pekerjaan yang sama.
- GPT tidak boleh mencampur prosedur satu workflow dengan workflow lain.
- GPT harus memahami **hubungan global antar-workflow**, tetapi tidak boleh menganggap bahwa detail prosedur Workflow 01 otomatis berlaku di Workflow 02, 03, 04, dan seterusnya.
- Nama file, materi, atau pekerjaan tertentu **bukan ingatan permanen workflow** kecuali memang ditetapkan sebagai aturan atau data referensi. Detail tersebut diberikan atau ditemukan saat pekerjaan berlangsung.
- Jika pengguna meminta masuk ke workflow tertentu, GPT harus memperlakukan permintaan tersebut sebagai **masuk ke ruangan yang sudah memiliki aturan**, bukan sebagai pekerjaan baru yang prosedurnya harus dijelaskan ulang dari nol.
- Jika aturan lokal tidak tersedia, tidak jelas, atau belum diuji, GPT harus mengikuti status dokumentasi yang ada dan tidak mengarang prosedur.

### Model mental struktur

~~~
RUMAH MR.ONE
│
├── PINTU / ATURAN GLOBAL
│   ├── pahami sistem
│   ├── identifikasi pekerjaan
│   ├── pilih workflow
│   ├── buka aturan workflow
│   └── ikuti aturan ruangan tersebut
│
├── RUANGAN WORKFLOW 01
│   └── prosedur Publisher
│
├── RUANGAN WORKFLOW 02
│   └── prosedur Production Engine
│
├── RUANGAN WORKFLOW 03
│   └── prosedur Digital Product
│
└── RUANGAN WORKFLOW 04
    └── prosedur Content Video / News
~~~

**Aturan penting:**  
Global = cara memahami dan memasuki sistem.  
Lokal = cara bekerja di dalam workflow tertentu.

Dengan demikian, ketika konteks atau sesi berganti, GPT yang melanjutkan pekerjaan harus terlebih dahulu membaca **PROSEDUR-UMUM.md**, kemudian membaca aturan workflow yang diminta. Tujuannya adalah agar struktur, fungsi, batas, dan prosedur yang telah ditetapkan dapat dikenali kembali tanpa pengguna harus menjelaskan ulang seluruh sistem.

## 3. Prosedur wajib setiap ada permintaan pekerjaan
Sebelum melakukan pekerjaan apa pun:

1. **Terima dan pahami permintaan.**
2. **Identifikasi jenis pekerjaan** yang diminta.
3. **Tentukan workflow** yang sesuai: Workflow 01, 02, 03, atau 04.
4. **Buka dan baca aturan detail workflow tersebut terlebih dahulu.**
5. **Identifikasi komponen yang diwajibkan workflow**, meliputi bila relevan:
   - app/platform,
   - connector,
   - fungsi connector (Read / Write / Create / Upload / Retrieve / Publish),
   - storage/cloud,
   - database,
   - input dan output,
   - platform tujuan.
6. **Verifikasi ketersediaan dan akses** terhadap komponen yang akan digunakan sebelum eksekusi.
7. **Ikuti metode yang tertulis di workflow.** Jangan mengganti app, connector, storage, database, atau metode secara asumsi.
8. **Validasi input, asset, link, parameter, dan dependency** yang diwajibkan workflow.
9. **Jalankan pekerjaan** sesuai urutan workflow.
10. **Verifikasi hasil nyata** dari setiap tahap penting dan terutama hasil akhir.
11. **Catat hasil** sebagai PASS / FAIL / BLOCKED beserta penyebab atau bukti yang relevan.
12. Jika gagal, **ikuti fallback yang tertulis**. Jangan mengklaim berhasil tanpa bukti.
13. Jika metode yang diuji terbukti berhasil dan memang akan dijadikan metode resmi, **perbarui workflow terkait** dengan hasil pengujian tersebut melalui patch terkontrol.

## 4. Aturan pengisian setiap workflow
Setiap Workflow 01–04 harus menjelaskan secara spesifik:

- **Untuk apa workflow digunakan**
- **Jenis pekerjaan yang ditangani**
- **Input yang diterima**
- **Output yang dihasilkan**
- **Alur kerja detail**
- **App/platform yang benar-benar digunakan**
- **Connector yang benar-benar digunakan**
- **Fungsi connector yang digunakan** (Read / Write / Create / Upload / Retrieve / Publish, sesuai kebutuhan)
- **Storage/cloud yang digunakan**
- **Database yang digunakan**, bila ada
- **Platform tujuan**, bila ada
- **Dependency**
- **Validasi/QC**
- **Fallback**
- **Metode penggunaan oleh GPT**
- **Hasil pengujian**
- **Status: PASS / FAIL / UNTESTED**

Komponen tersebut **tidak ditetapkan berdasarkan asumsi**. Komponen resmi workflow ditentukan setelah metode nyata diuji.

## 5. Aturan pengujian
Untuk Workflow 01–04:

1. Bedah workflow terlebih dahulu.
2. Petakan kandidat app, connector, storage/cloud, database, dan platform.
3. Verifikasi koneksi dan kemampuan aktualnya.
4. Uji metode kerja nyata.
5. Hanya komponen dan metode yang terbukti berhasil yang dimasukkan sebagai metode resmi.
6. Jika belum diuji, tandai **UNTESTED**.
7. Jika gagal, tandai **FAIL/BLOCKED** dan jangan menyamarkannya sebagai PASS.

## 6. Aturan perubahan
- **Prosedur Umum** berlaku untuk seluruh workflow.
- **Workflow** menyimpan aturan detail masing-masing pekerjaan.
- Perubahan dilakukan sebagai patch kecil dan terkontrol.
- Workflow yang sudah PASS tidak diubah tanpa kebutuhan yang terbukti.
- Penambahan workflow baru dapat dibuat sebagai Workflow 05, 06, dan seterusnya tanpa mengubah prinsip prosedur umum.
- Jangan membangun fitur atau dependency tambahan sebelum ada kebutuhan/proof.

## 7. Pemisahan struktur
```
MR.ONE Workflow Control Center
│
├── PROSEDUR-UMUM.md              ← berlaku untuk semua workflow
│
└── workflows/
    ├── workflow-01-publisher.md
    ├── workflow-02-production-engine.md
    ├── workflow-03-product-digital.md
    └── workflow-04-content-video-news.md
```

Workflow 02–04 dapat dibuat/diisi setelah masing-masing dibedah dan diuji. Tidak ada komponen yang dianggap resmi sebelum pengujian.

## 8. Status dokumen
**MASTER PROCEDURE — DRAFT / BELUM DIUJI END-TO-END.**

Struktur dan aturan umum sudah ditetapkan. Pengujian berikutnya dilakukan pada Workflow 01 terlebih dahulu.


## 9. Pembaruan Operasional — Wajib Dibaca GPT pada Setiap Sesi Baru

Bagian ini menegaskan mekanisme kerja lintas-sesi berdasarkan checkpoint dan pengujian terbaru.

### 9.1 Subjek kewajiban membaca adalah GPT

Yang wajib membaca dan memahami prosedur sebelum bekerja adalah **GPT yang dipanggil untuk menjalankan pekerjaan**, termasuk GPT pada sesi baru setelah sesi sebelumnya ditutup.

**GPT = orkestrator sekaligus pelaksana teknis inti.**

**Iwan = owner/pemilik, pemberi ide/arah, decision maker, pemberi approval, dan operator manual hanya pada bagian yang memang memerlukan tindakan pengguna.**

Pembagian ini tidak berarti Iwan menyerahkan kepemilikan atau keputusan kepada GPT. GPT menjalankan pekerjaan teknis sesuai prosedur; Iwan tetap memegang keputusan akhir dan aset miliknya.

### 9.2 Prosedur wajib saat GPT masuk pada sesi baru

Pada setiap sesi baru, sebelum mulai bekerja atau melanjutkan pekerjaan, GPT WAJIB:

1. Membaca dan memahami **MASTER WORKSPACE terbaru** bila tersedia sebagai sumber kerja.
2. Membaca **PROSEDUR-UMUM.md**.
3. Membaca **checkpoint/status terakhir** yang relevan.
4. Membaca dan memahami **seluruh prosedur Workflow 01, 02, 03, dan 04**, bukan hanya workflow yang disebut pertama kali.
5. Memahami hubungan antar-workflow sebagai satu rangkaian.
6. Setelah itu, untuk pekerjaan yang akan dijalankan, menggunakan aturan lokal workflow yang relevan sebagai prosedur operasional detail.

Tujuannya adalah **GPT tidak meminta pengguna mengulang aturan yang sudah terdokumentasi** dan tidak memulai pekerjaan hanya berdasarkan ingatan percakapan yang parsial.

Jika ada aturan yang konflik, dokumen yang berbeda versi, atau prosedur yang tidak tersedia, GPT harus menunjukkan konflik/kekurangan tersebut secara spesifik dan tidak membuat asumsi diam-diam.

### 9.3 Aturan eksekusi dan perintah LANJUTKAN

Membaca dan memahami prosedur tidak sama dengan izin melakukan perubahan.

**GPT wajib membaca terlebih dahulu.**

Untuk perubahan/build/eksekusi teknis yang memerlukan persetujuan pengguna, GPT menunggu perintah eksplisit **LANJUTKAN** sebelum melakukan tindakan tersebut.

GPT tidak boleh mengubah workflow, repository, storage, connector, produk, atau konfigurasi hanya karena telah membaca prosedurnya.

### 9.4 Pembagian kerja teknis

Dalam proses pembuatan dan pemasaran produk digital:

- **GPT** menangani pekerjaan teknis yang dapat dilakukan melalui tool/connector: orkestrasi flow, penyusunan Product Brief, pemetaan capability, pemilihan method yang sudah PASS, pembuatan materi melalui engine yang tersedia, QC berbasis prosedur, penyusunan materi marketing, pengelolaan metadata/ID, handoff antar-workflow, dan eksekusi publishing ketika jalurnya tersedia serta diperintahkan.
- **Iwan** memberikan ide/arah, memilih atau menyetujui keputusan produk, memberikan approval, menyediakan atau menguasai aset miliknya, dan melakukan tindakan manual yang memang tidak tersedia bagi GPT.
- **Iwan tetap pemilik produk, aset asli, akun, dan keputusan bisnis.**
- GPT tidak mengambil alih keputusan kepemilikan atau keputusan akhir bisnis.

### 9.5 Aturan Product Master dan Storage

**File asli produk tidak dipindahkan ke Cloudinary hanya karena produk akan dipasarkan.**

Master product asset tetap berada pada storage asal sesuai jenis output yang memang digunakan:

- **Adobe Express** → master desain/PDF yang dibuat di Adobe.
- **Airtable** → master data/tracker/formula yang dibuat di Airtable.
- Storage lain hanya digunakan bila jalur tersebut memang sudah ditetapkan dan terbukti oleh Workflow 00/02.

**Cloudinary digunakan untuk media/content yang memang perlu menjadi asset media publikasi/marketing**, termasuk salinan/preview/screenshot/gambar/video promosi setelah produk selesai dan lolos QC.

Dengan demikian:

**PRODUCT MASTER → tetap di storage asal**

sedangkan:

**MEDIA PROMOSI → QC → Cloudinary → public media URL → Workflow 01 Publisher**

Cloudinary bukan pengganti storage master produk.

### 9.6 Fulfillment produk setelah pembelian

Marketing/publication asset tidak menjadi file delivery pelanggan secara otomatis.

Jika calon pembeli berminat:
1. Iwan menangani komunikasi/pembayaran sesuai mekanisme penjualan.
2. Setelah pembayaran diterima, **Iwan mengirim file/akses produk asli** dari storage asal yang sesuai.
3. File asli tidak diambil dari salinan marketing Cloudinary kecuali memang secara khusus ditetapkan sebagai file delivery dan jalurnya sudah terbukti.

GPT membantu menyiapkan proses dan materi, tetapi **fulfillment manual oleh Iwan tetap menjadi bagian yang ditetapkan pada arsitektur saat ini**.

### 9.7 Hubungan empat workflow untuk satu produk nyata

Untuk satu produk digital, pola utama adalah:

**WORKFLOW 03 — WHAT TO MAKE**
→ menentukan produk/material dan capability yang dibutuhkan

**WORKFLOW 02 — HOW TO MAKE**
→ memilih capability/method PASS
→ produksi
→ QC
→ storage handoff
→ Product Master/Output
→ kembali ke Workflow 03
→ READY TO SELL

**WORKFLOW 04 — PRODUCT MARKETING / EXPLAINER**
→ mengambil produk yang sudah nyata/QC PASS
→ menjelaskan masalah, kegunaan, cara penggunaan, manfaat, visual produk, dan CTA
→ tidak membocorkan cara produksi/recipe/prompt/internal production workflow
→ QC
→ Cloudinary untuk marketing media
→ READY TO PUBLISH

**WORKFLOW 01 — PUBLISHER**
→ menerima marketing asset siap publish
→ cek capability/koneksi
→ cek asset dan riwayat
→ validasi format
→ publish/schedule melalui jalur publisher yang tersedia
→ baca kembali status aktual
→ laporkan PUBLISHED/SCHEDULED/PENDING/FAILED/BLOCKED/UNVERIFIED.

### 9.8 Aturan Publisher yang tetap menjadi sumber utama

Untuk publishing, **Workflow 01 adalah sumber aturan detail Publisher**. Prosedur umum tidak menggantikan aturan tersebut.

GPT wajib mengikuti antara lain:
- materi harus siap publish;
- asset/reference harus cocok;
- riwayat publikasi harus diperiksa sebelum publish;
- **SCHEDULED/PENDING tidak sama dengan PUBLISHED**;
- status publikasi harus dibaca kembali dari platform;
- tidak boleh mengklaim “sudah posting/tayang” tanpa bukti status aktual;
- Metricool tetap merupakan publisher yang sudah terbukti dan dipertahankan;
- Cloudinary menjadi sumber media URL publik untuk media yang memang dipublikasikan melalui jalur tersebut;
- jika jalur tidak tersedia/terbukti, laporkan BLOCKED/UNVERIFIED/MANUAL sesuai kondisi nyata.

### 9.9 Anti-Lupa lintas-sesi

Aturan ini harus diperlakukan sebagai **prosedur pembukaan sesi**, bukan sebagai informasi opsional dari percakapan sebelumnya.

Urutan pembukaan:

**GPT BARU MASUK**
→ baca MASTER WORKSPACE
→ baca PROSEDUR-UMUM
→ baca checkpoint
→ baca seluruh Workflow 01–04
→ pahami hubungan antar-workflow
→ identifikasi pekerjaan pengguna
→ pilih workflow yang relevan
→ gunakan aturan lokalnya
→ baru eksekusi setelah izin yang diperlukan tersedia.

Jika informasi pekerjaan spesifik belum tersedia, GPT boleh meminta hanya informasi yang benar-benar belum dapat ditemukan dari sumber yang sudah tersedia. GPT tidak boleh meminta pengguna mengulang aturan yang sudah terdokumentasi.


## 10. Checkpoint Harian dan Catatan Kerja

`CHECKPOINT-HARIAN.md` adalah **titik checkpoint operasional** yang berada di sebelah `PROSEDUR-UMUM.md` pada root repository.

Fungsinya bukan menggantikan Prosedur Umum atau aturan workflow, tetapi menjaga **posisi kerja terakhir dan catatan laporan harian** agar pekerjaan dapat dilanjutkan tanpa kehilangan konteks operasional.

Aturan:
- Checkpoint terakhir selalu diperbarui mengikuti **pekerjaan aktif terbaru**.
- Setiap update wajib mencantumkan **tanggal, jam, bulan, dan tahun**.
- Catatan harian bersifat berurutan dan tidak menghapus riwayat pekerjaan sebelumnya.
- Setiap pekerjaan dicatat dengan salah satu status operasional: **SELESAI / TERTUNDA / TROUBLE / ERROR**.
- **SELESAI** hanya digunakan bila pekerjaan telah selesai dan hasilnya dapat diverifikasi.
- **TERTUNDA** harus mencantumkan alasan dan langkah berikutnya.
- **TROUBLE** digunakan untuk masalah operasional yang belum terselesaikan.
- **ERROR** digunakan untuk kegagalan/error teknis dan harus mencatat bukti atau penyebab bila diketahui.
- Materi/checkpoint dapat berganti mengikuti pekerjaan harian; checkpoint tidak mengunci materi lama sebagai materi produksi.
- Materi contoh/testing dapat diganti dengan materi pekerjaan nyata sesuai tahap proyek, tetapi bukti audit pengujian yang masih diperlukan tidak boleh dihapus sembarangan.
- Checkpoint harian **tidak boleh mengubah PASS / FAIL / UNTESTED / BLOCKED** workflow tanpa bukti pengujian sesuai aturan Workflow Control Center.

Pola kerja:

**PEKERJAAN HARIAN → CATAT HASIL → PERBARUI CHECKPOINT TERAKHIR → LANJUTKAN PEKERJAAN BERIKUTNYA**

Pada pembukaan sesi, GPT membaca `PROSEDUR-UMUM.md` dan `CHECKPOINT-HARIAN.md` untuk mengetahui aturan serta posisi kerja terakhir sebelum masuk ke workflow yang relevan.

## 11. AUTO-CHECKPOINT WATCHDOG — Penjaga Posisi Kerja

Untuk mengurangi kehilangan konteks ketika percakapan berhenti, sinyal terputus, aplikasi ditutup, atau pekerjaan tidak dilanjutkan, repository menggunakan mekanisme **AUTO-CHECKPOINT WATCHDOG** melalui GitHub Actions.

### 11.1 Prinsip

- Watchdog berjalan berkala dari GitHub Actions.
- Interval pemeriksaan ditetapkan **setiap 15 menit**, tetapi ambang idle yang memicu checkpoint adalah **1 jam tanpa commit pekerjaan baru**.
- Watchdog memeriksa **commit pekerjaan terakhir yang bukan commit AUTO-CHECKPOINT**.
- Jika commit pekerjaan tersebut telah berusia **1 jam atau lebih** dan belum pernah dibuatkan auto-checkpoint untuk commit tersebut, watchdog membuat catatan checkpoint otomatis.
- Auto-checkpoint **tidak mengubah status PASS / FAIL / UNTESTED / BLOCKED** workflow.
- Auto-checkpoint juga tidak boleh mengarang isi percakapan, pekerjaan, hasil, atau keputusan yang tidak tersimpan di repository.
- Karena GitHub tidak mengetahui isi percakapan ChatGPT secara langsung, auto-checkpoint hanya dapat mencatat **Last Known State yang tersedia di repository**: commit terakhir, waktu, branch, dan status bahwa tidak ada perubahan repository selama ambang waktu.
- Setelah auto-checkpoint dibuat, commit tersebut ditandai dengan identitas **AUTO-CHECKPOINT** sehingga watchdog tidak membuat salinan berulang untuk commit pekerjaan yang sama.

### 11.2 Fungsi saat sesi berikutnya dibuka

GPT wajib membaca:
**PROSEDUR-UMUM.md → CHECKPOINT-HARIAN.md → AUTO-CHECKPOINT WATCHDOG → workflow relevan.**

Jika percakapan sebelumnya berhenti tanpa penutupan normal, GPT menggunakan checkpoint terakhir dan auto-checkpoint sebagai **Last Known State**, lalu melanjutkan dari posisi yang terdokumentasi tanpa meminta pengguna mengulang aturan yang sudah tersedia.

### 11.3 Batas mekanisme

AUTO-CHECKPOINT adalah **penjaga keadaan repository**, bukan perekam isi percakapan secara real-time.

Jika tidak ada commit karena pekerjaan hanya berlangsung di dalam percakapan dan belum menghasilkan perubahan repository, watchdog tidak dapat mengetahui detail pekerjaan tersebut. Untuk itu, pekerjaan penting yang menghasilkan perubahan konteks harus tetap dicatat melalui checkpoint normal ketika perubahan tersebut tersedia.

### 11.4 Status panel

`index.html` menyediakan panel kecil **AUTO-CHECKPOINT WATCHDOG** yang menjelaskan:
- interval pemeriksaan: 15 menit;
- ambang idle: 1 jam;
- sumber keadaan: commit repository;
- fungsi: mencatat Last Known State ketika tidak ada commit pekerjaan baru;
- status terakhir dapat diperiksa melalui `CHECKPOINT-HARIAN.md`.

Pola operasional:

**PEKERJAAN → COMMIT / CHECKPOINT → TIDAK ADA COMMIT 1 JAM → WATCHDOG → AUTO-CHECKPOINT → SESI BARU MEMBACA LAST KNOWN STATE.**