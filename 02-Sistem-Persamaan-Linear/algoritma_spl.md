# Algoritma Penyelesaian SPL Tiga Variabel dengan Eliminasi Gauss

## Tujuan

Menentukan nilai tiga variabel dari sistem persamaan linear (SPL) menggunakan metode Eliminasi Gauss dengan *Partial Pivoting*. Metode ini bekerja dengan mengubah matriks augmented menjadi matriks segitiga atas, kemudian menghitung nilai variabel menggunakan substitusi mundur.

## Contoh Kasus

Diberikan sistem persamaan linear berikut:

$$
\begin{aligned}
4x + y - z &= 3 \\
2x + 5y + z &= 15 \\
x - y + 3z &= 8
\end{aligned}
$$

Matriks koefisien dan vektor konstanta:

$$
A=
\begin{bmatrix}
4&1&-1\\
2&5&1\\
1&-1&3
\end{bmatrix},
\qquad
b=
\begin{bmatrix}
3\\15\\8
\end{bmatrix}
$$

## Ide Metode

1. Membentuk matriks augmented `[A | b]` dengan menggabungkan matriks koefisien dan vektor konstanta.
2. Pada setiap kolom pivot, mencari elemen dengan nilai absolut terbesar dari baris aktif hingga baris terakhir. Proses ini disebut *Partial Pivoting*.
3. Menukar posisi baris aktif dengan baris yang memiliki elemen pivot terbesar jika diperlukan.
4. Menghitung faktor eliminasi menggunakan rumus:

   $$m=\frac{a_{ik}}{a_{kk}}$$

5. Menggunakan faktor eliminasi untuk mengubah elemen di bawah pivot menjadi nol.
6. Mengulangi proses eliminasi hingga terbentuk matriks segitiga atas.
7. Menghitung nilai variabel dari baris terakhir menuju baris pertama melalui substitusi mundur.
8. Memeriksa ketepatan hasil dengan menghitung residual menggunakan rumus:

   $$r=Ax-b$$

## Pseudocode

```text
MULAI
  Masukkan matriks koefisien A dan vektor konstanta b
  Salin A dan b agar data asli tidak berubah
  Tentukan ukuran sistem n

  Pastikan A berukuran n x n dan b memiliki panjang n
  Bentuk matriks augmented M = [A | b]

  UNTUK k dari 0 sampai n-1:
      Pilih baris p dengan nilai |M[p,k]| terbesar
      pada baris k sampai n-1

      JIKA |M[p,k]| mendekati nol:
          Hentikan proses karena solusi tunggal tidak dapat diperoleh

      JIKA p berbeda dengan k:
          Tukar baris k dengan baris p

      UNTUK i dari k+1 sampai n-1:
          faktor = M[i,k] / M[k,k]
          Set M[i,k] = 0

          UNTUK j dari k+1 sampai n:
              M[i,j] = M[i,j] - faktor * M[k,j]

  Siapkan vektor solusi x

  UNTUK i dari n-1 turun ke 0:
      jumlah = jumlahkan M[i,j] * x[j] untuk j > i
      x[i] = (M[i,n] - jumlah) / M[i,i]

  Hitung residual r = A*x - b
  Tampilkan solusi x dan residual r
SELESAI
```

## Contoh Proses Eliminasi

Matriks augmented awal:

$$
\left[
\begin{array}{ccc|c}
4&1&-1&3\\
2&5&1&15\\
1&-1&3&8
\end{array}
\right]
$$

### 1. Eliminasi kolom pertama

Elemen pivot terbesar pada kolom pertama adalah 4, sehingga tidak diperlukan pertukaran baris.

Operasi baris yang dilakukan:

- $R_2 \leftarrow R_2-0{,}5R_1$
- $R_3 \leftarrow R_3-0{,}25R_1$

Hasilnya:

$$
\left[
\begin{array}{ccc|c}
4&1&-1&3\\
0&4{,}5&1{,}5&13{,}5\\
0&-1{,}25&3{,}25&7{,}25
\end{array}
\right]
$$

### 2. Eliminasi kolom kedua

Elemen pivot pada kolom kedua adalah 4,5.

Faktor eliminasi untuk baris ketiga:

$$
m=\frac{-1{,}25}{4{,}5}=-\frac{5}{18}
$$

Operasi baris:

$$
R_3\leftarrow R_3-\left(-\frac{5}{18}\right)R_2
$$

Hasil matriks segitiga atas:

$$
\left[
\begin{array}{ccc|c}
4&1&-1&3\\
0&4{,}5&1{,}5&13{,}5\\
0&0&\frac{11}{3}&11
\end{array}
\right]
$$

## Substitusi Mundur

Setelah matriks segitiga atas terbentuk, nilai variabel dihitung dari baris paling bawah.

**1. Menghitung nilai z**

$$
\frac{11}{3}z=11
$$

$$
z=3
$$

**2. Menghitung nilai y**

$$
4{,}5y+1{,}5(3)=13{,}5
$$

$$
4{,}5y=9
$$

$$
y=2
$$

**3. Menghitung nilai x**

$$
4x+2-3=3
$$

$$
4x=4
$$

$$
x=1
$$

## Hasil yang Diharapkan

Berdasarkan proses eliminasi dan substitusi mundur, diperoleh:

$$
\boxed{x=1,\quad y=2,\quad z=3}
$$

Solusi tersebut diverifikasi dengan memasukkan kembali nilai variabel ke dalam persamaan awal:

| Persamaan | Substitusi | Hasil |
|---|---|---|
| 1 | $4(1)+2-3$ | 3 = 3 |
| 2 | $2(1)+5(2)+3$ | 15 = 15 |
| 3 | $1-2+3(3)$ | 8 = 8 |

Residual untuk ketiga persamaan adalah:

$$
r=Ax-b=
\begin{bmatrix}
0\\0\\0
\end{bmatrix}
$$

Dengan demikian, solusi yang diperoleh memenuhi sistem persamaan linear yang diberikan.

## Catatan Batas Metode

Metode Eliminasi Gauss dengan *Partial Pivoting* dapat digunakan untuk menyelesaikan sistem persamaan linear berbentuk matriks persegi yang memiliki solusi tunggal.

Pemilihan pivot terbesar berdasarkan nilai absolut membantu mengurangi risiko pembagian dengan bilangan yang terlalu kecil dan meningkatkan kestabilan numerik.

Apabila pivot mendekati nol, program perlu menghentikan proses atau memberikan pesan bahwa sistem tidak dapat diselesaikan sebagai sistem dengan solusi tunggal menggunakan prosedur tersebut.

Untuk sistem yang singular atau memiliki banyak solusi, diperlukan analisis tambahan untuk menentukan karakteristik solusinya.

## Kesimpulan

Metode Eliminasi Gauss dengan *Partial Pivoting* menyelesaikan SPL melalui dua tahapan utama, yaitu eliminasi maju dan substitusi mundur. Berdasarkan contoh yang diberikan, metode ini menghasilkan nilai $x=1$, $y=2$, dan $z=3$ dengan residual nol.

Hasil tersebut menunjukkan bahwa metode berhasil menyelesaikan sistem persamaan linear pada contoh kasus ini.
