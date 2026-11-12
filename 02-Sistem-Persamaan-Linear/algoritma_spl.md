# Algoritma Penyelesaian SPL Tiga Variabel dengan Eliminasi Gauss

## Tujuan

Menentukan nilai tiga variabel dari sistem persamaan linear dengan mengubah matriks augmented menjadi matriks segitiga atas, lalu menghitung variabel dari bawah ke atas melalui substitusi mundur.

## Contoh kasus

\[
\begin{aligned}
4x + y - z &= 3 \\
2x + 5y + z &= 15 \\
x - y + 3z &= 8
\end{aligned}
\]

Matriks koefisien dan vektor konstanta:

\[
A=\begin{bmatrix}4&1&-1\\2&5&1\\1&-1&3\end{bmatrix},\qquad
b=\begin{bmatrix}3\\15\\8\end{bmatrix}
\]

## Ide metode

1. Bentuk matriks augmented `[A | b]`.
2. Pada kolom pivot ke-`k`, cari baris dengan nilai absolut elemen terbesar mulai baris `k` sampai baris terakhir. Pemilihan ini disebut *partial pivoting*.
3. Tukar baris pivot terpilih dengan baris `k` bila keduanya berbeda.
4. Untuk setiap baris di bawah pivot, hitung faktor eliminasi `m = a[i,k] / a[k,k]`.
5. Kurangi elemen baris tersebut dengan `m` kali baris pivot sehingga elemen di bawah pivot menjadi nol.
6. Ulangi untuk kolom pivot berikutnya sampai terbentuk matriks segitiga atas.
7. Hitung variabel terakhir, lalu gunakan substitusi mundur untuk memperoleh variabel sebelumnya.
8. Periksa hasil dengan menghitung residual `A x - b`.

## Pseudocode

```text
MULAI
  Masukkan matriks koefisien A dan vektor konstanta b
  Pastikan A berukuran n x n dan b berukuran n
  Bentuk matriks augmented M = [A | b]

  UNTUK k dari 0 sampai n-1:
      Pilih baris p dengan |M[p,k]| terbesar pada baris k sampai n-1
      JIKA |M[p,k]| mendekati nol:
          Hentikan: sistem tidak memiliki solusi tunggal
      Tukar baris k dan p jika p berbeda dengan k

      UNTUK i dari k+1 sampai n-1:
          faktor = M[i,k] / M[k,k]
          Set M[i,k] = 0
          UNTUK j dari k+1 sampai n:
              M[i,j] = M[i,j] - faktor * M[k,j]

  UNTUK i dari n-1 turun ke 0:
      jumlah = jumlahkan M[i,j] * x[j] untuk j > i
      x[i] = (M[i,n] - jumlah) / M[i,i]

  Hitung residual r = A*x - b
  Tampilkan x dan residual
SELESAI
```

## Contoh ringkas proses eliminasi

Matriks augmented awal adalah:

\[
\left[\begin{array}{ccc|c}
4&1&-1&3\\
2&5&1&15\\
1&-1&3&8
\end{array}\right]
\]

Pada kolom pertama, pivot terbesar sudah berada di baris pertama. Operasi `R2 ← R2 − 0,5R1` dan `R3 ← R3 − 0,25R1` menghasilkan:

\[
\left[\begin{array}{ccc|c}
4&1&-1&3\\
0&4.5&1.5&13.5\\
0&-1.25&3.25&7.25
\end{array}\right]
\]

Pada kolom kedua, faktor eliminasi baris ketiga adalah `−1,25 / 4,5 = −5/18`. Operasi `R3 ← R3 − (−5/18)R2` menghasilkan baris ketiga `[0, 0, 11/3 | 11]`. Dengan demikian `z = 3`, kemudian `y = (13,5 − 1,5 × 3) / 4,5 = 2`, dan `x = (3 − y + z) / 4 = 1`.

## Hasil yang diharapkan untuk contoh

\[
x=1,\qquad y=2,\qquad z=3
\]

Nilai ini dapat diverifikasi dengan memasukkannya kembali ke ketiga persamaan. Residual idealnya nol atau sangat dekat dengan nol karena pembulatan numerik.

## Catatan batas metode

Eliminasi Gauss dengan pivoting cocok untuk sistem persegi yang memiliki solusi tunggal. Jika pivot yang dipilih mendekati nol, program perlu berhenti atau melaporkan bahwa sistem tidak dapat diselesaikan sebagai solusi tunggal dengan prosedur ini. Untuk sistem yang singular atau memiliki banyak solusi, dibutuhkan analisis lebih lanjut.
