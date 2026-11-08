# Aktor, Katalog Use Case, dan Keputusan Pemodelan — SIA (P04)

Status: LATIHAN USE CASE DIAGRAM LANJUTAN
Sistem: Sistem Informasi Akademik
Diagram P04 bersifat kumulatif: seluruh elemen Pertemuan 2 dan 3 dipertahankan,
lalu elemen baru Pertemuan 4 ditambahkan.

## 1. Aktor

| Aktor | Kedudukan | Tujuan terhadap sistem |
|---|---|---|
| Civitas Akademika | Umum (general), baru pada P04 | Melihat kalender akademik; mewariskan fungsinya ke Mahasiswa dan Dosen |
| Mahasiswa | Khusus dari Civitas Akademika; ada sejak P02 | Melihat kalender (diwarisi); melihat jadwal kuliah, mengajukan KRS, mengunduh bukti pengajuan, melihat KHS (asosiasi sendiri) |
| Dosen | Khusus dari Civitas Akademika, baru | Melihat kalender (diwarisi); menginput nilai mata kuliah |
| Admin Akademik | Tetap dari P02 | Mengelola jadwal kuliah dan data mahasiswa |
| Dosen Wali | Tetap dari P03 | Memproses keputusan KRS |

Kelima aktor digambar pada diagram kumulatif. Aktor yang baru adalah Civitas
Akademika dan Dosen.

## 2. Pemetaan ID use case dari P03 ke P04

ID dan nama pada katalog P04 mengikuti penomoran gabungan. Berkas dan diagram
P03 tidak diubah.

| Nama | ID di P03 | ID di P04 |
|---|---|---|
| Ajukan KRS | SIA-UC01 | SIA-UC03 |
| Validasi KRS | SIA-UC02 | SIA-UC04 |
| Unduh Bukti Pengajuan KRS | SIA-UC03 | SIA-UC05 |
| Proses Keputusan KRS | SIA-UC04 | SIA-UC06 |

## 3. Katalog use case gabungan

| ID | Nama use case | Aktor terkait | Sumber kebutuhan | Tetap/Baru |
|---|---|---|---|---|
| SIA-UC01 | Lihat Jadwal Kuliah | Mahasiswa | SIA-R01 | Tetap (P02) |
| SIA-UC02 | Kelola Jadwal Kuliah | Admin Akademik | SIA-R02 | Tetap (P02) |
| SIA-UC03 | Ajukan KRS | Mahasiswa | SIA-R03 | Tetap (P03); include UC04, diperluas UC05 |
| SIA-UC04 | Validasi KRS | Tidak ada (disertakan UC03) | SIA-R04 | Tetap (P03) |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa | SIA-R05 | Tetap (P03); extend UC03 |
| SIA-UC06 | Proses Keputusan KRS | Dosen Wali | SIA-R06 | Tetap (P03) |
| SIA-UC07 | Lihat Kalender Akademik | Civitas Akademika | SIA-R07 | Baru |
| SIA-UC08 | Input Nilai Mata Kuliah | Dosen | SIA-R08 | Baru; direalisasikan SIA-CO01 |
| SIA-UC09 | Lihat KHS | Mahasiswa | SIA-R09 | Baru; direalisasikan SIA-CO02 |
| SIA-UC10 | Kelola Data Mahasiswa | Admin Akademik | SIA-R10, SIA-R11 | Baru; use case umum bagi UC11, UC12, UC13 |
| SIA-UC11 | Tambah Data Mahasiswa | Admin Akademik (lewat UC10) | SIA-R11 | Baru; khusus dari UC10 |
| SIA-UC12 | Ubah Data Mahasiswa | Admin Akademik (lewat UC10) | SIA-R11 | Baru; khusus dari UC10 |
| SIA-UC13 | Hapus Data Mahasiswa | Admin Akademik (lewat UC10) | SIA-R11 | Baru; khusus dari UC10 |

Kalender akademik (SIA-UC07) adalah agenda resmi institusi dan berbeda dari
jadwal kuliah (SIA-UC01).

## 4. Tabel relasi diagram kumulatif (18 hubungan)

| No | Sumber | Jenis relasi | Tujuan | Status | Sumber kebutuhan |
|---|---|---|---|---|---|
| 1 | Mahasiswa | Association | SIA-UC01 Lihat Jadwal Kuliah | Tetap (P02) | SIA-R01 |
| 2 | Mahasiswa | Association | SIA-UC03 Ajukan KRS | Tetap (P03) | SIA-R03 |
| 3 | Mahasiswa | Association | SIA-UC05 Unduh Bukti Pengajuan KRS | Tetap (P03) | SIA-R05 |
| 4 | Mahasiswa | Association | SIA-UC09 Lihat KHS | Baru | SIA-R09 |
| 5 | Civitas Akademika | Association | SIA-UC07 Lihat Kalender Akademik | Baru | SIA-R07 |
| 6 | Dosen | Association | SIA-UC08 Input Nilai Mata Kuliah | Baru | SIA-R08 |
| 7 | Admin Akademik | Association | SIA-UC02 Kelola Jadwal Kuliah | Tetap (P02) | SIA-R02 |
| 8 | Admin Akademik | Association | SIA-UC10 Kelola Data Mahasiswa | Baru | SIA-R10 |
| 9 | Dosen Wali | Association | SIA-UC06 Proses Keputusan KRS | Tetap (P03) | SIA-R06 |
| 10 | Mahasiswa | Generalization → | Civitas Akademika | Baru | SIA-R07 |
| 11 | Dosen | Generalization → | Civitas Akademika | Baru | SIA-R07 |
| 12 | SIA-UC03 Ajukan KRS | «include» | SIA-UC04 Validasi KRS | Tetap (P03) | SIA-R03; SIA-R04 |
| 13 | SIA-UC05 Unduh Bukti Pengajuan KRS | «extend» | SIA-UC03 Ajukan KRS | Tetap (P03) | SIA-R05 |
| 14 | SIA-UC11 Tambah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa | Baru | SIA-R11 |
| 15 | SIA-UC12 Ubah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa | Baru | SIA-R11 |
| 16 | SIA-UC13 Hapus Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa | Baru | SIA-R11 |
| 17 | SIA-CO01 Input Nilai Mata Kuliah (collaboration) | Realization → | SIA-UC08 Input Nilai Mata Kuliah | Baru | SIA-R12 |
| 18 | SIA-CO02 Lihat KHS (collaboration) | Realization → | SIA-UC09 Lihat KHS | Baru | SIA-R12 |

Catatan relasi extend (baris 13): dilengkapi condition [mahasiswa memilih
unduh] dan extension point Bukti pengajuan tersedia, seperti pada Pertemuan 3.

Catatan pemeriksaan:
- Tidak ada asosiasi dari Mahasiswa atau Dosen ke SIA-UC07 (diwarisi dari
  Civitas Akademika).
- Tidak ada garis dari aktor ke collaboration.
- Dosen Wali hanya terhubung ke SIA-UC06; SIA-UC04 tidak punya aktor langsung.

## 5. Keputusan generalization aktor

Hierarki (satu tingkat):
- Civitas Akademika = aktor umum
- Mahasiswa = bentuk khusus dari Civitas Akademika
- Dosen = bentuk khusus dari Civitas Akademika

Fungsi yang diwarisi dari Civitas Akademika: SIA-UC07 Lihat Kalender Akademik
(SIA-R07).

Asosiasi langsung milik aktor khusus (tidak diwariskan):

| Aktor khusus | Asosiasi langsung |
|---|---|
| Mahasiswa | SIA-UC01 Lihat Jadwal Kuliah; SIA-UC03 Ajukan KRS; SIA-UC05 Unduh Bukti Pengajuan KRS; SIA-UC09 Lihat KHS |
| Dosen | SIA-UC08 Input Nilai Mata Kuliah |

Alasan pemodelan:
- Mahasiswa dan Dosen berbagi fungsi yang sama persis, yaitu melihat kalender
  akademik. Kesamaan ini berlaku sebagai agenda resmi institusi dan bukan
  kebetulan pada satu skenario. Nama peran umum Civitas Akademika membuat
  diagram lebih jelas.
- Asosiasi ke SIA-UC07 digambar satu kali, dari Civitas Akademika. Tidak ada
  garis yang sama dari Mahasiswa maupun dari Dosen.
- Fungsi yang hanya dilakukan satu peran tetap digambar sebagai asosiasi
  langsung dari peran itu, karena tidak dimiliki aktor umum maupun aktor
  khusus yang lain.
- Dosen Wali dan Admin Akademik tidak dimasukkan ke hierarki karena tidak
  berbagi fungsi bersama dengan peran lain pada skenario ini.

Penggambaran: panah generalization berupa garis utuh, ujung segitiga kosong,
tanpa label, digambar dari Mahasiswa dan dari Dosen menuju Civitas Akademika.
Segitiga kosong menempel pada Civitas Akademika.

## 6. Keputusan generalization use case

Use case umum: SIA-UC10 Kelola Data Mahasiswa (SIA-R10, SIA-R11).
Use case khusus: SIA-UC11 Tambah Data Mahasiswa, SIA-UC12 Ubah Data
Mahasiswa, SIA-UC13 Hapus Data Mahasiswa.

Alasan: ketiganya adalah bentuk khusus pengelolaan data mahasiswa. Semuanya
mewarisi tujuan, aktor terkait (Admin Akademik), dan perilaku dasar SIA-UC10,
serta menghasilkan data mahasiswa yang terkelola.

Perilaku pembeda:

| Use case khusus | Perilaku pembeda |
|---|---|
| SIA-UC11 Tambah Data Mahasiswa | Menghasilkan data mahasiswa baru yang tersimpan. |
| SIA-UC12 Ubah Data Mahasiswa | Menghasilkan data mahasiswa yang berubah. |
| SIA-UC13 Hapus Data Mahasiswa | Menghasilkan data mahasiswa yang terhapus, hanya untuk mahasiswa yang tidak memiliki data akademik aktif. |

Penggambaran: tiga panah generalization dari UC11, UC12, dan UC13 menuju UC10
(garis utuh, ujung segitiga kosong, tanpa label). Admin Akademik dihubungkan
dengan SIA-UC10 saja, tidak dengan UC11 sampai UC13.

## 7. Keputusan collaboration dan realization

| ID | Nama collaboration (sama dengan nama use case) | Use case yang direalisasikan |
|---|---|---|
| SIA-CO01 | Input Nilai Mata Kuliah | SIA-UC08: Input Nilai Mata Kuliah |
| SIA-CO02 | Lihat KHS | SIA-UC09: Lihat KHS |

Alasan: Input Nilai Mata Kuliah dan Lihat KHS adalah dua use case utama pada
potongan model ini (SIA-R12), sehingga realisasinya ditunjukkan secara
eksplisit. Collaboration untuk use case lain tidak digambar pada pertemuan ini.

Penggambaran:
- Collaboration digambar sebagai elips garis putus-putus di dalam batas sistem,
  di dekat use case yang direalisasikannya.
- Relasi realization digambar dari collaboration menuju use case: garis
  putus-putus, ujung segitiga kosong, tanpa label.
- Aktor tidak dihubungkan langsung dengan collaboration.
- Collaboration bukan use case tambahan, sehingga memakai ID SIA-CO, bukan
  SIA-UC. Satu collaboration merealisasikan tepat satu use case.