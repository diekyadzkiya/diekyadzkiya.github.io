---
layout: post
title: komputasi interaktif
date: 2026-01-05 05:35:00+0700
description: komputasi interaktif sagemath
tags: formatting links
categories: sample-posts
sagecell: true
---

<iframe src="https://sagecell.sagemath.org/&lang=sage" width="100%" height="400px" style="border:1px solid #ddd; border-radius:4px;"></iframe>

### Mencoba Plot Fungsi Matematika Interaktif

Silakan ubah fungsi di bawah ini lalu tekan tombol jalankan untuk melihat grafiknya secara real-time.

<div class="sage">
<script type="text/x-sage">
# Definisikan variabel dan fungsi
x = var('x')
f = sin(x) * cos(x^2)

# Tampilkan visualisasi grafik
plot(f, (x, -3, 3), color='purple', title='Grafik Sinus Interaktif')
</script>
</div>

### Alat Peraga Interaktif (Slider)

<div class="sage">
<script type="text/x-sage">
@interact
def _(n=(1, [1..20])):
    x = var('x')
    # Menampilkan plot polinomial Taylor untuk fungsi e^x
    p = plot(exp(x), (x, -3, 3), color='blue', legend_label='e^x')
    pt = plot(taylor(exp(x), x, 0, n), (x, -3, 3), color='red', legend_label=f'Taylor Orde {n}')
    (p + pt).show(ymin=-1, ymax=20)
</script>
</div>


