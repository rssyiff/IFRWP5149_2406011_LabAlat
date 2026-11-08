# Use Case Description dan Spesifikasi Diagram — SIA (P04)

Status: LATIHAN USE CASE DIAGRAM LANJUTAN
Sistem: Sistem Informasi Akademik
ID dan nama use case sama dengan katalog di 01_skenario/P04_SIA_skenario_v01.md.

## 1. SIA-UC08 — Input Nilai Mata Kuliah

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC08 — Input Nilai Mata Kuliah |
| Sumber kebutuhan | SIA-R08 |
| Tujuan | Nilai mata kuliah tersimpan oleh dosen pengampu |
| Aktor utama | Dosen |
| Aktor pendukung | Tidak ada |
| Pemicu | Dosen memilih fungsi input nilai untuk suatu mata kuliah |
| Prasyarat | Dosen telah terautentikasi; dosen adalah pengampu mata kuliah tersebut; masa perkuliahan telah berakhir |
| Collaboration | SIA-CO01 — Input Nilai Mata Kuliah |
| Pascakondisi berhasil | Nilai tersimpan dan belum berstatus dipublikasikan |
| Pascakondisi gagal | Tidak ada nilai baru yang tersimpan |
| Aturan bisnis/asumsi | Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. Nilai yang diinput belum dipublikasikan. Rentang nilai yang sah mengikuti ketentuan penilaian (belum ditetapkan; lihat pertanyaan terbuka di P04_SIA_kebutuhan_v01.md). |

Alur utama:

| Langkah | Tindakan dosen | Respons sistem |
|---|---|---|
| 1 | Memilih mata kuliah | Memeriksa bahwa dosen adalah pengampu; menampilkan formulir input nilai |
| 2 | Mengisi nilai | Menampung nilai |
| 3 | Mengirim nilai | Memeriksa nilai berada dalam rentang yang sah |
| 4 | — | Menyimpan nilai (belum dipublikasikan) |
| 5 | Melihat konfirmasi | Menampilkan konfirmasi penyimpanan |

Alur alternatif/pengecualian:

| Rujukan | Kondisi | Hasil |
|---|---|---|
| A1 (langkah 1) | Dosen bukan pengampu mata kuliah | Sistem menolak dan menampilkan pesan; langkah 2 sampai 5 tidak dijalankan; tidak ada nilai tersimpan (pascakondisi gagal) |
| A2 (langkah 3) | Nilai di luar rentang yang sah | Sistem menolak nilai tersebut dan tidak menyimpannya sampai dikoreksi; bila tidak dikoreksi, pascakondisi gagal berlaku |

## 2. SIA-UC09 — Lihat KHS

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC09 — Lihat KHS |
| Sumber kebutuhan | SIA-R09 |
| Tujuan | Mahasiswa memperoleh KHS untuk semester yang nilainya sudah dipublikasikan |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Tidak ada |
| Pemicu | Mahasiswa memilih fungsi Lihat KHS |
| Prasyarat | Mahasiswa telah terautentikasi |
| Collaboration | SIA-CO02 — Lihat KHS |
| Pascakondisi berhasil | KHS ditampilkan hanya dengan nilai yang sudah dipublikasikan |
| Pascakondisi gagal | Tidak ada KHS yang ditampilkan |
| Aturan bisnis/asumsi | Hanya nilai yang sudah dipublikasikan yang ditampilkan; nilai yang belum dipublikasikan tidak ditampilkan |

Alur utama:

| Langkah | Tindakan mahasiswa | Respons sistem |
|---|---|---|
| 1 | Memilih fungsi Lihat KHS | Mencari semester yang nilainya sudah dipublikasikan |
| 2 | — | Menampilkan KHS untuk semester tersebut |

Alur alternatif/pengecualian:

| Rujukan | Kondisi | Hasil |
|---|---|---|
| 1a | Belum ada semester yang nilainya dipublikasikan (asumsi minimal, bukan ketetapan skenario) | Sistem memberi tahu bahwa KHS belum tersedia (pascakondisi gagal) |

## 3. Spesifikasi hubungan diagram kumulatif (18 hubungan)

Tabel ini harus identik dengan tabel di 01_skenario/P04_SIA_skenario_v01.md.

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

Catatan:
- Relasi extend (baris 13) dilengkapi condition [mahasiswa memilih unduh] dan
  extension point Bukti pengajuan tersedia, seperti pada Pertemuan 3.
- Tidak ada asosiasi dari Mahasiswa atau Dosen ke SIA-UC07 (diwarisi dari
  Civitas Akademika).
- Tidak ada garis dari aktor ke collaboration.
- Dosen Wali hanya terhubung ke SIA-UC06; SIA-UC04 tidak punya aktor langsung.