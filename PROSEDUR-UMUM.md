# PROSEDUR UMUM — MR.ONE Workflow Control Center

**Status:** DRAFT / UNTESTED  
**Versi:** 0.1

Dokumen ini adalah prosedur umum penggunaan seluruh workflow MR.ONE. Dokumen ini **terpisah dari aturan detail masing-masing workflow**.

## 1. Peran
- **GPT** adalah executor/orchestrator yang membaca dan menjalankan workflow melalui connector.
- **MR.ONE** adalah arsitektur/sistem kerja.
- **GitHub** adalah procedural memory / workflow library dan panel check-and-balance.
- Workflow menentukan aturan detail pekerjaannya.

## 2. Prosedur penggunaan
1. Terima perintah atau job dari pengguna.
2. Identifikasi workflow yang relevan.
3. Baca aturan detail workflow tersebut.
4. Periksa connector, akses, dan kemampuan aksi yang diperlukan sebelum eksekusi.
5. Ikuti urutan dan aturan workflow; jangan menebak prosedur yang tidak tertulis.
6. Verifikasi input, asset, link, dan parameter yang diwajibkan workflow.
7. Jalankan pekerjaan melalui connector yang ditetapkan.
8. Verifikasi hasil aksi.
9. Catat status hasil: **PASS / FAIL / BLOCKED**.
10. Jika terjadi kegagalan, ikuti fallback workflow dan jangan mengklaim pekerjaan berhasil tanpa bukti.

## 3. Aturan perubahan
- Workflow adalah sumber aturan detail.
- Perubahan dilakukan sebagai patch kecil dan terkontrol.
- Jangan mengubah workflow yang sudah PASS tanpa kebutuhan yang terbukti.
- Setelah perubahan, lakukan pengujian dan perbarui status.
- Jangan membangun fitur tambahan sebelum ada kebutuhan/proof.

## 4. Pemisahan tanggung jawab
- **Prosedur Umum:** cara menggunakan workflow.
- **Workflow 01–04:** aturan detail pekerjaan masing-masing.
- **GitHub Pages:** tampilan kontrol/check-and-balance, bukan mesin eksekusi.

## 5. Status
**UNTESTED** — struktur prosedur sudah dibuat, tetapi belum diuji melalui eksekusi workflow nyata.
