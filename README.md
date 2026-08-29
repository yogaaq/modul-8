# Modul 8 - FastAPI dan SQLModel

**Mata Kuliah:** Praktikum Sistem Terdistribusi dan Terdesentralisasi  
**Universitas Teknologi Digital Indonesia**

---

## Tujuan Praktikum

Praktikum Modul 8 bertujuan untuk mempelajari pembuatan **RESTful API** menggunakan **FastAPI** dan **SQLModel**.

Pada praktikum ini dilakukan pembuatan database SQLite, pembuatan tabel produk, pengisian data produk, pembuatan endpoint API, serta pengujian API menggunakan `curl` dan browser.

---

## 1. Persiapan Environment

Praktikum dilakukan menggunakan **WSL Ubuntu**.

Virtual environment dibuat menggunakan `uv` dengan Python 3.14.4.

```bash
cd ~
mkdir -p src/modul-08
cd ~/src/modul-08
uv venv --python 3.14.4
source .venv/bin/activate
