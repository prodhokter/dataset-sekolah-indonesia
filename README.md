# Dataset Sekolah Indonesia

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Records](https://img.shields.io/badge/records-547.019-orange)](sekolah-indonesia.csv)

Data seluruh satuan pendidikan di Indonesia dari Data Pokok Pendidikan (Dapodik) Kemendikbud, dilengkapi peringkat nasional Top 1000 LTMPT. Mencakup **51 jenis satuan pendidikan**, dari SD sampai lembaga kursus.

## Data

| File | Baris | Ukuran | Delimiter |
|------|-------|--------|-----------|
| `sekolah-indonesia.csv` | 547.019 | ~39 MB | `;` (titik koma) |

| Kolom | Deskripsi | Contoh |
|-------|-----------|--------|
| `npsn` | Nomor Pokok Sekolah Nasional (unik) | `20253979` |
| `name` | Nama sekolah | `SMAN 1 SURADE` |
| `province` | Provinsi (huruf besar) | `JAWA BARAT` |
| `city` | Kabupaten/kota (huruf besar, berawalan `KAB.` atau `KOTA`) | `KAB. SUKABUMI` |
| `district` | Kecamatan (huruf besar) | `SURADE` |
| `type` | Jenjang/satuan pendidikan (campuran huruf besar-kecil di sumber) | `SMA`, `sma`, `MTs`, `SMK` |
| `accreditation` | Akreditasi (campuran huruf besar-kecil) | `A`, `b`, `-` |
| `rank_national` | Peringkat nasional Top 1000 LTMPT, **hanya terisi 999 baris** | `245`, kosong untuk sisanya |

Sebaran jenjang terbesar: SD 149.476, TK 99.070, KB 83.202, SMP 43.500, RA 31.129, MI 26.884, SPS 19.782, MTS 18.828, SMA 14.756, SMK 14.453, KURSUS 12.292, PKBM 10.520.

Catatan kejujuran data:
- Banyak nama sekolah memakai singkatan, contoh `SMAN 1 SURADE`, bukan `SMA NEGERI 1 SURADE`. Pencarian berbasis teks harus memperhitungkan ini.
- Penulisan jenjang dan akreditasi tidak konsisten (`MTs` dan `MTS`, `b` dan `B`).
- `rank_national` kosong untuk 546.020 baris.

## Contoh data

```csv
npsn;name;province;city;district;type;accreditation;rank_national
20253979;SMAN 1 SURADE;JAWA BARAT;KAB. SUKABUMI;SURADE;SMA;A;
20316655;SMK NEGERI 1 KOTA BANDUNG;JAWA BARAT;KOTA BANDUNG;CIBEUNYING KALER;SMK;A;
```

## Aturan pembersihan (dipakai platform SNBTKU)

1. BOM di header dibuang, spasi ujung dirapikan.
2. `type` dan `accreditation` dinormalkan ke huruf besar (`MTs` menjadi `MTS`, `b` menjadi `B`).
3. `rank_national` kosong menjadi `NULL` (bukan string kosong).
4. `npsn` dipakai sebagai primary key; baris duplikat tidak ada.

## Cara pakai

### 1. Unduh langsung

```bash
curl -O https://raw.githubusercontent.com/prodhokter/dataset-sekolah-indonesia/master/sekolah-indonesia.csv
```

### 2. Lewat API publik (sudah bersih dan terindeks pencarian)

Base URL publik: `https://api.ibnuhabib.web.id`. Hostname internal untuk aplikasi SNBTKU (layanan sama): `https://datasets.snbtku.com`.

```bash
# Cari sekolah (q minimal 3 karakter, pencarian mengandung, tidak peka huruf besar-kecil)
curl "https://api.ibnuhabib.web.id/api/v1/schools/search?q=SURADE&limit=5"

# Filter jenjang SMA saja
curl "https://api.ibnuhabib.web.id/api/v1/schools/search?q=SMA%20NEGERI%201&type=SMA&limit=5"

# Detail satu sekolah lewat NPSN
curl "https://api.ibnuhabib.web.id/api/v1/schools/20253979"
```

Contoh respons nyata:

```json
// GET /api/v1/schools/20253979
{
  "school": {
    "npsn": "20253979",
    "name": "SMAN 1 SURADE",
    "province": "JAWA BARAT",
    "city": "KAB. SUKABUMI",
    "district": "SURADE",
    "type": "SMA",
    "accreditation": "A",
    "rank_national": null
  }
}
```

Catatan perilaku API: pencarian memakai pola mengandung dengan minimal 3 karakter, dan **tidak** menyediakan mode "compact search" yang mengabaikan spasi (misalnya `sman1`) seperti versi API lama. Gunakan kata kunci yang benar-benar ada, misalnya `SURADE` atau `SMAN 1`.

Rate limit 120 permintaan per menit per IP, CORS terbuka, respons di-cache 5 menit.

## Sumber & lisensi

- Sumber: Data Pokok Pendidikan (Dapodik), Kemendikbud, dan daftar Top 1000 LTMPT.
- Repo ini (kompilasi dan pembersihan): MIT, Copyright (c) 2025 Ibnul Habib.

## Changelog

Lihat [CHANGELOG.md](CHANGELOG.md).
