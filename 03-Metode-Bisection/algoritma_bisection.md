# Algoritma Pencarian Akar Persamaan Nonlinear dengan Metode Bisection

## Tujuan

Mendekati akar persamaan nonlinear satu variabel `f(x) = 0` dengan mempertahankan interval yang mengapit akar. Metode ini mensyaratkan fungsi kontinu pada interval dan nilai fungsi di kedua ujung interval memiliki tanda berlawanan.

## Contoh kasus

\[
f(x)=x^3+2x-7
\]

Gunakan interval awal `a = 1` dan `b = 2`.

\[
f(1)=-4,\qquad f(2)=5
\]

Karena `f(a) × f(b) < 0`, terdapat setidaknya satu akar pada interval tersebut berdasarkan Teorema Nilai Antara.

## Rumus utama

Titik tengah setiap iterasi:

\[
c=\frac{a+b}{2}
\]

- Jika `f(a) × f(c) < 0`, akar berada pada `[a,c]`, sehingga `b = c`.
- Jika `f(c) × f(b) < 0`, akar berada pada `[c,b]`, sehingga `a = c`.
- Jika `f(c) = 0`, titik tengah adalah akar tepat.

## Contoh tiga iterasi pertama

- Iterasi 1: `c = (1 + 2)/2 = 1,5`; `f(1,5) = −0,625`. Perubahan tanda terdapat pada `[1,5; 2]`.
- Iterasi 2: `c = (1,5 + 2)/2 = 1,75`; `f(1,75) = 1,859375`. Interval yang dipertahankan menjadi `[1,5; 1,75]`.
- Iterasi 3: `c = (1,5 + 1,75)/2 = 1,625`; `f(1,625) = 0,541015625`. Interval yang dipertahankan menjadi `[1,5; 1,625]`.

Contoh tersebut memperlihatkan bahwa panjang interval menjadi setengah pada setiap iterasi.

## Langkah algoritma

1. Definisikan fungsi kontinu `f(x)`.
2. Masukkan batas bawah `a`, batas atas `b`, toleransi, dan batas iterasi maksimum.
3. Hitung `f(a)` dan `f(b)`.
4. Tolak interval apabila `f(a)` dan `f(b)` memiliki tanda yang sama, karena syarat pengurungan akar belum dipenuhi.
5. Hitung titik tengah `c = (a+b)/2`.
6. Hitung `f(c)` dan batas galat interval saat ini `(b-a)/2`.
7. Catat nomor iterasi, `a`, `b`, `c`, `f(c)`, dan batas galat ke tabel.
8. Hentikan apabila `|f(c)|` atau batas galat sudah tidak melebihi toleransi, atau batas iterasi tercapai.
9. Jika belum berhenti, pilih setengah interval yang mempertahankan perubahan tanda.
10. Tampilkan pendekatan akar, nilai fungsi di akar pendekatan, jumlah iterasi, dan tabel iterasi.

## Pseudocode

```text
MULAI
  Definisikan f(x)
  Masukkan a, b, toleransi, dan iterasi maksimum
  fa = f(a); fb = f(b)
  Jika fa * fb > 0: tampilkan pesan interval tidak mengurung akar

  UNTUK iterasi = 1 sampai iterasi maksimum:
      c = (a + b) / 2
      fc = f(c)
      batas_galat = (b - a) / 2
      Catat a, b, c, fc, dan batas_galat

      Jika |fc| <= toleransi atau batas_galat <= toleransi:
          Hentikan iterasi
      Jika fa * fc < 0:
          b = c; fb = fc
      Selain itu:
          a = c; fa = fc

  Tampilkan c dan catatan iterasi
SELESAI
```

## Hasil yang diharapkan

Untuk `f(x) = x³ + 2x − 7` pada interval `[1,2]`, akar berada di sekitar `x ≈ 1,568946`. Nilai akhir yang ditampilkan notebook bergantung pada toleransi dan batas iterasi yang dipilih.

## Catatan istilah pada instruksi tugas

Metode Bisection klasik menyelesaikan persamaan nonlinear **satu variabel**. Metode ini tidak secara langsung menyelesaikan sistem nonlinear yang terdiri atas beberapa persamaan dengan beberapa variabel. Notebook ini mengimplementasikan bentuk satu variabel yang lazim disebut pencarian akar persamaan nonlinear. Apabila dosen secara khusus meminta sistem multivariabel, tanyakan metode atau penyederhanaan yang diharapkan sebelum menganggap contoh ini sudah mencakup sistem multivariabel.
