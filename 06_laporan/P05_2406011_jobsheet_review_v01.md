# Laporan Review P05 — Pemeriksaan Temuan dan Perbaikan Artefak

**NIM/Nama:** 2406011 / As'syifa Ramdani  
**Pertemuan:** P05  
**Studi Kasus:** Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus (LAB) dan Sistem Informasi Akademik (SIA)

## 1. Hasil Pemeriksaan

Pemeriksaan dilakukan terhadap kelengkapan berkas skenario, kesesuaian isi tabel dengan use case, serta kelengkapan relasi UML pada diagram.

### a. Pemeriksaan skenario LAB

| Pemeriksaan | Kondisi Awal | Perbaikan |
|---|---|---|
| Tabel skenario LAB | Tabel lengkap hanya tersedia di draw.io | Memuat 12 tabel skenario ke berkas `.md` |
| Skenario LAB-UC04 | Alur alternatif dan akhir masih menyalin teks UC01 | Menulis ulang sesuai perilaku Periksa Ketersediaan (UC04) |

Hasil: diperlukan pemindahan seluruh tabel skenario ke berkas Markdown dan penyesuaian isi skenario LAB-UC04 agar sesuai dengan perilaku use case-nya.

### b. Pemeriksaan skenario SIA

| Pemeriksaan | Kondisi Awal | Perbaikan |
|---|---|---|
| Skenario SIA-UC07 sampai SIA-UC13 | Tabel tersedia di draw.io, tetapi belum tertulis pada berkas `.md` | Menulis seluruh skenario ke berkas Markdown |
| Kelengkapan berkas | Berkas skenario SIA masih kosong | Mengisi berkas dengan tabel skenario lengkap |

Hasil: skenario SIA perlu didokumentasikan secara lengkap dalam berkas Markdown agar konsisten dengan diagram.

### c. Pemeriksaan relasi extend

| Pemeriksaan | Kondisi Awal | Perbaikan |
|---|---|---|
| Relasi «extend» UC05 ke UC03 | Belum mencantumkan condition | Menambahkan condition `[mahasiswa memilih cetak]` |
| Kondisi perluasan | Belum dinyatakan pada relasi | Mencantumkan kondisi pada titik perluasan |

Hasil: relasi «extend» perlu dilengkapi condition agar perilaku tambahan hanya berjalan ketika kondisi terpenuhi.

## 2. Daftar Temuan dan Perbaikan

| No. | Temuan | Perbaikan yang Diperlukan | Alasan |
|---|---|---|---|
| 1 | Tabel skenario LAB lengkap hanya ada di draw.io | Memuat 12 tabel skenario ke `01_skenario/P05_2406011_LAB_skenario_v01.md` | Berkas skenario harus memuat tabel lengkap, bukan hanya indeks |
| 2 | Skenario alternatif dan akhir LAB-UC04 masih menyalin teks UC01 | Menulis ulang sesuai perilaku UC04 Periksa Ketersediaan | Setiap tabel skenario harus menggambarkan alur use case-nya sendiri |
| 3 | Skenario SIA belum tertulis pada berkas `.md` | Menulis skenario SIA-UC07 sampai SIA-UC13 ke `01_skenario/P05_2406011_SIA_skenario_v01.md` | Berkas skenario SIA masih kosong padahal tabel di draw.io sudah ada |
| 4 | Relasi «extend» UC05 ke UC03 belum memuat condition | Mencantumkan condition `[mahasiswa memilih cetak]` | Relasi extend wajib disertai condition pada titik perluasan |

## 3. Checklist Pemeriksaan

| Butir | Status |
|---|---|
| Dua belas tabel skenario LAB tersedia dalam berkas `.md` | Perlu diperbaiki |
| Skenario alternatif LAB-UC04 sesuai perilaku use case | Perlu diperbaiki |
| Skenario akhir LAB-UC04 sesuai perilaku use case | Perlu diperbaiki |
| Skenario SIA-UC07 sampai SIA-UC13 tersedia dalam berkas `.md` | Perlu diperbaiki |
| Relasi «extend» UC05 ke UC03 memiliki condition | Perlu diperbaiki |
| Diagram dan berkas Markdown konsisten | Menunggu pemeriksaan ulang |
| Berkas sumber dapat dibuka kembali | Belum diuji |
| Ekspor sesuai sumber terkini | Belum diuji |

## 4. Hasil Review Pemeriksa

**Pemeriksa:** [nama rekan/asisten]

**Temuan:** Terdapat empat temuan terkait kelengkapan dokumentasi skenario LAB dan SIA, kesesuaian alur skenario LAB-UC04, serta condition pada relasi «extend» UC05 ke UC03.

## 5. Perbaikan Setelah Review

| No. | Perbaikan | Berkas yang Diperbarui | Status |
|---|---|---|---|
| 1 | Memasukkan 12 tabel skenario LAB secara lengkap | `P05_2406011_LAB_skenario_v01.md` | [Belum/Selesai] |
| 2 | Memperbaiki alur alternatif dan akhir LAB-UC04 | `P05_2406011_LAB_skenario_v01.md` | [Belum/Selesai] |
| 3 | Menulis skenario SIA-UC07 sampai SIA-UC13 | `P05_2406011_SIA_skenario_v01.md` | [Belum/Selesai] |
| 4 | Menambahkan condition pada relasi «extend» | Diagram draw.io terkait | [Belum/Selesai] |

**Versi setelah perbaikan:** [isi versi aktual, misalnya v02 jika memang dibuat.]

## 6. Hasil Uji Buka Ulang Sumber

| Berkas | Hasil Pengujian |
|---|---|
| `P05_2406011_LAB_skenario_v01.md` | [Hasil sebenarnya] |
| `P05_2406011_SIA_skenario_v01.md` | [Hasil sebenarnya] |
| Diagram draw.io LAB | [Hasil sebenarnya] |
| Diagram draw.io SIA | [Hasil sebenarnya] |

**Kesesuaian ekspor:** [Isi hasil pemeriksaan PNG terhadap sumber draw.io terkini.]