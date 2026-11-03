## Identifikasi Aktor

| No. | Nama Aktor | Deskripsi Peran |
|---|---|---|
| 1 | Mahasiswa | Melihat jadwal kuliah, mengajukan KRS, dan mengunduh bukti pengajuan jika diperlukan. |
| 2 | Admin Akademik | Mengelola jadwal kuliah. |
| 3 | Dosen Wali | Memproses pengajuan KRS dengan memberikan persetujuan atau penolakan. |

## Identifikasi Aktor dan Use Case SIA


| ID | Nama Use Case | Peran dalam Model |
|---|---|---|
| SIA-R01 | Melihat Jadwal Kuliah | Fungsi utama mahasiswa |
| SIA-R02 | Mengelola Jadwal Kuliah | Fungsi utama admin akademik |
| SIA-R03 | Mengajukan KRS | Fungsi utama mahasiswa |
| SIA-R04 | Memvalidasi KRS | Perilaku yang disertakan (*include*) dalam SIA-R03 |
| SIA-R05 | Mengunduh Bukti Pengajuan | Tambahan bersyarat (*extend*) pada SIA-R03 |
| SIA-R06 | Menyetujui / Menolak KRS | Fungsi utama dosen wali |

## Identifikasi Perilaku

| Sumber | Hubungan | Tujuan |
|---|---|---|
| Mahasiswa | Asosiasi | SIA-R01 |
| Mahasiswa | Asosiasi | SIA-R03 |
| Mahasiswa | Asosiasi | SIA-R05 |
| Admin Akademik | Asosiasi | SIA-R02 |
| Dosen Wali | Asosiasi | SIA-R06 |
| SIA-R03 | `<<include>>` | SIA-R04 |
| SIA-R05 | `<<extend>>` | SIA-R03 |

Keputusan Include

SIA-UC01 <<include>> SIA-UC02

Sumber: Ajukan KRS. Tujuan: Validasi KRS.
Alasan: setiap pengajuan menjalankan validasi (SIA-R04), sehingga Ajukan KRS tidak lengkap tanpa Validasi KRS.
Validasi dapat berhasil atau gagal; hasil gagal tidak berarti validasi bersifat opsional.
Letak pemanggilan: setelah mahasiswa mengirim pengajuan, sebelum pengajuan disimpan.
Keputusan Extend

SIA-UC03 <<extend>> SIA-UC01

Use case dasar: Ajukan KRS. Use case tambahan: Unduh bukti pengajuan KRS.
Extension point: Bukti pengajuan tersedia (pada konfirmasi penyimpanan).
Kondisi: [mahasiswa memilih unduh].
Alasan: pengajuan tetap berhasil tersimpan tanpa pengunduhan bukti (SIA-R05); unduhan hanya perilaku tambahan.
Tidak Dimodelkan pada P03
SIA-R01 dan SIA-R02 (jadwal kuliah): dikerjakan di Pertemuan 2, belum dimodelkan di P03.
Validasi gagal: alur alternatif pada deskripsi Ajukan KRS, bukan extend.
Pengguna terautentikasi: prasyarat, bukan include Login.