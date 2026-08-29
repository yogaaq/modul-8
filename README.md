# Modul 8 - FastAPI dan SQLModel

**Mata Kuliah:** Praktikum Sistem Terdistribusi dan Terdesentralisasi  
**Universitas Teknologi Digital Indonesia**

---

## Tujuan Praktikum

Praktikum Modul 8 bertujuan untuk mempelajari pembuatan REST API sederhana menggunakan **FastAPI** dan **SQLModel**. Pada praktikum ini dibuat database SQLite, tabel produk, data awal produk, serta API untuk menampilkan data produk melalui browser.

---

## 1. Persiapan Environment

Praktikum dilakukan menggunakan WSL Ubuntu dengan Python 3.14.4.

Virtual environment dibuat menggunakan `uv`:

```bash
cd ~
mkdir -p src/modul-08
cd ~/src/modul-08
uv venv --python 3.14.4
source .venv/bin/activate
