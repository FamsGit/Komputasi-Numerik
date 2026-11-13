# Algoritma Pencarian Akar Persamaan Nonlinear dengan Metode Bisection

## 1. Tujuan

Menentukan pendekatan akar dari persamaan nonlinear satu variabel berbentuk $f(x)=0$ menggunakan metode Bisection atau metode bagi dua.

Metode Bisection bekerja dengan mempertahankan interval yang mengapit akar, kemudian membagi interval tersebut menjadi dua bagian secara berulang hingga diperoleh pendekatan akar dengan tingkat ketelitian sesuai toleransi yang ditentukan.

Syarat utama metode Bisection adalah fungsi kontinu pada interval yang digunakan dan nilai fungsi pada kedua ujung interval memiliki tanda berlawanan. Kondisi tersebut menjamin setidaknya terdapat satu akar di dalam interval berdasarkan Teorema Nilai Antara.

## 2. Contoh Kasus

Diberikan persamaan nonlinear:

$$
f(x)=x^3+2x-7
$$

Gunakan interval awal:

$$
a=1,\qquad b=2
$$

Hitung nilai fungsi pada kedua ujung interval:

$$
f(1)=1^3+2(1)-7=-4
$$

$$
f(2)=2^3+2(2)-7=5
$$

Kalikan kedua nilai fungsi:

$$
f(a)\times f(b)=(-4)(5)=-20<0
$$

Karena hasil perkalian bernilai negatif, terdapat perubahan tanda pada kedua ujung interval. Dengan demikian, interval awal $[1,2]$ memenuhi syarat untuk menerapkan metode Bisection.

Fungsi yang digunakan merupakan fungsi polinomial sehingga kontinu pada seluruh bilangan real.

## 3. Rumus Utama

### 3.1 Menghitung Titik Tengah

Titik tengah interval pada setiap iterasi dihitung menggunakan rumus:

$$
c=\frac{a+b}{2}
$$

Keterangan:

- $a$ adalah batas bawah interval.
- $b$ adalah batas atas interval.
- $c$ adalah titik tengah yang digunakan sebagai pendekatan akar.

### 3.2 Menentukan Interval Berikutnya

Setelah memperoleh nilai $f(c)$, tentukan interval baru berdasarkan perubahan tanda:

1. Jika $f(a)\times f(c)<0$, akar berada pada interval $[a,c]$. Oleh karena itu, batas atas diperbarui menjadi $b=c$.
2. Jika $f(c)\times f(b)<0$, akar berada pada interval $[c,b]$. Oleh karena itu, batas bawah diperbarui menjadi $a=c$.
3. Jika $f(c)=0$, titik tengah merupakan akar tepat sehingga proses dapat langsung dihentikan.

### 3.3 Menghitung Batas Galat Interval

Batas galat untuk pendekatan akar pada setiap iterasi dihitung menggunakan rumus:

$$
E=\frac{b-a}{2}
$$

Nilai tersebut merupakan batas atas galat absolut antara titik tengah dan akar yang berada dalam interval saat itu.

Proses iterasi dihentikan apabila:

$$
E\leq \text{toleransi}
$$

Pada contoh ini, toleransi yang digunakan adalah $10^{-6}$.

Perlu diperhatikan bahwa batas galat interval berbeda dengan nilai absolut fungsi $|f(c)|$. Batas galat interval digunakan untuk memperkirakan ketelitian posisi akar, sedangkan $|f(c)|$ menunjukkan seberapa dekat nilai fungsi pada pendekatan akar terhadap nol.

## 4. Contoh Tiga Iterasi Pertama

### Iterasi 1

Interval awal:

$$
[a,b]=[1,2]
$$

Menghitung titik tengah:

$$
c=\frac{1+2}{2}=1{,}5
$$

Menghitung nilai fungsi:

$$
f(1{,}5)=1{,}5^3+2(1{,}5)-7
$$

$$
f(1{,}5)=-0{,}625
$$

Karena $f(1{,}5)$ negatif dan $f(2)$ positif, interval baru menjadi:

$$
[1{,}5,2]
$$

### Iterasi 2

Interval saat ini:

$$
[a,b]=[1{,}5,2]
$$

Menghitung titik tengah:

$$
c=\frac{1{,}5+2}{2}=1{,}75
$$

Menghitung nilai fungsi:

$$
f(1{,}75)=1{,}75^3+2(1{,}75)-7
$$

$$
f(1{,}75)=1{,}859375
$$

Karena $f(1{,}5)$ negatif dan $f(1{,}75)$ positif, interval baru menjadi:

$$
[1{,}5,1{,}75]
$$

### Iterasi 3

Interval saat ini:

$$
[a,b]=[1{,}5,1{,}75]
$$

Menghitung titik tengah:

$$
c=\frac{1{,}5+1{,}75}{2}=1{,}625
$$

Menghitung nilai fungsi:

$$
f(1{,}625)=1{,}625^3+2(1{,}625)-7
$$

$$
f(1{,}625)=0{,}541015625
$$

Karena $f(1{,}5)$ negatif dan $f(1{,}625)$ positif, interval baru menjadi:

$$
[1{,}5,1{,}625]
$$

Dari ketiga iterasi tersebut, terlihat bahwa interval yang mengapit akar selalu dipersempit menjadi setengah dari panjang interval sebelumnya.

## 5. Langkah Algoritma

1. Mendefinisikan fungsi nonlinear $f(x)$ yang akan dicari akarnya.
2. Memasukkan batas bawah $a$, batas atas $b$, nilai toleransi, dan jumlah iterasi maksimum.
3. Menghitung nilai fungsi pada kedua ujung interval, yaitu $f(a)$ dan $f(b)$.
4. Memeriksa apakah salah satu ujung interval merupakan akar tepat. Jika ya, proses langsung dihentikan.
5. Memeriksa apakah kedua ujung interval memiliki tanda berlawanan. Jika tidak, interval ditolak karena belum memenuhi syarat metode Bisection.
6. Menghitung titik tengah interval menggunakan rumus $c=(a+b)/2$.
7. Menghitung nilai fungsi pada titik tengah, yaitu $f(c)$.
8. Menghitung batas galat interval menggunakan rumus $E=(b-a)/2$.
9. Mencatat nomor iterasi, nilai $a$, $b$, $c$, $f(c)$, dan batas galat ke dalam tabel iterasi.
10. Memeriksa kondisi penghentian. Jika $f(c)=0$ atau batas galat interval sudah lebih kecil atau sama dengan toleransi, proses dihentikan.
11. Jika kondisi penghentian belum terpenuhi, menentukan setengah interval yang masih mengapit akar berdasarkan perubahan tanda.
12. Mengulangi proses hingga batas galat memenuhi toleransi atau jumlah iterasi maksimum tercapai.
13. Menampilkan pendekatan akar, nilai fungsi pada pendekatan akar, batas galat, jumlah iterasi, status konvergensi, dan tabel hasil iterasi.

**Catatan:** Pada algoritma ini, batas galat interval menjadi kriteria utama penghentian. Nilai $|f(c)|$ tetap ditampilkan sebagai informasi untuk memeriksa hasil, tetapi tidak digunakan sebagai pengganti batas galat posisi akar.

## 6. Pseudocode

```text
MULAI

  Definisikan fungsi f(x)
  Masukkan batas bawah a, batas atas b,
  toleransi, dan jumlah iterasi maksimum

  Hitung fa = f(a)
  Hitung fb = f(b)

  JIKA fa = 0:
      Tampilkan a sebagai akar
      SELESAI

  JIKA fb = 0:
      Tampilkan b sebagai akar
      SELESAI

  JIKA fa dan fb memiliki tanda yang sama:
      Tampilkan pesan bahwa interval tidak mengurung akar
      SELESAI

  konvergen = FALSE

  UNTUK iterasi = 1 sampai iterasi maksimum:

      c = (a + b) / 2
      fc = f(c)
      batas_galat = (b - a) / 2

      Catat iterasi, a, b, c, fc, batas_galat

      JIKA fc = 0:
          konvergen = TRUE
          Hentikan iterasi

      JIKA batas_galat <= toleransi:
          konvergen = TRUE
          Hentikan iterasi

      JIKA fa dan fc memiliki tanda berlawanan:
          b = c
          fb = fc
      SELAIN ITU:
          a = c
          fa = fc

  Tampilkan pendekatan akar c
  Tampilkan nilai f(c)
  Tampilkan batas galat
  Tampilkan jumlah iterasi
  Tampilkan status konvergensi
  Tampilkan tabel riwayat iterasi

SELESAI
```

Apabila jumlah iterasi maksimum tercapai sebelum batas galat memenuhi toleransi, status konvergensi tetap bernilai FALSE. Dengan demikian, algoritma tidak menyatakan berhasil ketika kriteria penghentian belum terpenuhi.

## 7. Hasil yang Diharapkan

Untuk persamaan:

$$
f(x)=x^3+2x-7
$$

Dengan menggunakan interval awal $[1,2]$, toleransi $10^{-6}$, dan jumlah iterasi maksimum 100, diperoleh pendekatan akar setelah 20 iterasi.

Hasil pendekatan akar pada iterasi ke-20 adalah:

$$
x_{20}\approx1{,}5689458847
$$

Dibulatkan menjadi enam angka di belakang koma:

$$
x\approx1{,}568946
$$

Batas galat interval pada iterasi ke-20 adalah:

$$
E_{20}=\frac{2-1}{2^{20}}
$$

$$
E_{20}\approx0{,}000000953674
$$

Karena:

$$
E_{20}<10^{-6}
$$

Maka kriteria penghentian telah terpenuhi setelah 20 iterasi.

Nilai fungsi pada pendekatan akar tersebut adalah:

$$
f(x_{20})\approx-0{,}000004864578
$$

Nilai fungsi tersebut mendekati nol. Perlu diperhatikan bahwa nilai $|f(x_{20})|$ tidak harus lebih kecil dari toleransi, karena kriteria yang digunakan untuk menjamin ketelitian posisi akar adalah batas galat interval.

## 8. Verifikasi Hasil

Verifikasi dilakukan dengan dua cara:

1. **Memeriksa nilai fungsi.** Masukkan pendekatan akar ke dalam fungsi awal:

   $$
   f(x)=x^3+2x-7
   $$

   Hasilnya seharusnya mendekati nol. Pada iterasi ke-20, diperoleh nilai fungsi sekitar $-0{,}000004864578$.

2. **Memeriksa batas galat interval.** Pastikan batas galat pendekatan akar sudah lebih kecil atau sama dengan toleransi yang ditentukan.

   $$
   E_{20}\approx9{,}536743\times10^{-7}
   $$

   Nilai tersebut lebih kecil daripada toleransi $10^{-6}$ sehingga pendekatan akar telah memenuhi kriteria ketelitian yang digunakan.

## 9. Catatan Batas Metode

Metode Bisection klasik digunakan untuk mencari akar persamaan nonlinear satu variabel, bukan untuk menyelesaikan sistem persamaan nonlinear yang terdiri atas beberapa variabel.

Metode ini memiliki beberapa ketentuan:

- Fungsi harus kontinu pada interval yang digunakan.
- Nilai fungsi pada kedua ujung interval harus memiliki tanda berlawanan, kecuali jika salah satu ujung merupakan akar tepat.
- Perubahan tanda menjamin setidaknya terdapat satu akar dalam interval, tetapi tidak selalu menjamin hanya terdapat satu akar.
- Metode ini memiliki konvergensi yang stabil, tetapi relatif lambat dibandingkan beberapa metode pencarian akar lainnya.

Apabila instruksi dosen secara khusus meminta penyelesaian sistem persamaan nonlinear multivariabel, diperlukan klarifikasi mengenai metode atau bentuk penyederhanaan yang diharapkan.

## 10. Kesimpulan

Metode Bisection merupakan metode numerik untuk mencari pendekatan akar persamaan nonlinear satu variabel dengan membagi interval yang mengapit akar menjadi dua bagian secara berulang.

Berdasarkan contoh $f(x)=x^3+2x-7$ pada interval awal $[1,2]$, diperoleh pendekatan akar sebesar $1{,}5689458847$ atau sekitar $1{,}568946$.

Dengan menggunakan toleransi $10^{-6}$ dan batas galat interval sebagai kriteria penghentian, metode Bisection berhasil mencapai batas galat sekitar $9{,}536743\times10^{-7}$ setelah 20 iterasi.

Dengan demikian, metode Bisection berhasil digunakan untuk menyelesaikan contoh pencarian akar persamaan nonlinear tersebut sesuai dengan toleransi yang telah ditentukan.
