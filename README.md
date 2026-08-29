# Modul 8 - FastAPI dan SQLModel

**Mata Kuliah:** Praktikum Sistem Terdistribusi dan Terdesentralisasi  
**Universitas Teknologi Digital Indonesia**

---

## Tujuan Praktikum

Praktikum Modul 8 bertujuan untuk mempelajari pembuatan **RESTful API** menggunakan **FastAPI** dan **SQLModel** yang terhubung dengan database SQLite.

Pada praktikum ini dilakukan proses pembuatan database, tabel produk, pengisian data, pembuatan API, serta pengujian API menggunakan `curl` dan browser.

---

## 1. Persiapan Environment

Praktikum dilakukan menggunakan **WSL Ubuntu** dengan virtual environment yang dibuat menggunakan `uv`.

### Membuat Folder Praktikum

```bash
wsl -d Ubuntu
cd ~
mkdir -p src/modul-08
cd ~/src/modul-08
```

### Membuat Virtual Environment

```bash
uv venv --python 3.14.4
source .venv/bin/activate
```

Kemudian mengecek versi Python:

```bash
python --version
```

Hasil:

```text
Python 3.14.4
```

---

## 2. Instalasi Library

Library yang digunakan dalam praktikum adalah **FastAPI**, **SQLModel**, dan **Uvicorn**.

### Instalasi FastAPI dan SQLModel

```bash
uv pip install fastapi sqlmodel
```

Untuk melihat library yang sudah terinstal:

```bash
uv pip list
```

### Instalasi Uvicorn

Uvicorn digunakan sebagai server untuk menjalankan aplikasi FastAPI.

```bash
uv pip install uvicorn
```

Kemudian versi Uvicorn dapat diperiksa dengan:

```bash
uvicorn --version
```

Hasil:

```text
Running uvicorn 0.52.4 with CPython 3.14.4 on Linux
```

---

## 3. Membuat Database dan Model

Pada tahap ini dibuat beberapa file untuk aplikasi:

```text
modul-08/
├── database.py
├── models.py
├── init_db.py
├── seed.py
├── main.py
└── database.db
```

### Database

File `database.py` digunakan untuk mengatur koneksi aplikasi dengan database SQLite.

Database yang digunakan bernama:

```text
database.db
```

### Model Produk

File `models.py` digunakan untuk membuat model `Produk` menggunakan SQLModel.

Struktur tabel `produk` terdiri dari:

| Kolom | Keterangan |
|---|---|
| `id` | ID produk |
| `kode` | Kode produk |
| `nama` | Nama produk |
| `tersedia` | Status ketersediaan produk |
| `harga` | Harga produk |

### Membuat Database dan Tabel

Proses pembuatan database dan tabel dilakukan menggunakan:

```bash
python init_db.py
```

Jika berhasil, terminal menampilkan:

```text
Database dan tabel berhasil dibuat.
```

---

## 4. Menambahkan Data Produk

Setelah tabel berhasil dibuat, data produk dimasukkan menggunakan file `seed.py`.

Perintah yang digunakan:

```bash
python seed.py
```

Sebanyak **5 data produk** berhasil ditambahkan ke database.

| Kode | Nama | Harga | Tersedia |
|---|---|---:|---|
| P001 | Laptop | Rp7.500.000 | Ya |
| P002 | Mouse | Rp150.000 | Ya |
| P003 | Keyboard | Rp350.000 | Ya |
| P004 | Monitor | Rp2.500.000 | Tidak |
| P005 | Headset | Rp450.000 | Ya |

Hasil proses:

```text
5 data produk berhasil ditambahkan.
```

---

## 5. Menjalankan FastAPI

Setelah database dan data produk selesai dibuat, aplikasi FastAPI dijalankan menggunakan Uvicorn.

Perintah yang digunakan:

```bash
uvicorn main:app --reload
```

Jika berhasil, terminal menampilkan:

```text
INFO:     Uvicorn running on http://127.0.0.1:8000
INFO:     Started reloader process
INFO:     Started server process
INFO:     Waiting for application startup.
INFO:     Application startup complete.
```

Server FastAPI berjalan pada:

```text
http://127.0.0.1:8000
```

---

## 6. Pengujian API

API diuji menggunakan endpoint:

```text
/produk/
```

Pengujian dilakukan menggunakan `curl`:

```bash
curl http://127.0.0.1:8000/produk/
```

Hasil pengujian menunjukkan bahwa API berhasil mengambil data dari database dan mengembalikannya dalam format JSON.

Contoh hasil:

```json
[
  {
    "kode": "P001",
    "nama": "Laptop",
    "harga": 7500000.0,
    "tersedia": true,
    "id": 1
  },
  {
    "kode": "P002",
    "nama": "Mouse",
    "harga": 150000.0,
    "tersedia": true,
    "id": 2
  },
  {
    "kode": "P003",
    "nama": "Keyboard",
    "harga": 350000.0,
    "tersedia": true,
    "id": 3
  },
  {
    "kode": "P004",
    "nama": "Monitor",
    "harga": 2500000.0,
    "tersedia": false,
    "id": 4
  },
  {
    "kode": "P005",
    "nama": "Headset",
    "harga": 450000.0,
    "tersedia": true,
    "id": 5
  }
]
```

---

## 7. Hasil pada Browser

Endpoint API juga dapat diuji melalui browser dengan membuka:

```text
http://127.0.0.1:8000/produk/
```

Browser akan menampilkan data produk yang tersimpan di database dalam format JSON.

### Dokumentasi Hasil Praktikum

#### 1. Persiapan Environment

![Persiapan Environment](ss/01-virtual-environment.png)

#### 2. Instalasi FastAPI dan SQLModel

![Instalasi Library](ss/02-install-fastapi-sqlmodel.png)

#### 3. Pembuatan Database

![Pembuatan Database](ss/03-init-database.png)

#### 4. Penambahan Data Produk

![Seed Data](ss/04-seed-data.png)

#### 5. Menjalankan Uvicorn

![Uvicorn](ss/05-uvicorn.png)

#### 6. FastAPI Berjalan

![FastAPI Server](ss/06-fastapi-server.png)

#### 7. Pengujian API dengan curl

![Curl API](ss/07-curl-produk.png)

#### 8. Hasil API pada Browser

![API Browser](ss/08-browser-produk.png)

> Nama file screenshot dapat disesuaikan dengan nama file screenshot yang kamu masukkan ke repository GitHub.

---

## 8. Pembahasan

Pada praktikum Modul 8 telah dilakukan pembuatan **RESTful API menggunakan FastAPI dan SQLModel** dengan database SQLite.

Praktikum dimulai dengan menyiapkan environment menggunakan WSL Ubuntu dan membuat virtual environment menggunakan `uv`. Setelah environment siap, library FastAPI, SQLModel, dan Uvicorn diinstal untuk mendukung proses pembuatan dan menjalankan API.

Selanjutnya dibuat database SQLite dan model `Produk` menggunakan SQLModel. Database tersebut digunakan untuk menyimpan informasi produk berupa kode, nama, harga, dan status ketersediaan.

Setelah tabel berhasil dibuat, dilakukan proses seeding menggunakan `seed.py`. Sebanyak lima data produk berhasil dimasukkan ke dalam database.

Aplikasi kemudian dijalankan menggunakan Uvicorn. Endpoint `/produk/` digunakan untuk mengambil data produk dari database. Pengujian menggunakan `curl` menunjukkan bahwa API berhasil mengembalikan data dalam format JSON.

Endpoint yang sama juga dapat dibuka melalui browser sehingga hasil data produk dapat dilihat secara langsung.

Dari praktikum ini dapat dipahami bahwa **FastAPI berperan sebagai framework untuk membuat API**, sedangkan **SQLModel digunakan untuk mendefinisikan model dan berinteraksi dengan database SQLite**.

---

## 9. Kesimpulan

Praktikum Modul 8 berhasil dilakukan dengan menggunakan **FastAPI, SQLModel, SQLite, Uvicorn, dan Python**.

Database dan tabel `produk` berhasil dibuat, kemudian lima data produk berhasil dimasukkan ke dalam database.

Aplikasi FastAPI berhasil dijalankan menggunakan Uvicorn dan endpoint `/produk/` berhasil mengambil data dari database. Hasil API juga berhasil diuji menggunakan `curl` dan ditampilkan melalui browser dalam format JSON.

Dengan demikian, praktikum ini memberikan pemahaman dasar mengenai pembuatan **RESTful API menggunakan FastAPI**, penggunaan **SQLModel untuk database**, serta proses pengujian API.
