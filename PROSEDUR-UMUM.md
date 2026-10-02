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
