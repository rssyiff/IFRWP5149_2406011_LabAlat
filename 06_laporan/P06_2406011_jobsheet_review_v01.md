# Laporan Review P06 — Pemeriksaan Temuan dan Perbaikan Artefak

**NIM/Nama:** 2406011 / As'syifa Ramdani  
**Pertemuan:** P06  
**Studi Kasus:** Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus (LAB) dan Sistem Informasi Akademik (SIA)

## 1. Hasil Pemeriksaan

Pemeriksaan dilakukan terhadap kesesuaian aksi pada cabang decision Activity Diagram serta kesesuaian hasil ekspor PNG dengan berkas sumber draw.io terkini.

### a. Pemeriksaan cabang decision Activity Diagram

| Pemeriksaan | Kondisi Awal | Perbaikan |
|---|---|---|
| Cabang `[tidak tersedia]` pada diagram Lihat Ketersediaan | Aksi masih menyalin teks cabang `[tersedia]` | Menulis pesan khusus untuk kondisi tidak tersedia |
| Kesesuaian pesan | Pesan belum membedakan kedua kondisi | Menyesuaikan pesan berdasarkan hasil decision |

Hasil: diperlukan perbaikan teks aksi pada cabang `[tidak tersedia]` agar sesuai dengan kondisi yang dihasilkan decision.

### b. Pemeriksaan ekspor PNG Activity Diagram LAB

| Pemeriksaan | Kondisi Awal | Perbaikan |
|---|---|---|
| PNG diagram keputusan | Belum diperbarui setelah koreksi label | Mengekspor ulang dari sumber draw.io terkini |
| PNG diagram kelola data | Belum diperbarui setelah koreksi label | Mengekspor ulang dari sumber draw.io terkini |
| PNG diagram peminjaman | Belum diperbarui setelah koreksi label | Mengekspor ulang dari sumber draw.io terkini |

Hasil: ketiga gambar ekspor perlu diregenerasi agar mencerminkan label terbaru pada diagram sumber.

### c. Pemeriksaan ekspor PNG Activity Diagram SIA

| Pemeriksaan | Kondisi Awal | Perbaikan |
|---|---|---|
| Activity Diagram SIA tahap akhir (L4) | PNG belum sesuai dengan sumber terkini | Mengekspor ulang `P06_2406011_SIA_activity_v01-L4.png` |
| Kesesuaian label | Ekspor belum merefleksikan koreksi label terakhir | Menggunakan sumber draw.io versi terbaru |

Hasil: ekspor PNG tahap L4 perlu diperbarui agar sesuai dengan koreksi terakhir pada sumber diagram.

## 2. Daftar Temuan dan Perbaikan

| No. | Temuan | Perbaikan yang Diperlukan | Alasan |
|---|---|---|---|
| 1 | Aksi cabang `[tidak tersedia]` pada diagram lihat ketersediaan masih menyalin teks cabang `[tersedia]` | Menulis teks pesan khusus untuk kondisi tidak tersedia | Setiap cabang decision harus memakai pesan yang sesuai kondisinya |
| 2 | Ekspor PNG keputusan, kelola data, dan peminjaman belum diregenerasi setelah koreksi label | Mengekspor ulang PNG dari sumber draw.io terkini | Gambar ekspor harus sesuai versi terakhir berkas sumber |
| 3 | Ekspor PNG SIA tahap akhir (L4) belum sesuai sumber terkini | Mengekspor ulang `P06_2406011_SIA_activity_v01-L4.png` | Ekspor harus merefleksikan koreksi label terakhir |

## 3. Checklist Pemeriksaan

| Butir | Status |
|---|---|
| Cabang `[tersedia]` memiliki aksi yang sesuai | Menunggu pemeriksaan ulang |
| Cabang `[tidak tersedia]` memiliki pesan khusus | Perlu diperbaiki |
| Aksi pada setiap cabang sesuai dengan kondisi decision | Menunggu pemeriksaan ulang |
| PNG diagram keputusan telah diekspor ulang | Perlu diperbaiki |
| PNG diagram kelola data telah diekspor ulang | Perlu diperbaiki |
| PNG diagram peminjaman telah diekspor ulang | Perlu diperbaiki |
| PNG SIA tahap akhir (L4) telah diekspor ulang | Perlu diperbaiki |
| Hasil ekspor sesuai dengan sumber draw.io terkini | Menunggu pemeriksaan ulang |
| Berkas sumber dapat dibuka kembali | Belum diuji |

## 4. Hasil Review Pemeriksa

**Pemeriksa:** [nama rekan/asisten]

**Temuan:** Terdapat tiga temuan, yaitu ketidaksesuaian pesan pada cabang `[tidak tersedia]`, ekspor PNG tiga Activity Diagram LAB yang belum diperbarui, dan ekspor PNG Activity Diagram SIA tahap L4 yang belum sesuai dengan sumber terkini.

## 5. Perbaikan Setelah Review

| No. | Perbaikan | Artefak yang Diperbarui | Status |
|---|---|---|---|
| 1 | Mengubah aksi cabang `[tidak tersedia]` dengan pesan khusus | Activity Diagram Lihat Ketersediaan | [Belum/Selesai] |
| 2 | Mengekspor ulang diagram keputusan | PNG Activity Diagram Keputusan | [Belum/Selesai] |
| 3 | Mengekspor ulang diagram kelola data | PNG Activity Diagram Kelola Data | [Belum/Selesai] |
| 4 | Mengekspor ulang diagram peminjaman | PNG Activity Diagram Peminjaman | [Belum/Selesai] |
| 5 | Mengekspor ulang Activity Diagram SIA tahap L4 | `P06_2406011_SIA_activity_v01-L4.png` | [Belum/Selesai] |

**Versi setelah perbaikan:** [Isi versi aktual jika ada perubahan versi sumber.]

## 6. Hasil Uji Buka Ulang Sumber

| Berkas | Hasil Pengujian |
|---|---|
| Sumber draw.io diagram keputusan | [Hasil sebenarnya] |
| Sumber draw.io diagram kelola data | [Hasil sebenarnya] |
| Sumber draw.io diagram peminjaman | [Hasil sebenarnya] |
| Sumber draw.io SIA tahap L4 | [Hasil sebenarnya] |

**Kesesuaian ekspor PNG:** [Isi hasil perbandingan setiap PNG dengan sumber draw.io terkini.]

**Status akhir:** [Belum selesai/Selesai setelah seluruh perbaikan dan pengujian dilakukan.]