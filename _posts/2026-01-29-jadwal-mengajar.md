---
layout: post
title: jadwal mengajar
date: 2026-01-29 05:08:00-0700
description: jadwal mengajar pada setiap semester
tags: formatting tables
categories: sample-posts
giscus_comments: true
related_posts: true
pretty_table: true
---

## Semester Genap 2025/2026

### Nashrul Millah

| Jam   | Waktu   | Senin             | Selasa              | Rabu   | Kamis              | Jum'at             |
| :---: | :-----: | :---------------: | :-----------------: | :----: | :----------------: | :----------------: |
| 1     | 07.00   | PD Numerik (A)    |                     |        |                    |                    |
| 2     | 08.00   | LKMAT 5           |                     |        |                    |                    |
| 3     | 09.00   | Kalk. Prakt. (A1) |                     |        |                    |                    |
| 4     | 10.00   | LKMAT 5           |                     |        |                    |                    |
| 5     | 11.00   |                   |                     |        | PDP (A2)           |                    |
| 6     | 12.00   |                   |                     |        | Ruang 323A         |                    |
| 7     | 13.00   | Kalkulus          |                     |        | Statistika II (A2) | Stat. Prakt. (A2A) |
| 8     | 14.00   | RK A1             |                     |        | Ruang 323A         | LKMAT 6            |
| 9     | 15.00   | GC-7.10b          | Kalkulus Lanj. (L1) |        |                    |                    |
| 10    | 16.00   |                   | GC-3.04             |        |                    |                    |
| 11    | 17.00   |                   |                     |        |                    |                    |

<p></p>

## HTML Example

It is also possible to use HTML to display tables. For example, the following HTML code will display a table with [Bootstrap Table](https://bootstrap-table.com/), loaded from a JSON file:

{% raw  %}

```html
<table id="table" data-toggle="table" data-url="{{ '/assets/json/table_data.json' | relative_url }}">
  <thead>
    <tr>
      <th data-field="id">ID</th>
      <th data-field="name">Item Name</th>
      <th data-field="price">Item Price</th>
    </tr>
  </thead>
</table>
```

{% endraw  %}

<table
  data-toggle="table"
  data-url="{{ '/assets/json/table_data.json' | relative_url }}">
  <thead>
    <tr>
      <th data-field="id">ID</th>
      <th data-field="name">Item Name</th>
      <th data-field="price">Item Price</th>
    </tr>
  </thead>
</table>

<p></p>

## More Complex Example

By using [Bootstrap Table](https://bootstrap-table.com/) it is possible to create pretty complex tables, with pagination, search, and more. For example, the following HTML code will display a table, loaded from a JSON file, with pagination, search, checkboxes, and header/content alignment. For more information, check the [documentation](https://examples.bootstrap-table.com/index.html).

{% raw  %}

```html
<table
  data-click-to-select="true"
  data-height="460"
  data-pagination="true"
  data-search="true"
  data-toggle="table"
  data-url="{{ '/assets/json/table_data.json' | relative_url }}"
>
  <thead>
    <tr>
      <th data-checkbox="true"></th>
      <th data-field="id" data-halign="left" data-align="center" data-sortable="true">ID</th>
      <th data-field="name" data-halign="center" data-align="right" data-sortable="true">Item Name</th>
      <th data-field="price" data-halign="right" data-align="left" data-sortable="true">Item Price</th>
    </tr>
  </thead>
</table>
```

{% endraw  %}

<table
  data-click-to-select="true"
  data-height="460"
  data-pagination="true"
  data-search="true"
  data-toggle="table"
  data-url="{{ '/assets/json/table_data.json' | relative_url }}">
  <thead>
    <tr>
      <th data-checkbox="true"></th>
      <th data-field="id" data-halign="left" data-align="center" data-sortable="true">ID</th>
      <th data-field="name" data-halign="center" data-align="right" data-sortable="true">Item Name</th>
      <th data-field="price" data-halign="right" data-align="left" data-sortable="true">Item Price</th>
    </tr>
  </thead>
</table>
