# Algoritma Penyelesaian Sistem Persamaan Linear Tiga Variabel dengan Eliminasi Gauss

## 1. Tujuan

Menentukan nilai tiga variabel dari sistem persamaan linear (SPL) menggunakan metode Eliminasi Gauss dengan *Partial Pivoting*.

Metode ini bekerja dengan mengubah matriks augmented menjadi matriks segitiga atas melalui proses eliminasi maju (*forward elimination*). Setelah itu, nilai setiap variabel dihitung menggunakan substitusi mundur (*backward substitution*).

Penggunaan *Partial Pivoting* bertujuan memilih elemen pivot dengan nilai absolut terbesar pada kolom yang sedang diproses untuk membantu meningkatkan kestabilan perhitungan numerik.

## 2. Contoh Kasus

Diberikan sistem persamaan linear berikut:

$$
\begin{aligned}
4x+y-z&=3\\
2x+5y+z&=15\\
x-y+3z&=8
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
3\\
15\\
8
\end{bmatrix}
$$

Tujuan penyelesaian adalah memperoleh nilai $x$, $y$, dan $z$ yang memenuhi ketiga persamaan tersebut.

## 3. Ide Metode

Metode Eliminasi Gauss dengan *Partial Pivoting* dilakukan melalui tahapan berikut:

1. Menghitung faktor eliminasi menggunakan rumus:

   $$m_{ik} = \frac{M[i,k]}{M[k,k]}$$
3. Menggunakan faktor eliminasi untuk mengubah elemen di bawah pivot menjadi nol melalui operasi baris:

   $$M[i,j] = M[i,j] - m_{ik} \times M[k,j]$$
4. Mengulangi proses eliminasi hingga terbentuk matriks segitiga atas.
5. Menghitung nilai variabel dari baris terakhir menuju baris pertama melalui substitusi mundur.
6. Memeriksa ketepatan hasil dengan menghitung residual menggunakan matriks dan vektor konstanta asli:

   $$r = A_{\text{asli}}x - b_{\text{asli}}$$
   
Keterangan:

- $M$ adalah matriks augmented yang digunakan selama proses eliminasi.
- $M[i,k]$ adalah elemen pada baris $i$ dan kolom $k$.
- $M[k,k]$ adalah elemen pivot.
- $m_{ik}$ adalah faktor eliminasi untuk menghilangkan elemen di bawah pivot.

## 4. Pseudocode

```text
MULAI

  Masukkan matriks koefisien A dan vektor konstanta b
  Tentukan ukuran sistem n

  Pastikan A berukuran n x n
  Pastikan panjang b sama dengan n

  Simpan salinan A_asli dan b_asli
  Salin A dan b untuk proses perhitungan
  Bentuk matriks augmented M = [A | b]

  Tentukan ambang toleransi pivot

  UNTUK k dari 0 sampai n-1:

      Pilih baris p dengan nilai |M[p,k]| terbesar
      dari baris k sampai n-1

      JIKA |M[p,k]| <= ambang toleransi pivot:
          Hentikan proses
          Tampilkan pesan bahwa pivot nol
          atau terlalu kecil untuk perhitungan numerik

      JIKA p berbeda dengan k:
          Tukar seluruh elemen baris k dengan baris p

      UNTUK i dari k+1 sampai n-1:

          faktor = M[i,k] / M[k,k]
          Set M[i,k] = 0

          UNTUK j dari k+1 sampai n:
              M[i,j] = M[i,j] - faktor * M[k,j]

  Siapkan vektor solusi x

  UNTUK i dari n-1 turun ke 0:

      jumlah = jumlahkan M[i,j] * x[j]
               untuk j dari i+1 sampai n-1

      x[i] = (M[i,n] - jumlah) / M[i,i]

  Hitung residual menggunakan data asli:
      r = A_asli * x - b_asli

  Tampilkan solusi x
  Tampilkan residual r

SELESAI
```

**Catatan:** Ambang toleransi pivot digunakan untuk mendeteksi pivot yang nol atau terlalu kecil. Kondisi tersebut tidak otomatis membuktikan bahwa sistem tidak memiliki solusi tunggal, tetapi menunjukkan bahwa proses perlu dihentikan atau dianalisis lebih lanjut.

## 5. Contoh Proses Eliminasi

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

### 5.1 Eliminasi Kolom Pertama

Elemen pivot dipilih berdasarkan nilai absolut terbesar pada kolom pertama:

$$
\max(|4|,|2|,|1|)=4
$$

Elemen pivot terbesar adalah 4, sehingga tidak diperlukan pertukaran baris.

Operasi baris yang dilakukan:

- $R_2\leftarrow R_2-0{,}5R_1$
- $R_3\leftarrow R_3-0{,}25R_1$

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

### 5.2 Eliminasi Kolom Kedua

Pada kolom kedua, elemen yang dibandingkan adalah 4,5 dan -1,25.

Nilai absolut terbesar adalah:

$$
\max(|4{,}5|,|-1{,}25|)=4{,}5
$$

Dengan demikian, elemen pivot tetap 4,5 dan tidak diperlukan pertukaran baris.

Faktor eliminasi untuk baris ketiga:

$$
m_{32}=\frac{-1{,}25}{4{,}5}
$$

$$
m_{32}=-\frac{5}{18}
$$

Operasi baris yang dilakukan:

$$
R_3\leftarrow R_3-\left(-\frac{5}{18}\right)R_2
$$

Atau dapat dituliskan:

$$
R_3\leftarrow R_3+\frac{5}{18}R_2
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

Pada contoh ini, proses *Partial Pivoting* tetap dilakukan dengan membandingkan elemen pivot pada setiap kolom. Namun, tidak terjadi pertukaran baris karena elemen pivot yang terpilih sudah berada pada baris aktif.

## 6. Substitusi Mundur

Setelah matriks segitiga atas terbentuk, nilai variabel dihitung mulai dari baris paling bawah menuju baris pertama.

### 6.1 Menghitung Nilai z

Dari baris ketiga diperoleh:

$$
\frac{11}{3}z=11
$$

$$
z=3
$$

### 6.2 Menghitung Nilai y

Dari baris kedua:

$$
4{,}5y+1{,}5(3)=13{,}5
$$

$$
4{,}5y+4{,}5=13{,}5
$$

$$
4{,}5y=9
$$

$$
y=2
$$

### 6.3 Menghitung Nilai x

Dari baris pertama:

$$
4x+y-z=3
$$

Substitusikan nilai $y=2$ dan $z=3$:

$$
4x+2-3=3
$$

$$
4x=4
$$

$$
x=1
$$

Dengan demikian, diperoleh nilai $x=1$, $y=2$, dan $z=3$.

## 7. Hasil yang Diharapkan

Berdasarkan proses eliminasi maju dan substitusi mundur, diperoleh solusi:

$$
\boxed{x=1,\qquad y=2,\qquad z=3}
$$

### 7.1 Verifikasi Solusi

Solusi diperiksa dengan memasukkan kembali nilai variabel ke dalam ketiga persamaan awal.

| Persamaan | Substitusi | Hasil |
|---|---|---|
| Pertama | $4(1)+2-3$ | $3=3$ |
| Kedua | $2(1)+5(2)+3$ | $15=15$ |
| Ketiga | $1-2+3(3)$ | $8=8$ |

Seluruh persamaan menghasilkan nilai yang sama dengan konstanta pada ruas kanan.

### 7.2 Perhitungan Residual

Dengan solusi yang diperoleh, yaitu x = [1, 2, 3]ᵀ, residual dihitung menggunakan matriks dan vektor konstanta asli.

**Langkah 1. Kalikan matriks dengan vektor solusi.**

$$
Ax =
\begin{bmatrix}
4 & 1 & -1 \\
2 & 5 & 1 \\
1 & -1 & 3
\end{bmatrix}
\begin{bmatrix}
1 \\
2 \\
3
\end{bmatrix}
=
\begin{bmatrix}
3 \\
15 \\
8
\end{bmatrix}
$$

**Langkah 2. Kurangkan hasil perkalian dengan vektor konstanta asli.**

$$
r = Ax - b
$$

$$
r =
\begin{bmatrix}
3 \\
15 \\
8
\end{bmatrix}
-
\begin{bmatrix}
3 \\
15 \\
8
\end{bmatrix}
$$

**Langkah 3. Peroleh hasil residual.**

$$
r =
\begin{bmatrix}
0 \\
0 \\
0
\end{bmatrix}
$$

Hasil residual merupakan vektor nol. Hal ini menunjukkan bahwa solusi x = [1, 2, 3] memenuhi sistem persamaan linear tersebut.

## 8. Catatan Batas Metode

Metode Eliminasi Gauss dengan *Partial Pivoting* digunakan untuk menyelesaikan sistem persamaan linear berbentuk matriks persegi. Metode ini dapat menghasilkan solusi tunggal apabila matriks koefisien tidak singular.

Beberapa hal yang perlu diperhatikan:

- Pemilihan pivot dilakukan dengan mencari nilai absolut terbesar pada kolom yang sedang diproses, mulai dari baris aktif hingga baris terakhir.
- Pertukaran baris dilakukan apabila elemen pivot terbesar tidak berada pada baris aktif.
- Pivot yang bernilai nol menyebabkan pembagian tidak dapat dilakukan.
- Pivot yang terlalu kecil dapat menyebabkan ketidakstabilan numerik sehingga perlu diperiksa berdasarkan ambang toleransi yang digunakan.
- Apabila sistem singular atau memiliki banyak solusi, diperlukan analisis tambahan untuk menentukan karakteristik sistem dan solusinya.

Keunggulan metode ini adalah dapat menyelesaikan sistem persamaan linear secara sistematis serta membantu meningkatkan kestabilan perhitungan melalui pemilihan pivot.

Namun, metode ini tetap dapat mengalami masalah numerik apabila sistem memiliki kondisi matriks yang buruk atau sangat sensitif terhadap kesalahan pembulatan.

## 9. Kesimpulan

Metode Eliminasi Gauss dengan *Partial Pivoting* menyelesaikan sistem persamaan linear melalui dua tahapan utama, yaitu eliminasi maju dan substitusi mundur.

Berdasarkan contoh sistem persamaan linear tiga variabel yang diberikan, diperoleh solusi:

$$
x=1,\qquad y=2,\qquad z=3
$$

Hasil verifikasi menunjukkan bahwa ketiga persamaan terpenuhi dan residual yang diperoleh bernilai nol.

Dengan demikian, metode Eliminasi Gauss dengan *Partial Pivoting* berhasil digunakan untuk menyelesaikan contoh sistem persamaan linear tersebut.
