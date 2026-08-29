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

```bash
wsl -d Ubuntu
cd ~
mkdir -p src/modul-08
cd ~/src/modul-08

uv venv --python 3.14.4
source .venv/bin/activate

python --version
