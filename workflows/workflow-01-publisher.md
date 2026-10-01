# MR.ONE Workflow 01 — Publisher

**Status:** DRAFT / UNTESTED  
**Versi:** 0.3

## Tujuan
Aturan detail untuk workflow publishing: menerima content/job yang siap dipublikasikan, mengambil asset/link dari **Workflow 00 — Storage**, lalu meneruskannya ke jalur publishing.

## Aturan detail
1. Input harus memiliki identitas content/job.
2. Asset/link harus valid dan aktif.
3. **Sumber asset mengikuti Workflow 00 — Storage:**
   - **MEDIA/CONTENT** → Cloudinary → gunakan asset reference/URL yang dikembalikan.
   - **FILE/DOCUMENT** → Box → gunakan file ID/content reference bila jalur publishing memang membutuhkan file.
4. Publisher tidak membuat, menyimpan, atau menjadi tempat utama upload asset. Tugas storage ditangani oleh Workflow 00.
5. Platform tujuan harus jelas.
6. Caption/copy dan parameter publishing harus berasal dari input/job atau aturan sumber.
7. Metricool digunakan sebagai jalur publishing/scheduling bila connector yang diperlukan tersedia.
8. Buffer dapat digunakan sebagai jalur publishing/scheduling tambahan bila integrasinya tersedia dan telah diuji.
9. Hasil aksi harus diverifikasi.
10. Jika input, asset, connector, atau aksi tidak tersedia, status harus **FAIL / BLOCKED** dan tidak boleh diklaim berhasil.

## Handoff dari Workflow 00 — Storage
Publisher menerima minimal:
- **content/job ID**
- **asset type**: MEDIA/CONTENT atau FILE/DOCUMENT
- **storage source**: Cloudinary atau Box
- **asset reference**: URL, asset ID, file ID, atau content reference yang sesuai
- **publishing metadata** bila diperlukan

### Routing
**MEDIA/CONTENT → Cloudinary → asset reference/URL → Publisher → Metricool/Buffer**

**FILE/DOCUMENT → Box → file ID/content reference → Publisher → jalur tujuan yang mendukung file**

Jika storage source dan asset type tidak cocok, jangan lanjutkan publishing; tandai **FAIL / BLOCKED**.

## Connector
### Metricool
- Fungsi: publishing/scheduling.
- Kemampuan Read/Write/Create harus diverifikasi saat eksekusi.

### Buffer
- Fungsi: jalur publishing/scheduling tambahan.
- Integrasi dan kemampuan Create/Read harus diverifikasi saat eksekusi.
- Tidak dianggap aktif hanya karena tercantum dalam prosedur.

## Storage
Storage dikunci melalui **Workflow 00 — Storage**:
- Cloudinary = konten/media.
- Box = file/dokumen.
- Publisher hanya menggunakan hasil handoff storage dan tidak mengambil alih fungsi storage.

## Output
- Status aksi: scheduled / published / failed.
- Identitas job atau hasil connector jika tersedia.
- Catatan hasil untuk audit.
- Referensi asset yang digunakan.

## Test Status
**UNTESTED** — hubungan prosedural dengan Workflow 00 sudah ditulis, tetapi eksekusi publishing nyata end-to-end belum dilakukan.
