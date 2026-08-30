# Modul 8 - FastAPI dan SQLModel

**Mata Kuliah:** Praktikum Sistem Terdistribusi dan Terdesentralisasi  
**Universitas Teknologi Digital Indonesia**

---

## Tujuan Praktikum

Praktikum Modul 8 bertujuan untuk mempelajari pembuatan **RESTful API** menggunakan **FastAPI** dan **SQLModel** yang terhubung dengan database SQLite.

Pada praktikum ini dilakukan proses pembuatan database, tabel produk, pengisian data, pembuatan API, menjalankan server, serta melakukan pengujian API menggunakan `curl` dan browser.

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

Virtual environment dibuat menggunakan Python 3.14.4.

```bash
uv venv --python 3.14.4
source .venv/bin/activate
```

Kemudian dilakukan pengecekan versi Python:

```bash
python --version
```

Hasil:

```text
Python 3.14.4
```

### Dokumentasi

![Persiapan Environment](ss/virtual-environment.png)

---

## 2. Instalasi Library

Library yang digunakan dalam praktikum adalah **FastAPI**, **SQLModel**, dan **Uvicorn**.

### Instalasi FastAPI dan SQLModel

```bash
uv pip install fastapi sqlmodel
```

Untuk melihat library yang telah terinstal:

```bash
uv pip list
```

### Instalasi Uvicorn

Uvicorn digunakan sebagai server untuk menjalankan aplikasi FastAPI.

```bash
uv pip install uvicorn
```

Kemudian dilakukan pengecekan versi Uvicorn:

```bash
uvicorn --version
```

Hasil:

```text
Running uvicorn 0.52.4 with CPython 3.14.4 on Linux
```

### Dokumentasi

![Instalasi FastAPI dan SQLModel](ss/install-fastapi-sqlmodel.png)

---

## 3. Membuat Database dan Model

Pada tahap ini dibuat beberapa file yang digunakan dalam aplikasi:

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

Database yang digunakan adalah:

```text
database.db
```

### Model Produk

File `models.py` digunakan untuk membuat model `Produk` menggunakan SQLModel.

Tabel `produk` memiliki beberapa kolom sebagai berikut:

| Kolom | Keterangan |
|---|---|
| `id` | ID produk |
| `kode` | Kode produk |
| `nama` | Nama produk |
| `tersedia` | Status ketersediaan produk |
| `harga` | Harga produk |

### Membuat Database dan Tabel

Database dan tabel dibuat menggunakan perintah:

```bash
python init_db.py
```

Jika berhasil, terminal menampilkan:

```text
Database dan tabel berhasil dibuat.
```

### Dokumentasi

![Pembuatan Database](ss/init-database.png)

---

## 4. Menambahkan Data Produk

Setelah database dan tabel berhasil dibuat, data produk dimasukkan menggunakan file `seed.py`.

Perintah yang digunakan:

```bash
python seed.py
```

Sebanyak **5 data produk** berhasil ditambahkan ke dalam database.

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

### Dokumentasi

![Penambahan Data Produk](ss/seed-data.png)

---

## 5. Menjalankan FastAPI

Setelah database dan data produk selesai dibuat, aplikasi FastAPI dijalankan menggunakan **Uvicorn**.

Perintah yang digunakan:

```bash
uvicorn main:app --reload
```

Jika berhasil, terminal menampilkan informasi bahwa server sedang berjalan:

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

### Dokumentasi

![FastAPI Server](ss/fastapi-server.png)

---

## 6. Pengujian API dengan curl

Setelah server FastAPI berjalan, API diuji menggunakan `curl`.

Endpoint yang digunakan adalah:

```text
/produk/
```

Perintah pengujian:

```bash
curl http://127.0.0.1:8000/produk/
```

Hasil pengujian menunjukkan bahwa API berhasil mengambil data produk dari database dan mengembalikannya dalam format **JSON**.

Data yang ditampilkan terdiri dari lima produk:

```text
P001 - Laptop
P002 - Mouse
P003 - Keyboard
P004 - Monitor
P005 - Headset
```

### Dokumentasi

![Pengujian API dengan curl](ss/curl-produk.png)

---

## 7. Hasil API pada Browser

Selain menggunakan `curl`, endpoint API juga dapat diakses melalui browser.

Buka alamat berikut:

```text
http://127.0.0.1:8000/produk/
```

Browser akan menampilkan data produk yang tersimpan di database dalam format **JSON**.

Dengan demikian, hasil API dapat dilihat secara langsung melalui browser.

### Dokumentasi

![Hasil API pada Browser](ss/browser-produk.png)

---

## 8. Pembahasan

Pada praktikum Modul 8 telah dilakukan pembuatan **RESTful API menggunakan FastAPI dan SQLModel** dengan database SQLite.

Praktikum dimulai dengan menyiapkan environment menggunakan **WSL Ubuntu** dan membuat virtual environment menggunakan `uv`. Setelah environment siap, library **FastAPI**, **SQLModel**, dan **Uvicorn** diinstal untuk mendukung proses pembuatan dan menjalankan API.

Selanjutnya dibuat database SQLite menggunakan `database.py` serta model `Produk` menggunakan SQLModel. Model tersebut digunakan untuk menentukan struktur tabel produk yang terdiri dari `id`, `kode`, `nama`, `tersedia`, dan `harga`.

Setelah tabel berhasil dibuat menggunakan `init_db.py`, dilakukan proses seeding menggunakan `seed.py`. Pada tahap ini berhasil ditambahkan **5 data produk** ke dalam database, yaitu Laptop, Mouse, Keyboard, Monitor, dan Headset.

Aplikasi kemudian dijalankan menggunakan Uvicorn dengan perintah:

```bash
uvicorn main:app --reload
```

Setelah server berjalan, endpoint `/produk/` digunakan untuk mengambil data produk dari database.

Pengujian dilakukan menggunakan `curl`:

```bash
curl http://127.0.0.1:8000/produk/
```

Hasil pengujian menunjukkan bahwa API berhasil mengembalikan data produk dalam format JSON. Endpoint yang sama juga dapat dibuka melalui browser sehingga data produk dapat dilihat secara langsung.

Dari praktikum ini dapat dipahami bahwa **FastAPI digunakan sebagai framework untuk membuat RESTful API**, sedangkan **SQLModel digunakan untuk membuat model dan berinteraksi dengan database SQLite**. **Uvicorn** digunakan sebagai server untuk menjalankan aplikasi FastAPI.

---

## 9. Kesimpulan

Praktikum Modul 8 berhasil dilakukan dengan menggunakan **Python, FastAPI, SQLModel, SQLite, dan Uvicorn**.

Database dan tabel `produk` berhasil dibuat, kemudian **5 data produk** berhasil dimasukkan ke dalam database.

Aplikasi FastAPI berhasil dijalankan menggunakan Uvicorn. Endpoint `/produk/` berhasil mengambil data dari database dan mengembalikannya dalam format JSON.

API berhasil diuji menggunakan `curl` dan hasilnya juga berhasil ditampilkan melalui browser.

Dengan demikian, praktikum ini memberikan pemahaman dasar mengenai **pembuatan RESTful API menggunakan FastAPI, penggunaan SQLModel untuk pengelolaan database, serta pengujian API menggunakan curl dan browser**.

---

## Struktur Folder

Struktur folder akhir Modul 8 adalah:

```text
modul-08/
├── .gitignore
├── .venv/
├── ss/
│   ├── virtual-environment.png
│   ├── install-fastapi-sqlmodel.png
│   ├── init-database.png
│   ├── seed-data.png
│   ├── fastapi-server.png
│   ├── curl-produk.png
│   └── browser-produk.png
├── database.db
├── database.py
├── init_db.py
├── main.py
├── models.py
├── seed.py
└── README.md
```

> Folder `.venv/` tidak di-upload ke GitHub karena sudah dimasukkan ke `.gitignore`.

---

## Teknologi yang Digunakan

- **Python 3.14.4**
- **FastAPI 0.141.1**
- **SQLModel 0.0.42**
- **SQLAlchemy 2.0.52**
- **Uvicorn 0.52.4**
- **SQLite**
- **WSL Ubuntu**
- **uv**
