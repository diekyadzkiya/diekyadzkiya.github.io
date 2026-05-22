---
layout: post
title: komputasi interaktif
date: 2026-01-01 05:35:00+0700
description: komputasi interaktif sagemath
tags: formatting links
categories: sample-posts
html: true
---

Berikut adalah komputasi interaktif menggunakan SageMathCell:

<!-- Kotak Eksekusi Sage -->
<div class="sage">
  <script type="text/x-sage">
A = matrix([[1, 2], [3, 4]])
print("Matriks A:")
show(A)
  </script>
</div>

<!-- Letakkan skrip pemanggil di bagian paling bawah agar jQuery sudah termuat sempurna -->
<script src="https://sagemath.org"></script>
<script>
document.addEventListener("DOMContentLoaded", function() {
    if (typeof sagecell !== 'undefined') {
        sagecell.makeSagecell({inputLocation: 'div.sage', evalButtonText: 'Hitung'});
    }
});
</script>
