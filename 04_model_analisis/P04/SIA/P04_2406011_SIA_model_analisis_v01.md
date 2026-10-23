## Tabel relasi use case diagram kumulatif SIA (18 hubungan)

| No | Sumber | Jenis relasi | Tujuan | Status | Sumber kebutuhan |
|---|---|---|---|---|---|
| 1 | Mahasiswa | Association | SIA-UC01 Lihat Jadwal Kuliah | Tetap (P2) | Rujuk P2 |
| 2 | Mahasiswa | Association | SIA-UC03 Ajukan KRS | Tetap (P3) | Rujuk P3 |
| 3 | Mahasiswa | Association | SIA-UC05 Unduh Bukti Pengajuan KRS | Tetap (P3) | Rujuk P3 |
| 4 | Mahasiswa | Association | SIA-UC09 Lihat KHS | Baru | SIA-R09 |
| 5 | Civitas Akademika | Association | SIA-UC07 Lihat Kalender Akademik | Baru | SIA-R07 |
| 6 | Dosen | Association | SIA-UC08 Input Nilai Mata Kuliah | Baru | SIA-R08 |
| 7 | Admin Akademik | Association | SIA-UC02 Kelola Jadwal Kuliah | Tetap (P2) | Rujuk P2 |
| 8 | Admin Akademik | Association | SIA-UC10 Kelola Data Mahasiswa | Baru | SIA-R10 |
| 9 | Dosen Wali | Association | SIA-UC06 Proses Keputusan KRS | Tetap (P3) | Rujuk P3 |
| 10 | Mahasiswa | Generalization → | Civitas Akademika | Baru | SIA-R07 |
| 11 | Dosen | Generalization → | Civitas Akademika | Baru | SIA-R07 |
| 12 | SIA-UC03 Ajukan KRS | «include» | SIA-UC04 Validasi KRS | Tetap (P3) | Rujuk P3 |
| 13 | SIA-UC05 Unduh Bukti Pengajuan KRS | «extend» | SIA-UC03 Ajukan KRS | Tetap (P3) | Rujuk P3 |
| 14 | SIA-UC11 Tambah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa | Baru | SIA-R11 |
| 15 | SIA-UC12 Ubah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa | Baru | SIA-R11 |
| 16 | SIA-UC13 Hapus Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa | Baru | SIA-R11 |
| 17 | SIA-CO01 Input Nilai Mata Kuliah (collaboration) | Realization → | SIA-UC08 Input Nilai Mata Kuliah | Baru | SIA-R12 |
| 18 | SIA-CO02 Lihat KHS (collaboration) | Realization → | SIA-UC09 Lihat KHS | Baru | SIA-R12 |