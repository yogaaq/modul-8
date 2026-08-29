# Modul 8 - FastAPI dan SQLModel

**Mata Kuliah:** Praktikum Sistem Terdistribusi dan Terdesentralisasi  
**Universitas Teknologi Digital Indonesia**

---

## Tujuan Praktikum

Praktikum Modul 8 bertujuan untuk mempelajari pembuatan **RESTful API** menggunakan **FastAPI** dan **SQLModel**.

Pada praktikum ini dilakukan beberapa tahapan, yaitu:

1. Menyiapkan environment Python menggunakan WSL Ubuntu.
2. Membuat virtual environment menggunakan `uv`.
3. Menginstal FastAPI dan SQLModel.
4. Membuat database SQLite.
5. Membuat model tabel produk menggunakan SQLModel.
6. Membuat tabel database.
7. Menambahkan data produk ke database.
8. Membuat REST API menggunakan FastAPI.
9. Menjalankan server menggunakan Uvicorn.
10. Melakukan pengujian API menggunakan `curl`.
11. Melihat hasil API melalui browser.

---

# 1. Persiapan Environment

Praktikum dilakukan menggunakan **WSL Ubuntu**.

Python yang digunakan pada Windows adalah Python 3.14.3, sedangkan pada environment WSL digunakan Python 3.14.4 melalui virtual environment.

### Mengecek Python pada Windows

```bash
python --version
