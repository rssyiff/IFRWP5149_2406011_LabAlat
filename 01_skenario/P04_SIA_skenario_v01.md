### Tabel aktor
| Aktor             | Kedudukan                                        | Tujuan terhadap Sistem                                                                                                     |
| ----------------- | ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| Civitas Akademika | Aktor umum (baru)                                | Melihat kalender akademik dan menjadi aktor induk bagi Mahasiswa dan Dosen melalui pewarisan (inheritance).                |
| Mahasiswa         | Aktor khusus dari Civitas Akademika (aktor lama) | Warisan: Melihat kalender akademik. Langsung: Melihat jadwal kuliah, mengajukan KRS, mengunduh bukti KRS, dan melihat KHS. |
| Dosen             | Aktor khusus dari Civitas Akademika (baru)       | Warisan: Melihat kalender akademik. Langsung: Menginput nilai mahasiswa.                                                   |
| Admin Akademik    | Aktor tetap dari P2/P3                           | Mengelola jadwal kuliah dan data mahasiswa.                                                                                |
| Dosen Wali        | Aktor tetap dari P3                              | Memproses dan mengambil keputusan terkait pengajuan KRS mahasiswa.                                                         |


### Katalog gabungan
| ID       | Nama use case             | Aktor terkait     | Sumber kebutuhan | Status                            |
| -------- | ------------------------- | ----------------- | ---------------- | --------------------------------- |
| SIA-UC01 | Lihat Jadwal Kuliah       | Mahasiswa         | SIA-R01\*        | Tetap (P2)                        |
| SIA-UC02 | Kelola Jadwal Kuliah      | Admin Akademik    | SIA-R02\*        | Tetap (P2)                        |
| SIA-UC03 | Ajukan KRS                | Mahasiswa         | SIA-R03\*        | Tetap (P3); include UC04          |
| SIA-UC04 | Validasi KRS              | (disertakan UC03) | SIA-R03\*        | Tetap (P3)                        |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa         | SIA-R04\*        | Tetap (P3); extend ke UC03        |
| SIA-UC06 | Proses Keputusan KRS      | Dosen Wali        | SIA-R05/R06\*    | Tetap (P3)                        |
| SIA-UC07 | Lihat Kalender Akademik   | Civitas Akademika | SIA-R07          | **Baru**                          |
| SIA-UC08 | Input Nilai Mata Kuliah   | Dosen             | SIA-R08, R12     | **Baru**; direalisasikan SIA-CO01 |
| SIA-UC09 | Lihat KHS                 | Mahasiswa         | SIA-R09, R12     | **Baru**; direalisasikan SIA-CO02 |
| SIA-UC10 | Kelola Data Mahasiswa     | Admin Akademik    | SIA-R10, R11     | **Baru**; use case **umum**       |
| SIA-UC11 | Tambah Data Mahasiswa     | (lewat UC10)      | SIA-R11          | **Baru**; khusus dari UC10        |
| SIA-UC12 | Ubah Data Mahasiswa       | (lewat UC10)      | SIA-R11          | **Baru**; khusus dari UC10        |
| SIA-UC13 | Hapus Data Mahasiswa      | (lewat UC10)      | SIA-R11          | **Baru**; khusus dari UC10        |


## Generalization aktor
- Mahasiswa → Civitas Akademika
- Dosen → Civitas Akademika
Alasan: Mahasiswa dan Dosen sama-sama melihat kalender akademik, sehingga fungsi itu
cukup digambar satu kali dari Civitas Akademika.

## Generalization use case
- SIA-UC11 Tambah Data Mahasiswa → SIA-UC10 Kelola Data Mahasiswa
- SIA-UC12 Ubah Data Mahasiswa → SIA-UC10 Kelola Data Mahasiswa
- SIA-UC13 Hapus Data Mahasiswa → SIA-UC10 Kelola Data Mahasiswa

## Perilaku pembeda:
- Tambah menghasilkan satu data mahasiswa baru.
- Ubah menghasilkan perubahan atribut data mahasiswa yang sudah ada.
- Hapus menghasilkan terhapusnya data mahasiswa yang tidak memiliki data akademik aktif.

## Include dan extend (tetap dari Pertemuan 3)
- SIA-UC03 Ajukan KRS «include» SIA-UC04 Validasi KRS
- SIA-UC05 Unduh Bukti Pengajuan KRS «extend» SIA-UC03 Ajukan KRS

## Collaboration dan realization
| ID | Nama collaboration | Use case yang direalisasikan |
|---|---|---|
| SIA-CO01 | Input Nilai Mata Kuliah | SIA-UC08 Input Nilai Mata Kuliah |
| SIA-CO02 | Lihat KHS | SIA-UC09 Lihat KHS |

Alasan: kedua use case itu ditetapkan jobsheet sebagai use case utama yang
realisasinya ditunjukkan secara eksplisit.

## Tabel perbandingan P3 dan P4
| Kelompok                      | Isi                                                                                                                                                                                                                         |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Tetap                         | Aktor Mahasiswa, Admin Akademik, dan Dosen Wali; UC01 sampai UC06; include UC03 ke UC04; extend UC05 ke UC03 beserta condition dan extension point; seluruh asosiasi P3.                                                    |
| Berubah karena Generalization | Tidak ada garis lama yang berpindah. Berbeda dengan Lab, fungsi bersama Mahasiswa dan Dosen untuk melihat kalender akademik baru muncul pada P4, sedangkan use case Lihat Jadwal Kuliah tetap menjadi milik Mahasiswa saja. |
| Ditambah                      | Aktor Civitas Akademika dan Dosen; 2 generalization aktor; UC07 sampai UC13; 3 generalization use case; 2 collaboration dan 2 realization.                                                                                  |
Catatan: Dosen Wali tetap menjadi aktor terpisah. Jobsheet tidak meminta Dosen Wali sebagai bentuk khusus Dosen, dan hierarki dibuat satu tingkat saja.