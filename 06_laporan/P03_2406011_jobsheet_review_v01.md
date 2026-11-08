# Review Tugas SIA P03 — Uji Konsistensi dan Pemeriksaan

Berkas yang diperiksa:
- P03_SIA_kebutuhan_v01.md
- P03_SIA_skenario_v01.md (aktor, katalog, include, extend)
- P03_2406011_SIA_deskripsi_v01.md
- P03_2406011_SIA_usecase_v01.drawio / .png

## Uji konsistensi tiga situasi

### a. Validasi berhasil, mahasiswa tidak mengunduh bukti

| Pemeriksaan | Diagram | Deskripsi |
|---|---|---|
| Use case yang berjalan | Ajukan KRS, termasuk Validasi KRS (include) | SIA-UC01 langkah 1-6; langkah 3 menjalankan SIA-UC02 |
| Validasi | Validasi KRS dipanggil dari Ajukan KRS | SIA-UC02 langkah 1-4: valid, hasil kembali ke UC01 |
| Penyimpanan | - | UC01 langkah 4: pengajuan tersimpan, status Menunggu persetujuan dosen wali |
| Unduh bukti | Extend tidak aktif karena kondisi tidak terpenuhi | UC01 alur 5b: lanjut ke langkah 6; SIA-UC03 tidak dijalankan |
| Hasil akhir | - | Pascakondisi berhasil UC01: pengajuan tersimpan |

Hasil: konsisten. Pengajuan tetap berhasil tanpa unduh bukti.

### b. Validasi gagal

| Pemeriksaan | Diagram | Deskripsi |
|---|---|---|
| Use case yang berjalan | Ajukan KRS dan Validasi KRS | UC01 langkah 1-3; SIA-UC02 alur 1a, 2a, atau 3a |
| Hasil validasi | (kegagalan tidak digambar pada diagram) | SIA-UC02 menyatakan KRS tidak valid beserta alasan |
| Penyimpanan | - | UC01 alur 3a: pengajuan tidak disimpan |
| Unduh bukti | Extend tidak dapat terjadi | Langkah 4-6 UC01 tidak dijalankan, extension point (langkah 5) tidak tercapai, SIA-UC03 tidak tersedia |
| Hasil akhir | - | Pascakondisi gagal UC01: tidak ada pengajuan baru tersimpan |

Hasil: konsisten. Kegagalan dijelaskan di deskripsi, sesuai ketentuan jobsheet
bahwa diagram tidak dipakai sebagai pengganti alur proses.

### c. Validasi berhasil, mahasiswa memilih mengunduh bukti

| Pemeriksaan | Diagram | Deskripsi |
|---|---|---|
| Use case yang berjalan | Ajukan KRS, Validasi KRS, Unduh bukti pengajuan KRS | UC01 langkah 1-5, lalu SIA-UC03, lalu UC01 langkah 6 |
| Kondisi extend | Catatan: [mahasiswa memilih unduh] | UC01 alur 5a: [mahasiswa memilih unduh] |
| Extension point | Catatan: Bukti pengajuan tersedia | UC01 langkah 5: Bukti pengajuan tersedia |
| Arah panah extend | Unduh bukti pengajuan KRS ke Ajukan KRS | SIA-UC03 memperluas SIA-UC01 |
| Hasil akhir | - | Bukti diunduh; pengajuan tetap tersimpan |

Hasil: konsisten. Kondisi dan extension point sama pada diagram dan deskripsi.

Catatan keterkaitan: prasyarat SIA-UC04 (status Menunggu persetujuan dosen
wali) sama dengan pascakondisi berhasil SIA-UC01.

## Checklist

| Butir | Status |
|---|---|
| Setiap aktor mempunyai interaksi yang jelas | Sesuai (Mahasiswa: UC01, UC03; Dosen wali: UC04) |
| Use case sesuai kebutuhan dan berada di dalam batas sistem | Sesuai (SIA-R03 sampai R06 ke SIA-UC01 sampai UC04) |
| Include mengarah ke perilaku yang disertakan | Sesuai (UC01 ke UC02) |
| Extend mengarah ke use case dasar | Sesuai (UC03 ke UC01) |
| Extension point berada pada use case dasar | Sesuai (UC01 langkah 5) |
| Kondisi extend tercantum di diagram/catatan dan deskripsi | Sesuai |
| Pengajuan tetap berhasil tanpa perilaku tambahan | Sesuai (UC01 alur 5b) |
| Prasyarat dibedakan dari perilaku include | Sesuai (terautentikasi sebagai prasyarat, tidak ada include Login) |
| Alur alternatif menjelaskan kegagalan dan hasil akhirnya | Sesuai |
| Diagram dan deskripsi memakai nama serta ID yang sama | Nama sama; ID ada di katalog dan deskripsi, elips di diagram menampilkan nama |
| Sumber dapat dibuka kembali | [isi setelah uji buka ulang] |
| Ekspor sesuai sumber terkini | [isi setelah PNG diekspor] |
| Kebutuhan yang belum dimodelkan ditandai | Sesuai (SIA-R01 dan SIA-R02) |

## Hasil review pemeriksa

Pemeriksa : [nama rekan/asisten]
Temuan    : [arah panah, kondisi, extension point, pascakondisi; tulis "tidak ada temuan" bila memang tidak ada]

## Perbaikan setelah review

[tulis hanya perubahan yang benar-benar dilakukan; bila ada, simpan versi v02 dan ekspor ulang]

## Hasil uji buka ulang sumber

[tulis hasil sebenarnya setelah menyimpan, menutup, dan membuka kembali berkas .drawio]
