Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa: menambah data mahasiswa baru, mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh collaboration yang bersesuaian.

## Kebutuhan tugas Pertemuan 4

| ID Kebutuhan | Deskripsi Kebutuhan |
|---|---|
| SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik. |
| SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya. |
| SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan. |
| SIA-R10 | Admin Akademik dapat mengelola data mahasiswa. |
| SIA-R11 | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa. |
| SIA-R12 | Model menunjukkan collaboration yang merealisasikan Input Nilai Mata Kuliah dan Lihat KHS. |

### Batas dan Asumsi

- Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01 dan SIA-R02 (Pertemuan 2) serta SIA-R03 sampai SIA-R06 (Pertemuan 3) tetap mempunyai identitas berbeda.
- Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
- Kalender akademik pada tugas ini adalah agenda resmi institusi, seperti awal semester, batas KRS, masa ujian, dan sejenisnya. Kalender akademik tidak disamakan dengan jadwal kuliah pada Pertemuan 2.
- Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. Nilai yang diinput belum terpublikasi sebelum dinyatakan resmi berdasarkan ketentuan tugas ini. KHS hanya menampilkan nilai yang sudah dipublikasikan.
- Hapus Data Mahasiswa hanya berlaku untuk mahasiswa yang tidak memiliki data akademik aktif. Ketentuan ini bersifat fiktif untuk latihan.
- Pengajuan KRS tetap digambarkan sebagai bagian dari diagram kumulatif Pertemuan 3. Pembayaran dan perancangan basis data berada di luar cakupan tugas ini.

## Hasil uji konsistensi

### Situasi A: Mahasiswa melihat kalender akademik tanpa garis asosiasi langsung

Hasil: **tetap benar menurut diagram.** Mahasiswa adalah bentuk khusus
dari Civitas Akademika (generalization). Civitas Akademika terhubung
dengan SIA-UC07 Lihat Kalender Akademik melalui satu asosiasi. Karena
aktor khusus mewarisi seluruh asosiasi aktor umum, Mahasiswa dapat
melakukan SIA-UC07 tanpa garis sendiri. Aktor khusus dapat dipakai di
setiap tempat aktor umum dapat dipakai (OMG UML 2.5.1). Hal yang sama
berlaku untuk Dosen. Jika garis Mahasiswa ke SIA-UC07 digambar, garis itu
justru berlebihan (asosiasi warisan digambar ulang).

Rujukan: SIA-R07; hubungan nomor 5, 10, dan 11 pada tabel hubungan.

### Situasi B: Dosen yang bukan pengampu mencoba menginput nilai

Hasil yang harus terjadi: **sistem menolak.** Menurut deskripsi
SIA-UC08, dosen harus menjadi pengampu mata kuliah (prasyarat). Pada
langkah 1, sistem memeriksa pengampu. Alur alternatif A1 berlaku: sistem
menolak akses input nilai dan menampilkan pesan penolakan. Pascakondisi
gagal berlaku: tidak ada nilai baru yang tersimpan dan data nilai tidak
berubah.

Rujukan: SIA-R08; SIA-UC08 prasyarat dan alur alternatif A1.

### Situasi C: Admin Akademik menghapus data mahasiswa yang masih memiliki data akademik aktif

Hasil yang harus terjadi: **penghapusan tidak dilakukan.** Aturan tugas
menetapkan bahwa Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak
memiliki data akademik aktif. Data mahasiswa tidak berubah dan tidak ada
data yang terhapus.

Catatan: aturan ini fiktif untuk latihan. Deskripsi lengkap SIA-UC13
tidak diminta pada tugas ini, sehingga perilaku rinci penolakan (misalnya
pesan yang ditampilkan) belum dimodelkan dan dicatat sebagai batasan.

Rujukan: SIA-R11; aturan batas tugas untuk Hapus Data Mahasiswa.