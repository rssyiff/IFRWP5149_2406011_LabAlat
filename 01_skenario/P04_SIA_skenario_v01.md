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

## Use case description

### SIA-UC08: Input Nilai Mata Kuliah

| Elemen | SIA-UC08: Input Nilai Mata Kuliah |
|---|---|
| ID dan nama | SIA-UC08: Input Nilai Mata Kuliah |
| Sumber kebutuhan | SIA-R08 dan SIA-R12 |
| Tujuan | Nilai mahasiswa pada mata kuliah yang diampu tercatat di sistem dengan status belum terpublikasi |
| Aktor utama | Dosen |
| Pemicu | Dosen memilih fungsi input nilai dan menentukan mata kuliah yang akan dinilai |
| Prasyarat | Dosen telah terautentikasi; dosen adalah pengampu mata kuliah yang dipilih; masa perkuliahan mata kuliah tersebut telah berakhir |
| Pascakondisi berhasil | Nilai mahasiswa tersimpan untuk mata kuliah terpilih dengan status belum terpublikasi |
| Pascakondisi gagal | Tidak ada nilai baru yang tersimpan; data nilai tidak berubah |
| Generalization | Tidak ada (bukan bagian hierarki use case) |
| Collaboration | SIA-CO01: Input Nilai Mata Kuliah |

**Alur utama**

| Langkah | Tindakan dosen | Respons sistem |
|---|---|---|
| 1 | Memilih mata kuliah yang akan dinilai | Memeriksa bahwa dosen adalah pengampu mata kuliah tersebut; menampilkan daftar mahasiswa peserta |
| 2 | Mengisi nilai setiap mahasiswa | Menampung isian nilai |
| 3 | Tidak ada | Memeriksa bahwa setiap nilai berada dalam rentang yang sah |
| 4 | Menyimpan nilai | Menyimpan nilai dengan status belum terpublikasi |
| 5 | Melihat konfirmasi | Menampilkan ringkasan nilai yang tersimpan |

**Alur alternatif atau pengecualian**

- **A1: Dosen bukan pengampu (pada langkah 1):** sistem menolak akses
  input nilai untuk mata kuliah tersebut dan menampilkan pesan penolakan.
  Pascakondisi gagal berlaku; tidak ada data yang disimpan.
- **A2: Nilai di luar rentang yang sah (pada langkah 3):** sistem menolak
  penyimpanan, menandai isian yang tidak sah, dan meminta dosen
  mengoreksinya. Nilai tidak disimpan sampai semua isian sah. Jika dosen
  membatalkan input, pascakondisi gagal berlaku.

**Aturan bisnis dan asumsi**

- Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut.
- Nilai yang baru diinput belum terpublikasi; KHS hanya menampilkan nilai
  yang sudah dipublikasikan.
- **Asumsi latihan:** rentang nilai yang sah adalah [ISI, misalnya 0 sampai
  100]. Jobsheet tidak menetapkan rentang ini.
- Proses dan pelaku publikasi nilai belum ditetapkan (pertanyaan terbuka).

---

### SIA-UC09: Lihat KHS (ringkas)

| Elemen | SIA-UC09: Lihat KHS |
|---|---|
| ID dan nama | SIA-UC09: Lihat KHS |
| Sumber kebutuhan | SIA-R09 dan SIA-R12 |
| Tujuan | Mahasiswa mengetahui hasil studi pada semester yang nilainya sudah dipublikasikan |
| Aktor utama | Mahasiswa |
| Pemicu | Mahasiswa memilih fungsi lihat KHS dan menentukan semester |
| Prasyarat | Mahasiswa telah terautentikasi |
| Alur ringkas | Mahasiswa memilih semester. Sistem mengambil nilai semester tersebut, **hanya yang sudah dipublikasikan**, lalu menampilkan KHS |
| Alur alternatif | A1: Semester terpilih belum memiliki nilai terpublikasi. Sistem menampilkan pesan bahwa KHS belum tersedia dan tidak menampilkan nilai apa pun |
| Pascakondisi berhasil | KHS semester terpilih tampil dan hanya memuat nilai yang sudah dipublikasikan

## Tabel hubungan diagram kumulatif SIA (18 hubungan)

| No | Sumber | Hubungan | Tujuan |
|---|---|---|---|
| 1 | Mahasiswa | Association (khusus, tetap dari P3) | SIA-UC01 Lihat Jadwal Kuliah |
| 2 | Mahasiswa | Association (khusus, tetap dari P3) | SIA-UC03 Ajukan KRS |
| 3 | Mahasiswa | Association (khusus, tetap dari P3) | SIA-UC05 Unduh Bukti Pengajuan KRS |
| 4 | Mahasiswa | Association (khusus, baru) | SIA-UC09 Lihat KHS |
| 5 | Civitas Akademika | Association | SIA-UC07 Lihat Kalender Akademik |
| 6 | Dosen | Association (khusus, baru) | SIA-UC08 Input Nilai Mata Kuliah |
| 7 | Admin Akademik | Association (tetap dari P2) | SIA-UC02 Kelola Jadwal Kuliah |
| 8 | Admin Akademik | Association | SIA-UC10 Kelola Data Mahasiswa |
| 9 | Dosen Wali | Association (tetap dari P3) | SIA-UC06 Proses Keputusan KRS |
| 10 | Mahasiswa | Generalization → | Civitas Akademika |
| 11 | Dosen | Generalization → | Civitas Akademika |
| 12 | SIA-UC03 Ajukan KRS | «include» (tetap dari P3) | SIA-UC04 Validasi KRS |
| 13 | SIA-UC05 Unduh Bukti Pengajuan KRS | «extend» (tetap dari P3) | SIA-UC03 Ajukan KRS |
| 14 | SIA-UC11 Tambah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa |
| 15 | SIA-UC12 Ubah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa |
| 16 | SIA-UC13 Hapus Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa |
| 17 | SIA-CO01 (collaboration) | Realization → | SIA-UC08 Input Nilai Mata Kuliah |
| 18 | SIA-CO02 (collaboration) | Realization → | SIA-UC09 Lihat KHS |

**Catatan pemeriksaan:**
- Tidak ada asosiasi warisan yang digambar ulang dari Mahasiswa atau Dosen ke SIA-UC07.
- Tidak ada garis dari aktor ke collaboration.
- SIA-UC07 hanya terhubung ke Civitas Akademika.
- Admin Akademik hanya terhubung ke SIA-UC02 dan SIA-UC10, tidak ke SIA-UC11, SIA-UC12, atau SIA-UC13.
- Tidak ada relasi baru terhadap SIA-UC04 selain include dari SIA-UC03.

