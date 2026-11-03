# Kebutuhan dan Batas — Sistem Informasi Akademik (P03)

Status: LATIHAN USE CASE DIAGRAM (bukan model lengkap sistem)

## Skenario

Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap
pengajuan menjalankan validasi KRS yang memeriksa kelengkapan,
prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil,
sistem menyimpan pengajuan berstatus menunggu persetujuan dosen
wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih
mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS
dan memberikan catatan keputusan.

Ketentuan ini fiktif untuk praktikum. Batas SKS, aturan pembayaran, dan
kewenangan institusi nyata tidak ditambahkan tanpa sumber.

## Kebutuhan tugas

| ID kebutuhan | Pernyataan kebutuhan                                                              |
| ------------ | --------------------------------------------------------------------------------- |
| SIA-R03      | Mahasiswa dapat mengajukan KRS                                                    |
| SIA-R04      | Sistem memvalidasi KRS sebagai bagian pengajuan                                   |
| SIA-R05      | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan         |
| SIA-R06      | Dosen wali dapat memproses persetujuan atau penolakan KRS                         |

Kode dimulai dari R03 agar kebutuhan jadwal SIA-R01 dan SIA-R02 dari
Pertemuan 2 tetap mempunyai identitas berbeda.

## Batas sistem dan aturan yang sudah ditetapkan

- Pengguna telah terautentikasi.
- Data mata kuliah, prasyarat, dan jadwal tersedia.
- Validasi memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal.
- Validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
- Pengajuan yang berhasil divalidasi berstatus menunggu persetujuan dosen wali.
- Unduh bukti tidak menjadi syarat keberhasilan pengajuan.
- KRS tersimpan belum berarti disetujui.
- Dosen wali menyetujui atau menolak KRS dan memberikan catatan keputusan.

## Di luar tugas

- Pembayaran.
- Pengisian nilai.
- Implementasi basis data.

## Belum dimodelkan pada P03 (ditandai, bukan dianggap selesai)

- SIA-R01 (Mahasiswa melihat jadwal kuliah) dan SIA-R02 (Admin akademik
  mengelola jadwal kuliah): sudah dikerjakan pada Pertemuan 2 dan tidak
  dimasukkan ke diagram KRS.

## Pertanyaan yang belum terjawab (tidak ditetapkan skenario, tidak dimodelkan)

- [isi hanya jika ada hal yang belum jelas dari skenario, misalnya apa yang
  terjadi setelah KRS ditolak. Jangan mengarang jawabannya.]
