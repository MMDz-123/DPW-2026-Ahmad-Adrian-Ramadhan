# Laporan Jobsheet 2

Memberi *styling* dasar dengan CSS3. *Styling* masih hanya meliputi pemberian *font*, warna *background*, dan kartu statistik pada bagian yang ditandai dengan `<article>`

Sebelum memberi *styling*, semua file `.html` harus diberi satu baris yang merujuk pada file `style.css`. Baris tersebut diisi dengan:
```html
<link rel="stylesheet" href="assets/css/style.css">
```

## Reset
```css
*{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```
digunakan untuk menghilangkan jarak default yang otomatis diberikan brower. Banyak elemen memiliki margin bawaan yang berbeda-beda tergantung dari browser yang dipakai.

## Gaya dasar
```css
body{
    font-family:'Segoe UI', Arial, sans-serif;
    color:#002a1f;
    background-color: #d1d1d1;
    line-height: 1.5;
}
```
- `font-family` dan `color` mengurutkan font berdasarkan prioritas. Browser akan mencoba font yang ditulis pertama, jika tidak aka maka browser memakai font kedua, dan seterusnya. `color: #2b2b2b` menentukan warna teks.
- `background color` menentukan warna latar belakang. `#f5f6f8` abu-abu muda.
- `line-height` jarak antar baris, 1.5 kali besar font.

## Tautan
- semua tautan menggunakan warna `#1d5b8a`
- Tautan diberi garis bawah **hanya** saat kursor diarahkan (hover) dengan `a:hover {text-decoration: underline}`

## Header dan Navbar
### Flexbox
Secara default elemen di dalam HTML disusun bertumpuk ke bawah. Flexbox berperan sebagai sistem tata letak yang mengatur bagaimana elemen anak disusun. 
```css
header{
    display: flex;
}
```
Potongan tersebut mengubah `<header>` menjadi *flex container* dan semua keturunannya menjadi *flex items* dan disusun sejajar secara horizontal

Flexbox dapat digunakan dua kali secara bertingkat. Pada jobsheet ini *flexbox* digunakan di `<header>` dan `<nav> <ul>` untuk list menu

## Layout `main` dan `section`
### main
```css
main{
    max-width: 1000px;
    margin: 2rem auto;
    padding: 0 1.5rem;
}
```
- `max-width` lebar maksimal 1000 piksel sehingga konten tidak melebar secara tidak wajar sehingga dapat dibaca dengan nyaman meskipun menggunakan monitor berukuran besar.
- `margin: 2rem auto` margin vertikal sebesar `2rem` dan horizontal dibuat otomatis dengan membagi rata ruang kosong di kiri dan kanan sehingga konten berada di tengah
- `padding` jarak dari tepi layar secara horizontal sebesar `1.5rem` sehingga konten tidak terlalu mepet ke tepi layar

### section
Setiap section dibagi menjadi beberapa kotak yang terlihat seperti kartu
```css
section {
    background-color: #fff;
    border-radius: 8px;
    padding: 1.5rem;
    margin-bottom: 1.5rem;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.08);
}
```
pada bagian `box-shadow` kode warna tidak menggunakan kode *hexadecimal* tetapi menggunakan kode rgba. Mirip seperti *hexadecimal* tetapi dengan tambahan `a` yaitu *alpha* atau transparansi sehingga bayangan tidak terlihat hitam pekat

## Kartu Statistik
Selain *flexbox*, css grid adalah salah satu sistem layout untuk menyusun elemen css.

```css
main section:nth-of-type(2){
    display: grid;
    grid-template-columns:repeat(3, 1fr) ;
    gap: 1rem;
}

main section:nth-of-type(2) article{
    background-color: #eef4fa;
    border-radius: 8px;
    padding: 1.25rem;
    text-align: center;
}
main section:nth-of-type(2) article h3{
font-size: 1rem;
color: #293541;
margin-bottom: 0.5rem;
}

main section:nth-last-of-type(2) article p{
    font-size: 1.8rem;
    font-weight: 700;
    color: #1d5b8a;
}
```

- `nth-of-type(2)` memilih elemen dengan urutan ke-2 diantara semua elemen di `<section>`. Dengan `main` maka yang diambil adalah section kedua yang ada di dalam `main`
- `grid-template-columns: repeat(3, 1fr)` tiga kolom dengan lebar masing-masing 1fr (bagian pecahan dari ruang yang ada)

## Tabel
```css
table{
    width: 100%;
    border-collapse: collapse;
}

th, td{
    text-align: left;
    padding: 0.65rem 0.75rem;
    border-bottom: 1px solid #e2e6ee;
}

thead{
    background-color: #1d5b8a;
    color: #fff;
}

tbody tr:nth-child(even){
    background-color: #f7f9fb;
}

tbody tr:hover{
    background-color: #eef4fa;
}

td button{
    padding: 0.35rem 0.7rem;
    margin-right: 0.35rem;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-size: 0.85rem;
    font-size: 0.85rem
}

td button:first-of-type{
    background-color: #fce1bd;
    color: #1d5b8a;
}

td button:last-of-type{
    background-color: #d9534f;
    color: #fff;
}
```

### Lebar Tabel
- `width: 100%` tabel menempati seluruh kotak yang ditempati
- Secara default, garis pembatas tampak dua garis sejajar. `border-collapse: collapse` menggabungkan dua garis sejajar tersebut menjadi satu agar terlihat lebih rapi

### Sel Header dan Data
- Sel header dan data menggunakan aturan yang sama sehingga *selector* langsung digabung dengan koma
- Karena `<th>` secara default menerapkan teks rata tengah, `text-align: left;` digunakan untuk "memaksa" tabel menggunakan teks rata kiri 
- Setiap garis di bawah sel diberi garis abu muda dengan `border-bottom: 1px solid #e2e6ea;`

### Header tabel
- Kepala tabel diberi warna biru polinema `#1d5b8a` dengan teks bewarna putih

### Baris selang-seling dan Efek Saat Hover
- `tbody tr:nth-child(even)` merujuk pada baris genap saja dan diberi warna abu muda sehingga tabel terlihat seperti kulit zebra. Hal ini dapat membantu pengguna membaca tabel tanpa "tersasar" ke baris lain
- Ketika kursor diarahkan ke salah satu baris, warna latar belakang baris tersebut menjadi biru pudar sehingga pengguna dapat melihat baris mana yang sedang disorot