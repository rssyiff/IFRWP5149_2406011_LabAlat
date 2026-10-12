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