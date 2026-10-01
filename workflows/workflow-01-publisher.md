# MR.ONE Workflow 01 — Publisher

**Status:** DRAFT / UNTESTED  
**Versi:** 0.1  
**Peran:** Prosedural workflow library untuk GPT.

## 1. Tujuan
Menjadi aturan kerja untuk mengambil konten yang sudah diproduksi, memperoleh asset/link aktif dari storage yang ditentukan oleh workflow sumber, lalu meneruskannya ke jalur publishing melalui connector yang ditetapkan.

## 2. Prinsip
- **Workflow adalah sumber aturan.**
- GitHub menyimpan prosedur; GitHub Pages hanya menjadi panel check-and-balance.
- **GPT adalah executor/orchestrator** yang membaca workflow dan menjalankan connector.
- Jangan menebak storage atau lokasi asset. Ikuti storage yang dinyatakan pada workflow sumber.
- Jangan mempublikasikan asset yang belum memiliki input/link yang valid.
- Setiap perubahan workflow dilakukan sebagai patch kecil dan harus diuji.

## 3. Alur kerja
1. Terima permintaan publishing.
2. Identifikasi content/job yang akan dipublikasikan.
3. Baca workflow sumber untuk mengetahui **storage** dan cara memperoleh asset/link aktif.
4. Ambil atau verifikasi asset/link.
5. Validasi input minimum untuk publishing.
6. Kirim ke **Metricool** melalui connector yang tersedia.
7. Tentukan platform, waktu, caption, media, dan parameter lain hanya dari input/workflow yang diberikan.
8. Verifikasi hasil aksi publishing/scheduling dari connector.
9. Catat hasil test: **PASS / FAIL** beserta catatan singkat.

## 4. Connector
### Metricool
- Fungsi utama: jalur publishing/scheduling.
- Status koneksi: **gunakan hanya setelah akses connector diverifikasi pada saat eksekusi**.
- Hak aksi yang dibutuhkan: Read untuk verifikasi dan Write/Create untuk scheduling/publishing, sesuai kemampuan connector yang tersedia.

## 5. Storage
**Tidak dikunci di Workflow 01.**  
Storage mengikuti workflow sumber dari asset yang akan dipublikasikan. Contoh arsitektur dapat menggunakan storage berbeda untuk jenis asset berbeda; GPT tidak boleh mengasumsikan satu storage global.

## 6. Input minimum
- Identitas content/job.
- Asset atau active link yang valid.
- Platform tujuan.
- Caption/copy atau sumber caption.
- Waktu publishing/scheduling bila diperlukan.

## 7. Output
- Status aksi: scheduled / published / failed.
- Identitas job atau hasil dari connector jika tersedia.
- Catatan audit singkat.

## 8. Fallback
Jika connector atau asset tidak dapat digunakan:
- **Jangan mengarang keberhasilan.**
- Tandai **FAIL / BLOCKED**.
- Catat penyebab dan hentikan langkah yang bergantung pada input tersebut.

## 9. Test Status
**UNTESTED** — workflow baru didokumentasikan; belum digunakan untuk eksekusi publishing nyata.
