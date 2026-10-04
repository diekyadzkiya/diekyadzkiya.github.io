---
layout: page
permalink: /instalasi-perangkat-lunak.html
title: instalasi perangkat lunak
description: langkah-langkah instalasi
---

# PyMinMaxGD

## GitHub Codespaces

Berikut adalah langkah-langkah instalasi [`PyMinMaxGD`](https://gitlab.univ-nantes.fr/dioids/python-toolbox) di `github codespace`. Langkah pertama adalah `clone` repositori PyMinMaxGD.

```
git clone https://gitlab.univ-nantes.fr/dioids/python-toolbox.git
```

Kemudian masuk ke folder utama dan lakukan `clone` repositori [`libminmaxgd`](https://gitlab.univ-nantes.fr/dioids/libminmaxgd). Setelah itu, gunakan branch `olivier`.

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

Berikut adalah langkah-langkah instalasi [`pyminmaxgd`](https://gitlab.univ-nantes.fr/dioids/python-toolbox) di `Google Colab`. Langkah pertama adalah `clone` repositori [`PyMinMaxGD`](https://gitlab.univ-nantes.fr/dioids/python-toolbox) dan [`libminmaxgd`](https://gitlab.univ-nantes.fr/dioids/libminmaxgd). Kemudian memindahkan hasil clone repositori `libminmaxgd` ke subfolder dari `python-toolbox`. Setelah itu, menggunakan branch `olivier` pada repositori `libminmaxgd`. Kemudian, install package yang dibutuhkan yaitu `python-dev-is-python3`, `python3-matplotlib` dan `swig`. Setelah itu, jalankan perintah `make` dari folder `python-toolbox`. Langkah terakhir adalah memasukkan folder `python-toolbox` ke `PATH`.

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
