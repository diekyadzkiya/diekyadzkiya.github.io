---
layout: post
title: komputasi interaktif
date: 2026-01-05 05:35:00+0700
description: komputasi interaktif sagemath
tags: formatting links
categories: sample-posts
sagecell: true
---

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

### Cara Pembuatan

Pertama, tambahkan kode berikut ke dalam file `/_includes/head.liquid`
```
{% if page.sagecell %}
  <script src="https://sagecell.sagemath.org/static/embedded_sagecell.js"></script>
  <script>
    // Mengaktifkan elemen dengan class "sage" menjadi Sage Cell interaktif
    sagecell.makeSagecell({
      inputLocation: '.sage',
      languages: ['sage', 'python', 'r'], // Bahasa yang diizinkan (opsional)
      evalButtonText: 'Hitung / Jalankan', // Mengubah teks tombol eksekusi
      editor: 'textarea',
    });
  </script>
{% endif %}
```
kemudian gunakan logika kondisional Jekyll seperti di file ini (bukan website) dan tambahkan `sagecell: true` pada front-matter halaman Markdown. Meskipun editor `textarea` tidak memiliki banyak fitur, namun teks terlihat jelas pada mode gelap maupun terang.
