---
layout: post
title: komputasi interaktif
date: 2026-01-01 05:35:00+0700
description: komputasi interaktif sagemath
tags: formatting links
categories: sample-posts
---

<script src="https://sagemath.org"></script>
<script>
$(function () {
    // Membuat semua elemen dengan kelas 'sage' menjadi interaktif
    sagecell.makeSagecell({inputLocation: 'div.sage', evalButtonText: 'Hitung'});
});
</script>

<h3>1. Contoh Aljabar Linier Interaktif</h3>
<p>Anda bisa mengubah matriks di bawah ini dan menekan tombol "Hitung".</p>

<div class="sage">
  <script type="text/x-sage">
A = matrix([[1, 2], [3, 4]])
print("Matriks A:")
show(A)
print("Invers dari Matriks A:")
show(A.inverse())
  </script>
</div>

<h3>2. Contoh Visualisasi Grafik 3D</h3>
<p>Grafik di bawah ini bisa diputar secara interaktif oleh pengunjung.</p>

<div class="sage">
  <script type="text/x-sage">
var('x,y')
plot3d(sin(x^2 + y^2), (x, -2, 2), (y, -2, 2))
  </script>
</div>
