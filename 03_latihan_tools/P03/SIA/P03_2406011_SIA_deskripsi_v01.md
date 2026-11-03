# Use Case Description — Sistem Informasi Akademik (P03)

Status: LATIHAN USE CASE DIAGRAM
ID dan nama use case sama dengan katalog di P03_SIA_skenario_v01.md.

## 1. SIA-UC01 — Ajukan KRS

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC01 — Ajukan KRS |
| Sumber kebutuhan | SIA-R03; SIA-R04 (melalui include); SIA-R05 (melalui extend) |
| Tujuan | Menghasilkan pengajuan KRS yang tersimpan di sistem |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Tidak ada |
| Pemicu | Mahasiswa memilih fungsi pengajuan KRS |
| Prasyarat | Mahasiswa telah terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia |
| Include | SIA-UC02 — Validasi KRS (langkah 3) |
| Extension point | Bukti pengajuan tersedia, pada langkah 5 |
| Extend | SIA-UC03 — Unduh bukti pengajuan KRS, jika [mahasiswa memilih unduh] |
| Pascakondisi berhasil | Pengajuan KRS tersimpan dengan status Menunggu persetujuan dosen wali |
| Pascakondisi gagal | Tidak ada pengajuan KRS baru yang berhasil tersimpan |
| Aturan bisnis/asumsi | Validasi gagal menyebabkan pengajuan belum berhasil tersimpan. Unduh bukti tidak menjadi syarat keberhasilan pengajuan. KRS tersimpan belum berarti disetujui. |

Alur utama:

| Langkah | Tindakan mahasiswa | Respons sistem |
|---|---|---|
| 1 | Membuka pengajuan KRS | Menampilkan daftar mata kuliah yang dapat dipilih |
| 2 | Memilih mata kuliah | Menampung pilihan mata kuliah |
| 3 | Mengirim pengajuan | Menjalankan SIA-UC02 (Validasi KRS) |
| 4 | — | Jika valid, menyimpan pengajuan dengan status Menunggu persetujuan dosen wali |
| 5 | Melihat konfirmasi | Menampilkan konfirmasi penyimpanan; mencapai extension point Bukti pengajuan tersedia |
| 6 | Mengakhiri pengajuan | Menutup proses pengajuan |

Alur alternatif/pengecualian:

| Rujukan | Kondisi | Hasil |
|---|---|---|
| 3a | Validasi KRS gagal (SIA-UC02 menyatakan tidak valid) | Sistem menampilkan alasan kegagalan; pengajuan tidak disimpan; use case berakhir tanpa pengajuan berhasil (pascakondisi gagal); langkah 4 sampai 6 tidak dijalankan |
| 5a | [mahasiswa memilih unduh] | Sistem menjalankan SIA-UC03; setelah selesai, alur kembali ke langkah 6 |
| 5b | Mahasiswa tidak memilih unduh | Alur langsung ke langkah 6; pengajuan tetap berhasil tersimpan |

## 2. SIA-UC02 — Validasi KRS

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC02 — Validasi KRS |
| Sumber kebutuhan | SIA-R04 |
| Tujuan | Memastikan pengajuan KRS lengkap, memenuhi prasyarat mata kuliah, dan bebas benturan jadwal |
| Aktor utama | Mahasiswa (melalui SIA-UC01) |
| Aktor pendukung | Tidak ada |
| Pemicu | Mahasiswa mengirim pengajuan pada SIA-UC01 langkah 3 |
| Prasyarat | Mahasiswa telah memilih mata kuliah; data mata kuliah, prasyarat, dan jadwal tersedia |
| Pascakondisi berhasil | KRS dinyatakan valid dan kendali kembali ke SIA-UC01 untuk menyimpan pengajuan |
| Pascakondisi gagal | KRS dinyatakan tidak valid beserta alasannya; pengajuan belum tersimpan |
| Aturan bisnis/asumsi | Validasi memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal. Tidak ada aturan lain (misalnya batas SKS) yang ditambahkan. |

Alur utama:

| Langkah | Tindakan mahasiswa | Respons sistem |
|---|---|---|
| 1 | — | Memeriksa kelengkapan pengajuan |
| 2 | — | Memeriksa prasyarat setiap mata kuliah yang dipilih |
| 3 | — | Memeriksa benturan jadwal antar mata kuliah yang dipilih |
| 4 | — | Menyatakan KRS valid dan mengembalikan hasil ke SIA-UC01 |

Alur alternatif/pengecualian:

| Rujukan | Kondisi | Hasil |
|---|---|---|
| 1a | Pengajuan tidak lengkap | Sistem menyatakan KRS tidak valid dan menyertakan alasan; langkah 2 sampai 4 tidak dijalankan |
| 2a | Prasyarat mata kuliah tidak terpenuhi | Sistem menyatakan KRS tidak valid dan menyertakan alasan; langkah 3 dan 4 tidak dijalankan |
| 3a | Terjadi benturan jadwal | Sistem menyatakan KRS tidak valid dan menyertakan alasan; langkah 4 tidak dijalankan |

Pada ketiga kasus, hasil tidak valid dikembalikan ke SIA-UC01 (alur 3a pada UC01).

## 3. SIA-UC03 — Unduh bukti pengajuan KRS

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC03 — Unduh bukti pengajuan KRS |
| Sumber kebutuhan | SIA-R05 |
| Tujuan | Mahasiswa memperoleh bukti pengajuan KRS yang dapat diunduh |
| Aktor utama | Mahasiswa |
| Aktor pendukung | Tidak ada |
| Pemicu | Mahasiswa memilih unduh bukti pada konfirmasi penyimpanan |
| Prasyarat | Pengajuan KRS telah lolos validasi dan tersimpan; extension point Bukti pengajuan tersedia pada SIA-UC01 langkah 5 tercapai |
| Extend | Memperluas SIA-UC01 — Ajukan KRS, pada extension point Bukti pengajuan tersedia, dengan kondisi [mahasiswa memilih unduh] |
| Pascakondisi berhasil | Bukti pengajuan KRS berhasil diunduh; data pengajuan tetap tersimpan |
| Pascakondisi gagal | Bukti tidak berhasil diunduh; data pengajuan tetap tersimpan |
| Aturan bisnis/asumsi | Unduh bukti tidak menjadi syarat keberhasilan pengajuan. Jika validasi gagal, pengajuan tidak tersimpan dan opsi unduh tidak tersedia. |

Alur utama:

| Langkah | Tindakan mahasiswa | Respons sistem |
|---|---|---|
| 1 | Memilih unduh bukti | Menyiapkan bukti pengajuan KRS |
| 2 | — | Menyediakan berkas bukti untuk diunduh |
| 3 | Menerima berkas bukti | Mengembalikan alur ke SIA-UC01 langkah 6 |

Alur alternatif/pengecualian:

| Rujukan | Kondisi | Hasil |
|---|---|---|
| 1a | Mahasiswa tidak memilih unduh | SIA-UC03 tidak dijalankan; pengajuan tetap selesai (SIA-UC01 alur 5b) |
| 2a | Bukti gagal disiapkan atau diunduh | Sistem menampilkan informasi bahwa bukti gagal diunduh; data pengajuan tetap tersimpan |

## 4. SIA-UC04 — Proses keputusan KRS

| Bagian | Isi |
|---|---|
| ID dan nama | SIA-UC04 — Proses keputusan KRS |
| Sumber kebutuhan | SIA-R06 |
| Tujuan | Menetapkan persetujuan atau penolakan pengajuan KRS mahasiswa |
| Aktor utama | Dosen wali |
| Aktor pendukung | Tidak ada |
| Pemicu | Dosen wali memilih pengajuan KRS yang menunggu persetujuan |
| Prasyarat | Dosen wali telah terautentikasi; pengajuan KRS berstatus Menunggu persetujuan dosen wali tersedia |
| Pascakondisi berhasil | Keputusan dan catatan keputusan tersimpan; status pengajuan menjadi Disetujui atau Ditolak |
| Pascakondisi gagal | Keputusan tidak tersimpan; status pengajuan tetap Menunggu persetujuan dosen wali |
| Aturan bisnis/asumsi | KRS tersimpan belum berarti disetujui. Hanya pengajuan yang telah tersimpan yang dapat diproses. Dosen wali memberikan catatan keputusan. |

Alur utama:

| Langkah | Tindakan dosen wali | Respons sistem |
|---|---|---|
| 1 | Memilih pengajuan KRS mahasiswa | Menampilkan rincian pengajuan |
| 2 | Memeriksa pengajuan dan memilih keputusan (setujui atau tolak) | Menampung keputusan |
| 3 | Memberikan catatan keputusan | Menampung catatan keputusan |
| 4 | Mengirim keputusan | Menyimpan keputusan dan catatan, lalu memperbarui status pengajuan |
| 5 | Melihat konfirmasi | Menampilkan hasil keputusan |

Alur alternatif/pengecualian:

| Rujukan | Kondisi | Hasil |
|---|---|---|
| 4a | Dosen wali memilih setujui | Sistem menyimpan keputusan dan catatan; status menjadi Disetujui |
| 4b | Dosen wali memilih tolak | Sistem menyimpan keputusan dan catatan; status menjadi Ditolak |
| 4c | Keputusan tidak berhasil disimpan | Sistem menampilkan informasi kegagalan; status pengajuan tetap seperti sebelumnya (pascakondisi gagal) |
