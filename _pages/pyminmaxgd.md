---
layout: page
permalink: /pyminmaxgd.html
title: pyminmaxgd
description: langkah-langkah instalasi
---

Berikut adalah langkah-langkah instalasi [`pyminmaxgd`](https://gitlab.univ-nantes.fr/dioids/python-toolbox) di `github codespace`.
```
git clone https://gitlab.univ-nantes.fr/dioids/python-toolbox.git
cd python-toolbox
git clone https://gitlab.univ-nantes.fr/dioids/libminmaxgd.git
cd libminmaxgd
git switch olivier
cd ..
sudo apt update
sudo apt upgrade
sudo apt install python-dev-is-python3 python3-matplotlib swig
make
python Scripts/initial_configuration.py
pip install matplotlib
```

Berikut adalah langkah-langkah instalasi [`pyminmaxgd`](https://gitlab.univ-nantes.fr/dioids/python-toolbox) di `google colab`.
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
