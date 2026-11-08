# Kebutuhan dan Batas — Sistem Informasi Akademik (P04)

Status: LATIHAN USE CASE DIAGRAM LANJUTAN
Sistem: Sistem Informasi Akademik

## Skenario

Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yang
dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang
diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu
Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan.
Admin Akademik mengelola data mahasiswa: menambah data mahasiswa baru,
mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case
utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya
oleh collaboration yang bersesuaian.

Ketentuan ini fiktif untuk praktikum.

## Kebutuhan

SIA-R01 dan SIA-R02: tetap berlaku, lihat Jobsheet Pertemuan 2.
SIA-R03 sampai SIA-R06: tetap berlaku, lihat Jobsheet Pertemuan 3.

| ID kebutuhan | Pernyataan kebutuhan |
|---|---|
| SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik |
| SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya |
| SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan |
| SIA-R10 | Admin Akademik dapat mengelola data mahasiswa |
| SIA-R11 | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa |
| SIA-R12 | Model menunjukkan collaboration yang merealisasikan Input Nilai Mata Kuliah dan Lihat KHS |

## Batas dan aturan yang sudah ditetapkan

- Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01 sampai SIA-R06 tetap
  mempunyai identitas berbeda.
- Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
- Kalender akademik adalah agenda resmi institusi (awal semester, batas
  KRS, masa ujian, dan sejenisnya), bukan jadwal kuliah pada Pertemuan 2.
- Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut.
- KHS hanya menampilkan nilai yang sudah dipublikasikan.
- Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data
  akademik aktif.
- Pengajuan KRS tetap digambar sebagai bagian diagram kumulatif dari
  Pertemuan 3.

## Di luar tugas

- Pembayaran.
- Perancangan basis data.

## Pertanyaan terbuka (tidak ditetapkan, tidak dimodelkan)

- [isi dengan hal yang tidak dijelaskan skenario; usulan di bawah]

## Hasil uji konsistensi

### Situasi A: Mahasiswa melihat kalender akademik

Pada diagram tidak ada garis asosiasi langsung dari Mahasiswa ke SIA-UC07
Lihat Kalender Akademik. Hal itu tetap benar karena Mahasiswa adalah bentuk
khusus dari Civitas Akademika (generalization), dan Civitas Akademika
berasosiasi dengan SIA-UC07. Aktor khusus mewarisi seluruh asosiasi aktor
umum, sehingga Mahasiswa dapat melihat kalender akademik. Garisnya digambar
satu kali dari aktor umum agar tidak digambar ulang dari tiap aktor khusus
(Dosen mewarisi hal yang sama).

Hasil: diagram dan deskripsi konsisten.

### Situasi B: Dosen yang bukan pengampu mencoba menginput nilai

Menurut deskripsi SIA-UC08, dosen pengampu adalah prasyarat. Pada alur
alternatif A1 (langkah 1), sistem menolak dan menampilkan pesan; langkah 2
sampai 5 tidak dijalankan. Tidak ada nilai yang tersimpan (pascakondisi
gagal SIA-UC08).

Hasil: konsisten dengan aturan "nilai hanya dapat diinput oleh dosen
pengampu mata kuliah tersebut".

### Situasi C: Admin Akademik menghapus data mahasiswa yang masih memiliki data akademik aktif

Menurut aturan tugas, Hapus Data Mahasiswa (SIA-UC13) hanya untuk mahasiswa
yang tidak memiliki data akademik aktif. Karena syarat itu tidak terpenuhi,
penghapusan tidak dapat dilakukan dan data mahasiswa tetap tersimpan.

Hasil: konsisten dengan aturan tugas dan dengan perilaku pembeda SIA-UC13
pada P04_SIA_skenario_v01.md. Arti "data akademik aktif" belum ditetapkan
dan tercatat sebagai pertanyaan terbuka.

