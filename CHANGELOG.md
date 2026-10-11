# Changelog

## 2026-10-11 (revisi), Hostname publik dan internal dipisah

- README memakai `https://api.ibnuhabib.web.id` sebagai base URL publik.
- `https://datasets.snbtku.com` adalah hostname internal untuk aplikasi SNBTKU (layanan sama), tidak dipromosikan untuk umum.

## 2026-10-11, Dokumentasi diperbarui

- README ditulis ulang dengan fakta yang diverifikasi dari data: 547.019 baris, 51 jenis satuan pendidikan, `rank_national` hanya terisi 999 baris.
- Ditambahkan catatan kejujuran data: nama sekolah sering berupa singkatan (`SMAN 1 SURADE`), penulisan jenjang dan akreditasi tidak konsisten.
- Aturan pembersihan platform didokumentasikan (normalisasi huruf besar, BOM, `rank_national` kosong menjadi `NULL`).
- Contoh pemakaian API ditulis ulang mengikuti API terbaru, termasuk catatan bahwa mode compact search tidak tersedia lagi.
- Data `sekolah-indonesia.csv` tidak berubah.
