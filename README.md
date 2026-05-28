# Dataset Sekolah Indonesia

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![API Status](https://img.shields.io/badge/api-live-green)](https://api.ibnuhabib.web.id/api/schools)
[![Records](https://img.shields.io/badge/records-547.019-orange)](sekolah-indonesia.csv)

Data seluruh sekolah di Indonesia dari Data Pokok Pendidikan (Dapodik) Kemendikbud, dilengkapi ranking Top 1000 LTMPT.

## Data

| File | Records | Size | Delimiter |
|------|---------|------|-----------|
| `sekolah-indonesia.csv` | 547.019 | ~39 MB | `;` (titik koma) |

## Kolom

| Kolom | Deskripsi | Contoh |
|-------|-----------|--------|
| `npsn` | Nomor Pokok Sekolah Nasional | `20253979` |
| `name` | Nama sekolah | `SMA NEGERI 1 SURADE` |
| `province` | Provinsi | `JAWA BARAT` |
| `city` | Kabupaten/Kota | `KAB. SUKABUMI` |
| `district` | Kecamatan | `SURADE` |
| `type` | Jenjang | `SMA`, `SMK`, `MA`, `SMP`, `SD` |
| `accreditation` | Akreditasi | `A`, `B`, `C` |
| `rank_national` | Ranking nasional LTMPT Top 1000 | `245` (kosong jika di luar 1000) |

## Contoh Data

```csv
npsn;name;province;city;district;type;accreditation;rank_national
20253979;SMA NEGERI 1 SURADE;JAWA BARAT;KAB. SUKABUMI;SURADE;SMA;A;
20202361;SMP NEGERI 2 SURADE;JAWA BARAT;KAB. SUKABUMI;SURADE;SMP;B;
```

## API

Gunakan [api-datasets-indonesia](https://github.com/prodhokter/api-datasets-indonesia) untuk akses REST API.

**Base URL:** `https://api.ibnuhabib.web.id`

```bash
# Cari sekolah (support compact search — "sman1" cocok "SMA NEGERI 1")
curl "https://api.ibnuhabib.web.id/api/schools?search=sman1&limit=5"

# Filter per provinsi + jenjang
curl "https://api.ibnuhabib.web.id/api/schools?province=jawa+barat&type=sma&limit=10"

# Detail via NPSN
curl "https://api.ibnuhabib.web.id/api/schools/20253979"

# Download CSV lengkap
curl -O "https://api.ibnuhabib.web.id/download/schools.csv"
```

**Parameter search:**

| Param | Deskripsi |
|-------|-----------|
| `search` | Nama sekolah atau NPSN |
| `province` | Provinsi (exact) |
| `city` | Kabupaten/kota (partial) |
| `type` | Jenjang: `SMA`, `SMK`, `MA`, `SMP`, `SD` |
| `page` | Halaman (default 1) |
| `limit` | Per halaman (max 500, default 50) |

## Dataset Terkait

- [api-datasets-indonesia](https://github.com/prodhokter/api-datasets-indonesia) — REST API
- [dataset-perguruan-tinggi-indonesia](https://github.com/prodhokter/dataset-perguruan-tinggi-indonesia)
- [dataset-program-studi-indonesia](https://github.com/prodhokter/dataset-program-studi-indonesia)
- [dataset-kbbi-indonesia](https://github.com/prodhokter/dataset-kbbi-indonesia)
- [dataset-wilayah-indonesia](https://github.com/prodhokter/dataset-wilayah-indonesia)

## Sumber

- Data Pokok Pendidikan (Dapodik), Kemendikbud
- Top 1000 Sekolah, LTMPT

## Lisensi

MIT — © 2025 [Ibnul Habib](https://github.com/prodhokter). Data bersumber dari institusi pemerintah Indonesia.
