# MR.ONE Workflow 01 — Publisher

**Status:** DRAFT / UNTESTED  
**Versi:** 0.2

## Tujuan
Aturan detail untuk workflow publishing: menerima content/job yang siap dipublikasikan, mengambil asset/link sesuai storage yang ditentukan sumber, lalu meneruskannya ke jalur publishing.

## Aturan detail
1. Input harus memiliki identitas content/job.
2. Asset/link harus valid dan aktif.
3. Storage mengikuti workflow sumber; jangan mengasumsikan storage global.
4. Platform tujuan harus jelas.
5. Caption/copy dan parameter publishing harus berasal dari input/job atau aturan sumber.
6. Metricool digunakan sebagai jalur publishing/scheduling bila connector yang diperlukan tersedia.
7. Hasil aksi harus diverifikasi.
8. Jika input, asset, connector, atau aksi tidak tersedia, status harus **FAIL / BLOCKED** dan tidak boleh diklaim berhasil.

## Connector
### Metricool
- Fungsi: publishing/scheduling.
- Kemampuan Read/Write/Create harus diverifikasi saat eksekusi.

## Storage
Tidak dikunci di workflow ini. Ikuti storage yang ditetapkan workflow sumber.

## Output
- Status aksi: scheduled / published / failed.
- Identitas job atau hasil connector jika tersedia.
- Catatan hasil untuk audit.

## Test Status
**UNTESTED** — belum dilakukan eksekusi publishing nyata.
