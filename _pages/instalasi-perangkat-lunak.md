---
layout: page
permalink: /instalasi-perangkat-lunak.html
title: instalasi perangkat lunak
description: langkah-langkah instalasi
---

# dReal

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
  "postCreateCommand": "sudo apt-get update && sudo apt-get install -y curl pip && git clone https://github.com/dreal/dreal4 && cd dreal4 && sudo ./setup/ubuntu/`lsb_release -r -s`/install_prereqs.sh && cd .. && pip install dreal --upgrade && curl -fsSL https://raw.githubusercontent.com/dreal/dreal4/master/setup/ubuntu/22.04/install.sh | sudo bash"
}
```

Jalankan `python3` di terminal dan tulis program berikut

```
from dreal import *

x = Variable("x")
y = Variable("y")
z = Variable("z")

f_sat = And(0 <= x, x <= 10,
            0 <= y, y <= 10,
            0 <= z, z <= 10,
            sin(x) + cos(y) == z)

result = CheckSatisfiability(f_sat, 0.001)
print(result)
```

## Google Colab

Berdasarkan [tautan](https://github.com/dreal/dreal4), lakukan perintah berikut

```
!sudo apt-get install curl
!curl -fsSL https://raw.githubusercontent.com/dreal/dreal4/master/setup/ubuntu/22.04/install.sh | sudo bash
```

Instal alat kompilasi

```
!apt-get install -y build-essential cmake pkg-config
```

Konfigurasi direktori dReal

```
import os

os.environ["PKG_CONFIG_PATH"] = (
    "/opt/dreal/4.21.06.2/lib/pkgconfig:"
    "/opt/libibex/2.7.4/share/pkgconfig:"
    + os.environ.get("PKG_CONFIG_PATH", "")
)

!pkg-config dreal --modversion
!pkg-config dreal --cflags --libs
```

Jika `pkg-config` berhasil menemukan dReal, kita dapat melanjutkan.

Unduh contoh resmi dan kompilasi

```
!git clone https://github.com/dreal/dreal-cmake-example-project.git
!cmake -S dreal-cmake-example-project -B dreal-cmake-example-project/build
!cmake --build dreal-cmake-example-project/build
```

Jalankan program

```
!./dreal-cmake-example-project/build/check_sat
```

# GitHub

## Google Colab

Google Colab dapat digunakan untuk menjalankan berbagai operasi Git seperti `clone`, `commit`, `push`, dan lainnya. Karena notebook Colab berjalan di atas lingkungan sistem operasi Linux (Ubuntu), Anda bisa menjalankan perintah Git langsung dengan menambahkan tanda seru (`!`) di awal perintah.

Kloning repositori (`git clone`)

```
!git clone https://github.com/nama-pengguna/nama-repo.git
```

Navigasi ke Direktori Repositori. Gunakan perintah `%cd` (magic command) agar Colab tetap berada di direktori tersebut untuk perintah selanjutnya:

```
%cd nama-repo
```

Mengecek Status dan Histori (`git status` & `git log`)

```
!git status
!git log --oneline
```

Konfigurasi Identitas Pengguna. Sebelum melakukan _commit_, Anda perlu mengatur nama dan email:

```
!git config --global user.name "Nama Anda"
!git config --global user.email "email@example.com"
```

Melakukan Commit dan Push Perubahan

```
!git add .
!git commit -m "Pesan commit Anda"
!git push origin main
```

Hal Penting Terkait Otentikasi (`git push`). Karena Colab tidak menyimpan sesi login secara permanen, Anda memerlukan _Personal Access Token_ (PAT) atau SSH key dari GitHub/GitLab untuk melakukan _push_. Cara termudah adalah memasukkan token langsung pada URL repositori saat _clone_ atau saat mengubah _remote URL_:

```
!git remote set-url origin https://<TOKEN_ANDA>@github.com/nama-pengguna/nama-repo.git
!git push origin main
```

## Token

Untuk repositori milik akun Bapak sendiri, gunakan **fine-grained personal access token**:
<ol>
<li>Klik avatar, kemudian pilih settings. Setelah itu pilih Credentials.</li>
<li>Pilih <b>Generate new token</b>.</li>
<li>Isi nama, misalnya `Colab-LaTeX`.</li>
<li>Tentukan masa berlaku token.</li>
<li>Pada <b>Resource owner</b>, pilih pemilik repositori.</li>
<li>Pada <b>Repository access</b>, pilih <b>Only select repositories</b>, kemudian pilih repositori LaTeX.</li>
<li>Pada <b>Repository permissions</b>, atur <b>Contents -- Read-only</b>.</li>
<li>Buat token dan salin nilainya.</li>
</ol>

Token dapat digunakan untuk mengakses repositori privat dengan perintah berikut:

```
!git clone https://USERNAME:TOKEN_GITHUB@github.com/PEMILIK/NAMA_REPOSITORI.git
```

# GitLab

## Token

Untuk contoh ini, gunakan PAT dengan scope read_repository:
<ol>
<li>Login ke GitLab.</li>
<li>Klik avatar -- <b>Edit profile</b>.</li>
<li>Pilih <b>Access -- Personal access tokens</b>.</li>
<li>Pada tampilan yang menyediakan pilihan jenis token, pilih <b>Generate token -- Legacy token</b>.</li>
<li>Beri nama, misalnya `Colab-LaTeX`.</li>
<li>Tentukan tanggal kedaluwarsa.</li>
<li>Centang `read_repository`.</li>
<li>Buat token dan segera salin nilainya.</li>
</ol>

Token dapat digunakan untuk mengakses repositori privat dengan perintah berikut:

```
!git clone https://USERNAME:TOKEN_GITLAB@gitlab.com/PEMILIK/NAMA_REPOSITORI.git
```

# LaTeX

## Google Colab

Google Colab dapat digunakan untuk mengompilasi dan menjalankan berkas LaTeX. Karena lingkungan Colab berbasis Linux (Ubuntu), Anda bisa menginstal distribusi LaTeX seperti `texlive` dan kompiler `pdflatex` atau `xelatex` untuk menghasilkan dokumen PDF langsung dari sel notebook.

Instal Kompiler TeXLive (_Perlu waktu sekitar 1-2 menit untuk diunduh_). Daftar paket dasar TeX Live dan latexmk dapat diinstal menggunakan perintah apt-get:

```
!apt-get update -qq
!apt-get install -y texlive-latex-base texlive-latex-extra texlive-fonts-recommended latexmk
```

Buat Berkas .tex Menggunakan Cell Magic. Gunakan perintah `%%writefile` di awal sel untuk membuat berkas dokumen LaTeX (misalnya `document.tex`):

```
%%writefile document.tex
\documentclass{article}
\usepackage[utf8]{utf8}
\usepackage{amsmath}

\title{Contoh Dokumen LaTeX di Colab}
\author{Nama Penulis}
\date{\today}

\begin{document}

\maketitle

\section{Pendahuluan}
Ini adalah contoh dokumen \LaTeX{} yang dikompilasi menggunakan Google Colab.

\section{Formulasi Matematika}
Persamaan matematika dapat ditulis dengan mudah:
\begin{equation}
E = mc^2
\end{equation}

\end{document}
```

Kompilasi Berkas LaTeX menjadi PDF. Jalankan kompiler `pdflatex` untuk memproses berkas `.tex` menjadi file `.pdf`:

```
!pdflatex -interaction=nonstopmode document.tex
```

Unduh Hasil PDF:

```
from google.colab import files
files.download('document.pdf')
```

Tips Tambahan

- Mendukung Paket Lengkap: Jika dokumen Anda membutuhkan banyak paket khusus, Anda bisa menginstal paket penuh dengan `!apt-get install -y texlive-full` (membutuhkan waktu unduh lebih lama dan ruang penyimpanan sekitar 4 GB).
- Integrasi dengan Google Drive: Simpan berkas `.tex` di Google Drive agar tidak hilang saat sesi runtime Colab berakhir.

Apabila file latex berada di repositori GitHub publik, maka pertama instal latex dan kloning repositori. Kemudian navigasi ke direktori repositori.

```
!apt-get update -qq
!apt-get install -y texlive-latex-base texlive-latex-extra texlive-fonts-recommended latexmk
!git clone https://github.com/nama-pengguna/nama-repo.git
%cd nama-repo
```

Untuk menghasilkan file PDF, pertama `pull` dari repositori kemudian kompilasi file latex dan unduh hasilnya:

```
!git pull origin main
!pdflatex -interaction=nonstopmode document.tex
from google.colab import files
files.download('document.pdf')
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
