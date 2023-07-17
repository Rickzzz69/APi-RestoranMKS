# Dokumentasi API Restoran Makassar

## Table of Contents

- [Dokumentasi API Restoran Makassar](#dokumentasi-api-restoran-makassar)
  - [Table of Contents](#table-of-contents)
  - [Base URL](#base-url)
  - [Endpoints](#endpoints)
    - [Get List of Restaurant](#get-list-of-restaurant)
    - [Get Detail of Restaurant](#get-detail-of-restaurant)
    - [Search Restaurant](#search-restaurant)
    - [Add Review](#add-review)

## Base URL

Base URL untuk API Restoran Makassar adalah : `https://apirestoran.000webhostapp.com/`

## Endpoints

### Get List of Restaurant 
> Mendapatkan semua daftar restoran 

- **URL**: `https://apirestoran.000webhostapp.com/restoran.php`
- **Method**: `GET`
- **Header**: 
  - `key = API Key/Token Anda`
- **Response Sukses**:
```json
{
    "Status": {
        "Code": 200,
        "Description": "Request Valid"
    },
    "total_data": 36,
    "restoran": [
        {
            "id_resto": "1",
            "nama_resto": "Restoran Chawan",
            "deskripsi": "Restoran yang terletak di Makassar dengan berbagai menu yang beragam dengan cita rasa asli",
            "alamat": "Jl. Karunrung No.1-D, Sawerigading, Kec. Ujung Pandang, Kota Makassar, Sulawesi Selatan 90113",
            "lokasi_maps": "https://goo.gl/maps/SheEwu4ot3KEDPMA9",
            "no_telpon": "0411-329662",
            "jam_buka": " 8:30 - 21:00"
        },
        ...
        {
            "id_resto": "36",
            "nama_resto": "Rumah Makan BURATU (Bumbu Ratu)",
            "deskripsi": "Restoran yang terletak di Makassar dengan berbagai menu yang beragam dengan cita rasa asli",
            "alamat": "Jl. Perintis Kemerdekaan No.km, Tamalanrea, Makassar City, South Sulawesi 90245",
            "lokasi_maps": "https://goo.gl/maps/dyKBYLu7sgQdvor37",
            "no_telpon": "085240087234",
            "jam_buka": "09:00 - 22:00"
        }
    ]
}
```
- **Response Gagal**:
```json
{
    "Status": {
        "Code": 400,
        "Description": "API Key/Token Not Provided"
    }
}
``` 

### Get Detail of Restaurant 
> Mendapatkan detail restoran berdasarkan ID

- **URL**: `https://apirestoran.000webhostapp.com/restoran_detail.php`
- **Method**: `GET`
- **Header**: 
  - `key = API Key/Token Anda`
- **Parameter**: 
  - `id_resto = ID Restoran yang ingin di cari`
- **Response Sukses**:
```json
{
    "Status": {
        "Code": 200,
        "Description": "Request Valid"
    },
    "restoran": {
        "id_resto": "10",
        "nama_resto": "Restoran Bakso Sampe",
        "deskripsi": "Restoran yang terletak di Makassar dengan berbagai menu yang beragam dengan cita rasa asli",
        "alamat": "Jl. Perintis Kemerdekaan No.11, Tamalanrea, Makassar City, South Sulawesi 90245",
        "lokasi_maps": "https://goo.gl/maps/uBhtdDEu9Ny4SETy5",
        "no_telpon": "0411-318861",
        "jam_buka": "10:00 - 24:00",
        "review": [
            {
                "nama_pengguna": "Edho",
                "komentar": "Restoran yang bagus!",
                "rating": "4"
            },
            {
                "nama_pengguna": "abduk",
                "komentar": "Wah restorannya sangat jelek sekali",
                "rating": "1"
            }
        ],
        "menu": [
            {
                "nama_menu": "Ayam Goreng",
                "harga": "20000"
            },
            {
                "nama_menu": "Ayam Bakar",
                "harga": "25000"
            },
            {
                "nama_menu": "Es Kopi",
                "harga": "10000"
            }
        ]
    }
}
```
- **Response Gagal**:
```json
{
    "Status": {
        "Code": 400,
        "Description": "API Key/Token Not Provided"
    }
}
``` 

### Search Restaurant 
> Mencari restoran berdasarkan keyword yang dimasukkan

- **URL**: `https://apirestoran.000webhostapp.com/restoran_search.php`
- **Method**: `GET`
- **Header**: 
  - `key = API Key/Token Anda`
- **Parameter**: 
  - `search = keyword/Nama Restoran yang ingin di cari`
- **Response Sukses**:
```json
{
    "Status": {
        "Code": 200,
        "Description": "Request Valid"
    },
    "data_ditemukan": 1,
    "restoran": [
        {
            "id_resto": "15",
            "nama_resto": "Rumah Makan Padang Jaya",
            "deskripsi": "Restoran yang terletak di Makassar dengan berbagai menu yang beragam dengan cita rasa asli",
            "alamat": "Jl. Urip Sumoharjo No.178, Sinrijala, Kec. Panakkukang, Kota Makassar, Sulawesi Selatan 90231",
            "lokasi_maps": "https://goo.gl/maps/XZUwmzMKMHp2vr8YA",
            "no_telpon": "0411-452978",
            "jam_buka": "08:00 - 23:00",
            "review": [
                {
                    "nama_pengguna": "Mimin",
                    "komentar": "Saya suka suasana restoran ini.",
                    "rating": "3"
                }
            ],
            "menu": [
                {
                    "nama_menu": "Gulai Kepala Kakap",
                    "harga": "30000"
                },
                {
                    "nama_menu": "Lalapan",
                    "harga": "20000"
                },
                {
                    "nama_menu": "Teh Sereh",
                    "harga": "15000"
                }
            ]
        }
    ]
}
```
- **Response Gagal**:
```json
{
    "Status": {
        "Code": 400,
        "Description": "API Key/Token Not Provided"
    }
}
``` 


### Add Review
> Menambahkan Review pada restoran tertentu

- **URL**: `https://apirestoran.000webhostapp.com/restoran_review.php`
- **Method**: `POST`
- **Header**: 
  - `key = API Key/Token Anda`
- **Body/x-www-form-urlencoded**: 
  - `id_resto = ID restoran yang ingin di review`
  - `nama_pengguna = nama anda`
  - `komentar = komentar yang ingin anda masukkan`
  - `rating = raing restoran menurut anda`
- **Response Sukses**:
```json
{
    "Status": {
        "Code": 200,
        "Description": "1 Data Telah Berhasil ditambahkan"
    },
    "result": {
        "id_resto": "5",
        "nama_pengguna": "Lutfi",
        "komentar": "Wah restorannya sangat bagus, jadi pengen datang lagi hehe",
        "rating": "5"
    }
}
```
- **Response Gagal**:
```json
{
    "Status": {
        "Code": 400,
        "Description": "API Key/Token Not Provided"
    }
}
``` 
