Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap pengajuan menjalankan validasi KRS yang memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil, sistem menyimpan pengajuan berstatus menunggu persetujuan dosen wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS dan memberikan catatan keputusan.

| ID      | Kebutuhan Tugas                                                            |
| ------- | -------------------------------------------------------------------------- |
| SIA-R01 | Mahasiswa dapat melihat jadwal kuliah.                                     |
| SIA-R02 | Admin akademik dapat mengelola jadwal kuliah.                              |
| SIA-R03 | Mahasiswa dapat mengajukan KRS.                                            |
| SIA-R04 | Sistem memvalidasi KRS sebagai bagian dari pengajuan.                      |
| SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan. |
| SIA-R06 | Dosen wali dapat memproses persetujuan atau penolakan KRS.                 |

Batas dan asumsi:
- Pengguna telah terautentikasi.
- Data mata kuliah, prasyarat, dan jadwal tersedia.
- Validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
- Unduh bukti tidak menjadi syarat keberhasilan pengajuan.
- KRS tersimpan belum berarti disetujui.
- Pembayaran, pengisian nilai, dan implementasi basis data berada di luar
tugas.

Deskripsi Use Case
1. SIA-R03 — Mengajukan KRS
| Elemen | SIA-R03 — Mengajukan KRS |
|---|---|
| Tujuan | Menghasilkan pengajuan KRS yang tersimpan di sistem. |
| Aktor utama | Mahasiswa |
| Sumber kebutuhan | SIA-R03 dan SIA-R04 |
| Pemicu | Mahasiswa memilih fungsi pengajuan KRS. |
| Prasyarat | Mahasiswa telah terautentikasi dan jadwal kuliah tersedia. |
| Pascakondisi berhasil | Pengajuan KRS berhasil tersimpan dan dapat diproses oleh dosen wali. |
| Pascakondisi gagal | Pengajuan KRS tidak tersimpan apabila validasi gagal. |
| Include | SIA-R04 — Memvalidasi KRS |
| Extension point | Bukti pengajuan tersedia setelah pengajuan berhasil dikonfirmasi. |
| Extend | SIA-R05 — Mengunduh Bukti Pengajuan, jika mahasiswa memilih opsi unduh. |

2. SIA-R04 — Memvalidasi KRS
| Elemen | SIA-R04 — Memvalidasi KRS |
|---|---|
| Tujuan | Memastikan pengajuan KRS memenuhi aturan akademik yang berlaku. |
| Aktor utama | Sistem |
| Sumber kebutuhan | SIA-R04 |
| Pemicu | Mahasiswa mengajukan KRS melalui SIA-R03. |
| Prasyarat | Mahasiswa telah mengisi data KRS yang akan diajukan. |
| Pascakondisi berhasil | KRS dinyatakan valid dan proses pengajuan dapat dilanjutkan. |
| Pascakondisi gagal | Sistem menampilkan informasi kesalahan validasi dan pengajuan tidak dilanjutkan sampai kesalahan diperbaiki. |
| Include | Dipanggil oleh SIA-R03 — Mengajukan KRS. |
| Alur alternatif | Jika validasi gagal, sistem menampilkan alasan kegagalan dan mahasiswa dapat memperbaiki data KRS. |
| Extend | Tidak ada. |

3. SIA-R05 — Mengunduh Bukti Pengajuan KRS

| Elemen | SIA-R05 — Mengunduh Bukti Pengajuan KRS |
|---|---|
| Tujuan | Menyediakan bukti pengajuan KRS yang dapat diunduh oleh mahasiswa setelah pengajuan berhasil. |
| Aktor utama | Mahasiswa |
| Sumber kebutuhan | SIA-R05 |
| Pemicu | Mahasiswa memilih opsi unduh bukti setelah pengajuan KRS berhasil divalidasi dan dikonfirmasi. |
| Prasyarat | Pengajuan KRS telah lolos validasi, berhasil disimpan, dan bukti pengajuan tersedia. |
| Pascakondisi berhasil | Bukti pengajuan KRS berhasil diunduh oleh mahasiswa, sedangkan data pengajuan tetap tersimpan di sistem. |
| Pascakondisi gagal | Sistem menampilkan informasi bahwa bukti pengajuan gagal diunduh. Data pengajuan KRS tetap tersimpan. |
| Extend | SIA-R03 — Mengajukan KRS, jika pengajuan berhasil dan mahasiswa memilih opsi unduh bukti. |
| Alur alternatif 1 | Jika mahasiswa tidak memilih opsi unduh bukti, proses pengajuan KRS tetap selesai tanpa menjalankan SIA-R05. |
| Alur alternatif 2 | Jika validasi KRS gagal, pengajuan tidak dilanjutkan sebagai pengajuan berhasil dan opsi unduh bukti tidak tersedia. |
| Include | Tidak ada. |

4. SIA-R06 — Memproses Keputusan KRS
| Elemen | SIA-R06 — Memproses Keputusan KRS |
|---|---|
| Tujuan | Memproses keputusan persetujuan atau penolakan pengajuan KRS mahasiswa. |
| Aktor utama | Dosen Wali |
| Sumber kebutuhan | SIA-R06 |
| Pemicu | Dosen wali memilih pengajuan KRS mahasiswa untuk diproses. |
| Prasyarat | Dosen wali telah terautentikasi dan pengajuan KRS tersedia untuk diperiksa. |
| Pascakondisi berhasil | Keputusan dosen wali tersimpan di sistem dan status pengajuan diperbarui menjadi Disetujui atau Ditolak. |
| Pascakondisi gagal | Keputusan tidak tersimpan dan status pengajuan tetap seperti sebelumnya. |
| Alur alternatif — Disetujui | Dosen wali menyetujui KRS, sistem menyimpan keputusan dan memperbarui status menjadi Disetujui. |
| Alur alternatif — Ditolak | Dosen wali menolak KRS, sistem menyimpan keputusan dan memperbarui status menjadi Ditolak. Jika diperlukan, alasan penolakan dicatat agar mahasiswa dapat melakukan perbaikan. |
| Include | Tidak ada. |
| Extend | Tidak ada. |
