### Tabel Kebutuhan Use Case LAB

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

## Use case description baru

### Skenario Use Case LAB-UC11: Catat Pengembalian Peralatan

| Elemen | Deskripsi |
|---|---|
| ID dan Nama | LAB-UC11: Catat Pengembalian Peralatan |
| Sumber Kebutuhan | LAB-R09 dan LAB-R10 |
| Tujuan | Pengembalian tercatat dan status peminjaman serta kondisi peralatan terbarui. |
| Aktor Utama | Petugas Laboratorium |
| Pemicu | Petugas memilih fungsi pencatatan pengembalian dan menentukan peminjaman yang akan dikembalikan. |
| Prasyarat | Petugas telah terautentikasi. Peminjaman terpilih berstatus `Dipinjam`. |
| Pascakondisi Berhasil | Pengembalian tercatat dengan tanggal kembali dan kondisi peralatan. Status peminjaman menjadi `Selesai`. |
| Pascakondisi Gagal | Tidak ada pengembalian baru yang tercatat. Status peminjaman tidak berubah. |
| Include | LAB-UC12: Periksa Kondisi Peralatan |
| Collaboration | LAB-CO02: Catat Pengembalian Peralatan |


## Alur Utama
| Langkah | Tindakan Petugas | Respons Sistem |
|---|---|---|
| 1 | Memilih peminjaman yang akan dikembalikan. | Menampilkan data peminjaman terpilih dan statusnya. |
| 2 | Mengonfirmasi alat yang kembali dan jumlahnya. | Menampung konfirmasi petugas. |
| 3 | Tidak ada tindakan. | Memeriksa apakah status peminjaman adalah `Dipinjam`. |
| 4 | Tidak ada tindakan. | Menjalankan LAB-UC12 untuk memeriksa dan mencatat kondisi peralatan. |
| 5 | Menyimpan pencatatan pengembalian. | Menyimpan tanggal kembali dan kondisi peralatan, lalu mengubah status peminjaman menjadi `Selesai`. |
| 6 | Melihat konfirmasi. | Menampilkan ringkasan pengembalian. |

## Alur alternatif atau pengecualian
- A1: Status bukan Dipinjam (pada langkah 3): sistem menolak pencatatan dan menampilkan status peminjaman saat ini. Pascakondisi gagal berlaku; tidak ada data yang disimpan.
- A2: Kondisi Rusak Ringan atau Rusak Berat (pada langkah 4): sistem tetap menyimpan pencatatan, menandai kondisi tersebut pada data peralatan, dan pengembalian tetap tercatat. Kerusakan tidak otomatis menimbulkan denda pada model ini.
- A3: Jumlah alat yang kembali tidak sesuai (pada langkah 2): sistem meminta petugas memeriksa kembali isian sebelum penyimpanan; pencatatan tidak disimpan sampai jumlah sesuai atau dikoreksi.

