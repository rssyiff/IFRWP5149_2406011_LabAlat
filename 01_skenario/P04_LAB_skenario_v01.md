Skenario berikut merupakan bahan latihan yang ditetapkan untuk jobsheet, bukan hasil pengumpulan kebutuhan laboratorium nyata. Skenario ini melanjutkan potongan model Pertemuan 3. Selain mahasiswa, dosen juga meminjam peralatan laboratorium untuk kegiatan praktikum dan penelitian. Mahasiswa dan dosen sama-sama dapat melihat ketersediaan peralatan dan mengajukan peminjaman. Petugas laboratorium mengelola data peralatan: menambah peralatan baru, mengubah data peralatan, dan menghapus data peralatan yang tidak lagi dipakai. Setelah peminjaman disetujui dan alat diambil, petugas mencatat pengembalian peralatan. Pada saat mencatat pengembalian, petugas memeriksa dan mencatat kondisi peralatan. Dua use case utama pada potongan model ini, Ajukan Peminjaman dan Catat Pengembalian Peralatan, ditunjukkan realisasinya oleh collaboration yang bersesuaian. Seluruh fungsi Pertemuan 3 tetap berlaku dan tetap digambar: pemeriksaan ketersediaan di dalam pengajuan, pencetakan bukti pengajuan oleh mahasiswa, proses keputusan peminjaman oleh petugas, dan laporan peminjaman untuk kepala laboratorium. Diagram Pertemuan 4 adalah diagram Pertemuan 3 yang ditambah, bukan diagram baru yang menggantikannya.


# Skenario LAB Pertemuan 4

| Aktor | Kedudukan | Tujuan terhadap Sistem |
|---|---|---|
| Peminjam | Umum (general), baru pada Pertemuan 4 | Peran umum bagi peminjam peralatan. Mewariskan fungsinya kepada Mahasiswa dan Dosen. |
| Mahasiswa | Khusus dari Peminjam, tetap dari Pertemuan 3 | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam), ditambah mencetak bukti pengajuan sebagai asosiasi khususnya sendiri. |
| Dosen | Khusus dari Peminjam, baru pada Pertemuan 4 | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam). |
| Petugas Laboratorium | Tetap dari Pertemuan 3 | Mengelola data peralatan, memproses keputusan peminjaman, dan mencatat pengembalian peralatan. |
| Kepala Laboratorium | Tetap dari Pertemuan 3 | Melihat laporan peminjaman. |


## Tabel Katalog Use Case

| ID | Nama Use Case | Peran dalam Model | Sumber Kebutuhan |
|---|---|---|---|
| LAB-UC01 | Lihat Ketersediaan Peralatan | Tetap dari Pertemuan 3. Fungsi aktor umum Peminjam. | LAB-R01, LAB-R07 |
| LAB-UC02 | Kelola Data Peralatan | Tetap dari Pertemuan 3. Use case UMUM bagi LAB-UC08, LAB-UC09, dan LAB-UC10. | LAB-R02, LAB-R08 |
| LAB-UC03 | Ajukan Peminjaman | Tetap dari Pertemuan 3. Fungsi aktor umum Peminjam. Menyertakan LAB-UC04 dan direalisasikan oleh LAB-CO01. | LAB-R03, LAB-R07 |
| LAB-UC04 | Periksa Ketersediaan | Tetap dari Pertemuan 3. Perilaku yang disertakan oleh LAB-UC03. | LAB-R03 |
| LAB-UC05 | Cetak Bukti Pengajuan | Tetap dari Pertemuan 3. Tambahan bersyarat pada LAB-UC03 melalui relasi `<<extend>>`. | LAB-R04 |
| LAB-UC06 | Proses Keputusan Peminjaman | Tetap dari Pertemuan 3. Fungsi utama petugas laboratorium. | LAB-R05 |
| LAB-UC07 | Lihat Laporan Peminjaman | Tetap dari Pertemuan 3. Fungsi utama kepala laboratorium. | LAB-R06 |
| LAB-UC08 | Tambah Data Peralatan | Baru pada Pertemuan 4. Use case KHUSUS dari LAB-UC02. | LAB-R08 |
| LAB-UC09 | Ubah Data Peralatan | Baru pada Pertemuan 4. Use case KHUSUS dari LAB-UC02. | LAB-R08 |
| LAB-UC10 | Hapus Data Peralatan | Baru pada Pertemuan 4. Use case KHUSUS dari LAB-UC02. | LAB-R08 |
| LAB-UC11 | Catat Pengembalian Peralatan | Baru pada Pertemuan 4. Fungsi utama petugas laboratorium dan direalisasikan oleh LAB-CO02. | LAB-R09 |
| LAB-UC12 | Periksa Kondisi Peralatan | Baru pada Pertemuan 4. Perilaku yang disertakan oleh LAB-UC11. | LAB-R10 |

## Tetapkan generalization aktor
Tuliskan dua keputusan pemodelan berikut pada berkas skenario, lengkap
dengan alasannya:
- Mahasiswa adalah bentuk khusus dari Peminjam, dan Dosen adalah
bentuk khusus dari Peminjam. Alasan: keduanya berbagi fungsi yang
sama, yaitu melihat ketersediaan peralatan dan mengajukan peminjaman.
- Asosiasi ke LAB-UC01 dan LAB-UC03 digambar satu kali, yaitu dari
Peminjam. Jangan menggambar garis yang sama dari Mahasiswa dan dari
Dosen.
- Asosiasi Mahasiswa ke LAB-UC05 Cetak Bukti Pengajuan tidak ikut
dipindahkan dan tidak dihapus, karena fungsi itu khusus mahasiswa.
Asosiasi ini menjadi contoh asosiasi tambahan milik aktor khusus.
- Periksa arah panah pada gambar: ujung segitiga kosong harus menempel
pada Peminjam, bukan pada Mahasiswa dan bukan pada Dosen. Karena
Peminjam digambar di tengah, panah Mahasiswa mengarah ke bawah dan
panah Dosen mengarah ke atas; keduanya berakhir pada Peminjam.

## Tabel 4.4 Perbandingan diagram Pertemuan 3 dan diagram Pertemuan 4
| Kelompok | Isi |
|---|---|
| Tetap sama dari Pertemuan 3 | Aktor Mahasiswa, Petugas Laboratorium, dan Kepala Laboratorium. Use case LAB-UC01 sampai LAB-UC07. Relasi `«include»` dari LAB-UC03 ke LAB-UC04. Relasi `«extend»` dari LAB-UC05 ke LAB-UC03, lengkap dengan condition `[mahasiswa memilih cetak]` dan extension point `Bukti pengajuan tersedia`. Asosiasi Petugas Laboratorium ke LAB-UC02 dan LAB-UC06. Asosiasi Kepala Laboratorium ke LAB-UC07. Asosiasi Mahasiswa ke LAB-UC05. |
| Berubah karena generalization aktor | Asosiasi ke LAB-UC01 dan LAB-UC03 yang pada Pertemuan 3 digambar dari Mahasiswa, kini digambar satu kali dari Peminjam. Fungsi Mahasiswa tidak hilang karena Mahasiswa mewarisinya dari Peminjam. Inilah satu-satunya perubahan garis pada diagram lama. Alasannya adalah aturan generalization, bukan penghapusan fungsi. |
| Ditambah pada Pertemuan 4 | Aktor Peminjam dan Dosen beserta dua generalization aktor. Use case LAB-UC08, LAB-UC09, dan LAB-UC10 beserta tiga generalization use case ke LAB-UC02. Use case LAB-UC11 dan LAB-UC12 beserta relasi `«include»` di antara keduanya dan asosiasi Petugas Laboratorium ke LAB-UC11. Collaboration LAB-CO01 dan LAB-CO02 beserta dua relasi realization. |

## Tetapkan generalization use case
- LAB-UC08, LAB-UC09, dan LAB-UC10 adalah bentuk khusus dari LABUC02 Kelola Data Peralatan. Alasan: ketiganya adalah bentuk khusus pengelolaan data peralatan.
- Tuliskan untuk setiap use case khusus satu kalimat perilaku pembedanya.
Tambah menghasilkan data peralatan baru. Ubah menghasilkan data peralatan yang berubah. Hapus menghasilkan data peralatan yang terhapus dengan syarat pada aturan studi kasus.

## Tetapkan collaboration dan realization
| ID | Nama Collaboration | Use Case yang Direalisasikan |
|---|---|---|
| LAB-CO01 | Ajukan Peminjaman | LAB-UC03: Ajukan Peminjaman |
| LAB-CO02 | Catat Pengembalian Peralatan | LAB-UC11: Catat Pengembalian Peralatan |
kedua use case tersebut adalah use case utama pada potongan model ini, sehingga realisasinya ditunjukkan secara eksplisit. Collaboration untuk use case lain tidak digambar pada pertemuan ini.