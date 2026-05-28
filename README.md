# Dataset Sekolah Indonesia

Data seluruh sekolah di Indonesia dari Data Pokok Pendidikan (Dapodik) Kemendikbud, dilengkapi ranking Top 1000 LTMPT.

## Data

**File:** `sekolah-indonesia.csv`  
**Records:** 547.019 sekolah  
**Size:** ~39 MB  
**Delimiter:** titik koma (`;`)

## Kolom

| Kolom | Deskripsi | Contoh |
|-------|-----------|--------|
| `npsn` | Nomor Pokok Sekolah Nasional | `20253979` |
| `name` | Nama sekolah | `SMA NEGERI 1 SURADE` |
| `province` | Provinsi | `JAWA BARAT` |
| `city` | Kabupaten/Kota | `KAB. SUKABUMI` |
| `district` | Kecamatan | `SURADE` |
| `type` | Jenjang pendidikan | `SMA`, `SMK`, `MA`, `SMP`, `SD` |
| `accreditation` | Akreditasi | `A`, `B`, `C` |
| `rank_national` | Ranking nasional (LTMPT Top 1000) | `245` (kosong jika di luar top 1000) |

## Contoh

```csv
npsn;name;province;city;district;type;accreditation;rank_national
20253979;SMA NEGERI 1 SURADE;JAWA BARAT;KAB. SUKABUMI;SURADE;SMA;A;
```

## API

Gunakan [api-datasets-indonesia](https://github.com/prodhokter/api-datasets-indonesia) untuk akses via REST API:

```
GET /api/schools?search=sman1&province=jawa+barat&type=sma&page=1&limit=50
GET /api/schools/:npsn
```

## Sumber

- Data Pokok Pendidikan (Dapodik), Kemendikbud
- Top 1000 Sekolah, LTMPT

## Lisensi

Data bersumber dari institusi pemerintah Indonesia. Gunakan sesuai ketentuan yang berlaku.
