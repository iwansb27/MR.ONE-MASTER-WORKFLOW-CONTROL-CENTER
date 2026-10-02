# MR.ONE Workflow 01 — Publisher

**Status:** LOGIKA & JALUR PUBLISHER TERBUKTI  
**Versi:** 0.5  
**Fungsi:** Peta kerja tetap untuk mekanisme publishing, verifikasi, dan pengecekan riwayat publikasi MR.ONE.

## Prinsip Utama

Workflow 01 adalah **jalur publikasi**, bukan tempat produksi dan bukan storage utama.

Pola universal:

**MATERI SIAP PUBLISH → PUBLISHER → PLATFORM PUBLISHING → VERIFIKASI HASIL**

Publisher **tidak mengingat atau bergantung pada nomor/nama workflow asal**. Workflow asal hanya menyediakan materi dan metadata yang diperlukan. Publisher hanya mengingat mekanisme publishing, aturan validasi, verifikasi, dan pengecekan riwayat publikasi.

Perbedaan cara menghasilkan materi bukan tanggung jawab Publisher. **Logika Publisher tetap sama.**

## Aturan Detail

1. Input harus memiliki identitas content/job atau identitas materi yang dapat digunakan untuk mencocokkan riwayat.
2. Publisher menerima materi siap publish beserta asset reference dan metadata yang diperlukan. **Nama/nomor workflow asal tidak menjadi memori kerja Publisher.**
3. Sebelum membuat publikasi baru, Publisher wajib **memeriksa apakah materi sudah pernah dipublikasikan** berdasarkan metadata/riwayat yang tersedia di platform publishing.
   - **MEDIA/CONTENT → Cloudinary → gunakan asset reference/URL yang dikembalikan.**
   - **FILE/DOCUMENT → Box → gunakan file ID/content reference bila jalur publishing memang membutuhkan file.**
4. Asset yang akan dipublikasikan harus memiliki reference yang dapat diakses platform. Untuk media melalui Metricool, URL media harus publik, langsung menunjuk ke file gambar/video, dan tidak kedaluwarsa.
5. Publisher tidak membuat atau menjadi storage utama asset.
6. Platform tujuan harus jelas.
7. Metadata publishing harus dipetakan sebelum aksi:
   - content/job ID
   - asset type
   - asset reference/URL/file reference
   - caption/copy
   - title/description bila diperlukan
   - link/CTA bila diperlukan
   - target channel
   - tanggal
   - jam
   - timezone
   - status workflow/publishing
8. **Jika riwayat menunjukkan materi sudah PUBLISHED, Publisher tidak boleh membuat publikasi ulang hanya karena ada permintaan publish baru.** Publisher harus melaporkan bahwa materi sudah pernah dipublikasikan beserta riwayat yang ditemukan.
9. **Jadwal yang diminta harus benar-benar dibuat di platform publishing.** Pernyataan “sudah dijadwalkan” tidak boleh dibuat hanya berdasarkan niat atau pemanggilan tool.
10. Setelah aksi publishing dilakukan, **status aktual harus dibaca kembali dari platform** dan dicatat.
11. Publisher wajib membedakan sekurang-kurangnya:
   - **DRAFT** = masih draft, belum menjadi jadwal publikasi.
   - **PENDING** = menunggu/terjadwal sesuai status platform, tetapi belum published.
   - **SCHEDULED** = jadwal sudah tercatat pada platform.
   - **PUBLISHED** = platform mengonfirmasi konten sudah dipublikasikan.
   - **FAILED** = aksi gagal.
   - **BLOCKED** = tidak dapat dilanjutkan karena input, asset, connector, izin, atau kondisi lain tidak tersedia.
12. **Tidak boleh menyatakan “sudah posting”, “sudah publish”, atau “sudah tayang” tanpa bukti status aktual dari platform.**
13. Jika status aktual masih PENDING/SCHEDULED, laporan harus menyatakan masih tertunda/terjadwal dan tidak boleh disebut sudah tayang.
14. Jika aksi gagal atau status tidak dapat diverifikasi, hasil harus dilaporkan sebagai **FAILED / BLOCKED / UNVERIFIED**, bukan sebagai berhasil.
15. Jenis materi yang dipublikasikan harus diverifikasi dan dilaporkan sesuai kenyataan:
   - VIDEO
   - IMAGE
   - TEXT
   - LINK
   - atau tipe lain yang memang didukung platform.
16. Asset yang digunakan harus dicocokkan dengan job dan metadata yang diminta. Jangan sampai jadwal benar tetapi asset atau jenis kontennya salah.
17. Metricool digunakan sebagai jalur publishing/scheduling bila connector yang diperlukan tersedia.
18. Buffer dapat digunakan sebagai jalur publishing/scheduling tambahan bila integrasinya tersedia dan telah diuji.
19. Jika input, asset, connector, izin, atau aksi tidak tersedia, status harus **FAIL / BLOCKED** dan tidak boleh diklaim berhasil.

## Input Publisher / Storage Reference

Publisher menerima minimal:

- **content/job ID**
- **asset type**
- **storage source**
- **asset reference**
- **publishing metadata**
- **target platform/channel**
- **tanggal dan jam**
- **timezone**

### Routing

**MEDIA/CONTENT → Cloudinary → asset reference/URL → Publisher → Metricool/Buffer**

**FILE/DOCUMENT → Box → file ID/content reference → Publisher → jalur tujuan yang mendukung file**

Jika storage source dan asset type tidak cocok, jangan lanjutkan publishing; tandai **FAIL / BLOCKED**.

## Pemeriksaan Riwayat Sebelum Publish

Sebelum membuat publikasi baru, Publisher melakukan:

**IDENTIFIKASI MATERI → CEK RIWAYAT PLATFORM → JIKA SUDAH PUBLISHED: STOP & LAPORKAN → JIKA BELUM: LANJUT PUBLISH**

Riwayat publikasi tidak disimpan sebagai hafalan nama file di Workflow 01. Nama file/materi diberikan saat pengguna meminta pemeriksaan atau publikasi. Publisher kemudian mencari record/metadata publikasi yang relevan di platform.

Jika riwayat ditemukan dengan status **PUBLISHED**, Publisher melaporkan minimal tanggal/jam, channel/platform, dan status tersebut bila tersedia. Tidak perlu publish ulang kecuali pengguna secara eksplisit meminta tindakan lain yang memang berbeda dari publikasi ulang.

Jika hanya ditemukan **DRAFT/PENDING/SCHEDULED**, Publisher harus melaporkan kondisi tersebut dan tidak boleh menyebut materi sudah tayang.

## Pemetaan Status Wajib

Publisher harus memiliki laporan yang menunjukkan perjalanan job:

**INPUT READY → DRAFT → SCHEDULED/PENDING → PUBLISHED**

atau:

**INPUT READY → DRAFT → FAILED/BLOCKED**

Pada setiap tahap yang benar-benar dilakukan, catat **status aktual dari platform**.

Khusus perpindahan menuju published:

**SCHEDULED/PENDING ≠ PUBLISHED**

Published hanya boleh dicatat apabila platform memberikan bukti/status bahwa konten benar-benar sudah dipublikasikan.

## Laporan Wajib Setelah Aksi

Setiap perintah publishing harus menghasilkan laporan minimal:

| Field | Wajib |
|---|---|
| Job/content ID | Ya |

| Jenis konten | Ya |
| Asset source | Ya |
| Asset URL/reference | Ya |
| Platform/channel | Ya |
| Tanggal & jam target | Ya |
| Timezone | Ya |
| Status aktual platform | Ya |
| Status hasil MR.ONE | Ya |
| Keterangan | Ya |

Contoh:

**VIDEO → asset URL publik → Metricool → TikTok → 20:00 WIB → SCHEDULED/PENDING**

berarti **belum boleh dilaporkan sebagai tayang**.

Jika platform kemudian memberikan status:

**PUBLISHED**

barulah laporan:

**VIDEO → Cloudinary → Metricool → TikTok → PUBLISHED → berhasil tayang**

## Aturan Anti-Lupa / Anti-Klaim Palsu

> **Publisher tidak pernah menganggap pemanggilan tool sebagai bukti publikasi. Bukti publikasi adalah status aktual yang dikembalikan/terlihat pada platform publishing.**

> **Jadwal yang diminta pengguna harus dipetakan ke metadata jadwal yang benar-benar tercatat pada platform. Setelah itu statusnya harus diverifikasi dan dilaporkan.**

> **“Sudah dijadwalkan” dan “sudah tayang” adalah dua kondisi berbeda dan wajib dilaporkan berbeda.**

Aturan ini berlaku untuk **semua jenis konten** dan **semua workflow asal**.

## Connector — Metricool

Kemampuan berikut sudah terbukti dari penggunaan nyata sebelumnya:

- GPT dapat membuat content/copy.
- GPT dapat membuat scheduled post.
- GPT dapat menentukan tanggal dan jam.
- GPT dapat menggunakan Metricool untuk publishing workflow.
- Hasil pada Metricool dapat memiliki status seperti **PUBLISHED** dan **PENDING**.

**Catatan:** yang perlu dibuktikan per jenis asset pada tahap berikutnya adalah jalur baru **Storage Master → Publisher → Metricool**, bukan kemampuan dasar GPT → Metricool yang sudah terbukti.

## Storage

Storage dikunci melalui **Workflow 00 — Storage**:

- Cloudinary = konten/media.
- Box = file/dokumen.
- Publisher menggunakan hasil handoff storage dan tidak mengambil alih fungsi storage.

## Output

Output Publisher wajib berisi:

1. Status aksi.
2. Status aktual platform.
3. Identitas job/content.
4. Jenis konten.
5. Asset reference yang digunakan.
6. Platform/channel.
7. Jadwal yang tercatat.
8. Keterangan apakah **PUBLISHED, SCHEDULED/PENDING, FAILED, BLOCKED, atau UNVERIFIED**.
9. Catatan audit bila ada perbedaan antara permintaan dan hasil aktual.

## Bukti Dasar yang Sudah Ada

- **Cloudinary → asset tersimpan → URL publik dikembalikan → URL dapat digunakan sebagai asset reference:** TERBUKTI.
- **GPT → Metricool → content/copy → penentuan waktu → scheduled post:** TERBUKTI dari penggunaan nyata sebelumnya.
- **Metricool memiliki status aktual seperti PUBLISHED dan PENDING:** TERBUKTI dari data scheduled posts yang telah diperiksa.

## Test Status

**LOGIKA PUBLISHER: TERBUKTI & DITETAPKAN**

**E2E asset-specific:** mengikuti pengujian sumber asset masing-masing. Tidak perlu mengubah logika Publisher hanya karena jenis asset berbeda.

---

## Kalimat Pengingat Inti

> **Workflow 01 Publisher tidak mengingat nama/nomor workflow atau nama file secara permanen. Publisher mengingat mekanismenya: terima materi siap publish + asset reference + metadata → cek riwayat publikasi → jika sudah PUBLISHED, jangan publish ulang dan laporkan riwayat → jika belum, lakukan schedule/publish → baca kembali status aktual platform → laporkan hasil nyata.**

> **Untuk media yang dikirim ke Metricool melalui URL, URL harus publik, tidak kedaluwarsa, dan langsung menunjuk ke file gambar/video. URL halaman biasa bukan pengganti media URL. Link HTTPS untuk isi/caption dapat digunakan sebagai link publikasi; ini berbeda dari media URL yang menjadi lampiran file.**
