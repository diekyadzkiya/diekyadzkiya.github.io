---
layout: page
permalink: /instalasi-perangkat-lunak.html
title: instalasi perangkat lunak
description: langkah-langkah instalasi
---

# dreal

## GitHub Codespaces

Di repositori GitHub Anda, buat folder bernama `.devcontainer`. Di dalam folder tersebut, buat berkas bernama `devcontainer.json`. Masukkan konfigurasi berikut:

```
{
  "name": "Ubuntu 22.04 Environment",
  "image": "mcr.microsoft.com/devcontainers/base:ubuntu-22.04",
  "remoteUser": "vscode",
  "features": {
    "ghcr.io/devcontainers/features/common-utils:1": {
      "configureZshAsDefaultShell": true
    }
  },
  "postCreateCommand": "sudo apt-get update && sudo apt-get install -y curl && curl -fsSL https://raw.githubusercontent.com/dreal/dreal4/master/setup/ubuntu/22.04/install.sh | sudo bash"
}
```

Ujicoba instalasi:

```
/opt/dreal/4.21.06.2/bin/dreal
```

# PyMinMaxGD

## GitHub Codespaces

Berikut adalah langkah-langkah instalasi [`PyMinMaxGD`](https://gitlab.univ-nantes.fr/dioids/python-toolbox) di GitHub Codespaces. Langkah pertama adalah clone repositori [`PyMinMaxGD`](https://gitlab.univ-nantes.fr/dioids/python-toolbox).

```
git clone https://gitlab.univ-nantes.fr/dioids/python-toolbox.git
```

Kemudian masuk ke folder utama dan lakukan clone repositori [`libminmaxgd`](https://gitlab.univ-nantes.fr/dioids/libminmaxgd). Setelah itu, gunakan branch `olivier`.

```
cd python-toolbox
git clone https://gitlab.univ-nantes.fr/dioids/libminmaxgd.git
cd libminmaxgd
git switch olivier
cd ..
```

Install package yang dibutuhkan yaitu `python-dev-is-python3`, `python3-matplotlib` dan `swig`. Kemudian jalankan `make` dan `initial_configuration.py`. Setelah itu install package python `matplotlib`.

```
sudo apt update
sudo apt upgrade
sudo apt install python-dev-is-python3 python3-matplotlib swig
make
python Scripts/initial_configuration.py
pip install matplotlib
```

## Google Colab

Berikut adalah langkah-langkah instalasi [`PyMinMaxGD`](https://gitlab.univ-nantes.fr/dioids/python-toolbox) di Google Colab. Langkah pertama adalah clone repositori [`PyMinMaxGD`](https://gitlab.univ-nantes.fr/dioids/python-toolbox) dan [`libminmaxgd`](https://gitlab.univ-nantes.fr/dioids/libminmaxgd). Kemudian memindahkan hasil clone repositori [`libminmaxgd`](https://gitlab.univ-nantes.fr/dioids/libminmaxgd) ke subfolder dari `python-toolbox`. Setelah itu, menggunakan branch `olivier` pada repositori [`libminmaxgd`](https://gitlab.univ-nantes.fr/dioids/libminmaxgd). Kemudian, install package yang dibutuhkan yaitu `python-dev-is-python3`, `python3-matplotlib` dan `swig`. Setelah itu, jalankan perintah `make` dari folder `python-toolbox`. Langkah terakhir adalah memasukkan folder `python-toolbox` ke `PATH`.

```
!git clone https://gitlab.univ-nantes.fr/dioids/python-toolbox.git
!git clone https://gitlab.univ-nantes.fr/dioids/libminmaxgd.git
!mv /content/libminmaxgd/ /content/python-toolbox/
!git -C /content/python-toolbox/libminmaxgd switch olivier
!sudo apt install python-dev-is-python3 python3-matplotlib swig
!make -C /content/python-toolbox/
import sys
sys.path.append('/content/python-toolbox/')
```

# SageMath

## GitHub Codespaces

Di repositori GitHub Anda, buat folder bernama `.devcontainer`. Di dalam folder tersebut, buat berkas bernama `devcontainer.json`. Masukkan konfigurasi berikut:

```
{
  "name": "SageMath Environment",
  "image": "sagemath/sagemath:latest",
  "settings": {
    "terminal.integrated.shell.linux": "/bin/bash"
  },
  "customizations": {
    "vscode": {
      "extensions": [
        "ms-python.python",
        "ms-toolsai.jupyter"
      ]
    }
  }
}
```

Membuka antarmuka Jupyter Notebook di browser lokal Anda dengan kernel SageMath yang sudah terintegrasi secara otomatis:

```
sage -n jupyter
```

## Google Colab

Instal condacolab (_Persiapan lingkungan Conda di Colab_). Tulis dan jalankan kode berikut pada _cell_ pertama untuk mengunduh serta mengonfigurasi Conda ke dalam runtime Colab:

```
!pip install -q condacolab
import condacolab
condacolab.install()
```

**Catatan:** Setelah sel ini selesai dijalankan, runtime Colab akan otomatis melakukan _restart_ (ditandai dengan pesan _"Crash"_ atau _"Kernel restarted"_ di pojok kanan bawah). Ini adalah perilaku normal agar jalur sistem _(PATH)_ Conda aktif secara penuh.

Instal SageMath via Conda (_Mengunduh dan merakit dependensi SageMath_). Setelah runtime selesai _restart_, jalankan perintah instalasi SageMath melalui channel conda-forge di _cell_ baru:

```
!conda install -c conda-forge sage -y
```

_Proses ini biasanya memakan waktu sekitar 3–5 menit tergantung pada kecepatan koneksi server Colab._

Uji Coba Eksekusi Kode SageMath (_Memastikan SageMath terpasang dengan benar_). Setelah paket `sage` selesai terinstal, Anda dapat memanggil modul-modul SageMath atau mengeksekusi skrip Sage langsung dari antarmuka Python Colab:

```
import sage.all as sage

# Menggunakan simbolik variabel dari Sage
x = sage.var('x')

# Menyelesaikan persamaan simbolik
persamaan = sage.solve(x**2 + 5*x + 6 == 0, x)
print("Solusi:", persamaan)

# Menghitung faktor polinomial
print("Faktorisasi:", sage.factor(x**4 - 1))

# Operasi Matriks
M = sage.Matrix([[1, 2], [3, 4]])
print("Determinant:", M.det())
```
