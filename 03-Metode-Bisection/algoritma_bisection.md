# Algoritma Pencarian Akar Persamaan Nonlinear dengan Metode Bisection

## 1. Tujuan

Menentukan pendekatan akar dari persamaan nonlinear satu variabel berbentuk \(f(x)=0\) menggunakan metode Bisection atau metode bagi dua.

Metode ini bekerja dengan mempertahankan interval yang mengapit akar, kemudian membagi interval tersebut menjadi dua bagian secara berulang hingga diperoleh pendekatan akar dengan tingkat ketelitian sesuai toleransi yang ditentukan.

Syarat utama metode Bisection adalah fungsi harus kontinu pada interval yang digunakan dan nilai fungsi pada kedua ujung interval harus memiliki tanda berlawanan, kecuali jika salah satu ujungnya sudah merupakan akar tepat.

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

Karena nilai fungsi pada kedua ujung interval memiliki tanda berlawanan:

$$
f(a)\times f(b)=(-4)(5)=-20<0
$$

Maka terdapat setidaknya satu akar pada interval \([1,2]\) berdasarkan Teorema Nilai Antara.

## 3. Rumus Utama

Titik tengah interval pada setiap iterasi dihitung menggunakan rumus:

$$
c=\frac{a+b}{2}
$$

Keterangan:

- \(a\) adalah batas bawah interval.
- \(b\) adalah batas atas interval.
- \(c\) adalah titik tengah atau pendekatan akar.

Setelah nilai \(f(c)\) diperoleh, tentukan interval berikutnya berdasarkan perubahan tanda:

1. Jika \(f(a)\times f(c)<0\), akar berada pada interval \([a,c]\), sehingga batas atas diperbarui menjadi \(b=c\).
2. Jika \(f(c)\times f(b)<0\), akar berada pada interval \([c,b]\), sehingga batas bawah diperbarui menjadi \(a=c\).
3. Jika \(f(c)=0\), titik tengah merupakan akar tepat dan proses dapat dihentikan.

Batas galat interval untuk pendekatan akar pada setiap iterasi dihitung menggunakan:

$$
E=\frac{b-a}{2}
$$

Nilai tersebut merupakan batas atas galat absolut titik tengah terhadap akar yang berada dalam interval saat itu.

## 4. Contoh Tiga Iterasi Pertama

### Iterasi 1

Interval awal:

$$
[a,b]=[1,2]
$$

Titik tengah:

$$
c=\frac{1+2}{2}=1{,}5
$$

Nilai fungsi:

$$
f(1{,}5)=1{,}5^3+2(1{,}5)-7=-0{,}625
$$

Karena \(f(1{,}5)\) negatif dan \(f(2)\) positif, interval baru menjadi:

$$
[1{,}5,2]
$$

### Iterasi 2

Titik tengah:

$$
c=\frac{1{,}5+2}{2}=1{,}75
$$

Nilai fungsi:

$$
f(1{,}75)=1{,}75^3+2(1{,}75)-7
$$

$$
f(1{,}75)=1{,}859375
$$

Karena \(f(1{,}5)\) negatif dan \(f(1{,}75)\) positif, interval baru menjadi:

$$
[1{,}5,1{,}75]
$$

### Iterasi 3

Titik tengah:

$$
c=\frac{1{,}5+1{,}75}{2}=1{,}625
$$

Nilai fungsi:

$$
f(1{,}625)=1{,}625^3+2(1{,}625)-7
$$

$$
f(1{,}625)=0{,}541015625
$$

Karena \(f(1{,}5)\) negatif dan \(f(1{,}625)\) positif, interval baru menjadi:

$$
[1{,}5,1{,}625]
$$

Contoh tersebut menunjukkan bahwa panjang interval selalu menjadi setengah dari panjang interval sebelumnya selama proses iterasi berlangsung.

## 5. Langkah Algoritma

1. Mendefinisikan fungsi nonlinear \(f(x)\) yang akan dicari akarnya.
2. Memasukkan batas bawah \(a\), batas atas \(b\), toleransi, dan jumlah iterasi maksimum.
3. Menghitung nilai fungsi pada kedua ujung interval, yaitu \(f(a)\) dan \(f(b)\).
4. Memeriksa apakah salah satu ujung interval merupakan akar tepat. Jika ya, proses dapat langsung dihentikan.
5. Memastikan nilai \(f(a)\) dan \(f(b)\) memiliki tanda berlawanan. Jika tidak, interval ditolak karena belum memenuhi syarat pengurungan akar.
6. Menghitung titik tengah interval menggunakan rumus \(c=(a+b)/2\).
7. Menghitung nilai fungsi pada titik tengah, yaitu \(f(c)\).
8. Menghitung batas galat interval menggunakan rumus \(E=(b-a)/2\).
9. Mencatat nomor iterasi, nilai \(a\), \(b\), \(c\), \(f(c)\), dan batas galat ke dalam tabel iterasi.
10. Memeriksa kondisi penghentian. Proses dihentikan apabila \(|f(c)|\) atau batas galat sudah lebih kecil atau sama dengan toleransi, atau apabila jumlah iterasi maksimum telah tercapai.
11. Jika kondisi penghentian belum terpenuhi, menentukan setengah interval yang masih memiliki perubahan tanda.
12. Mengulangi proses hingga kondisi penghentian terpenuhi.
13. Menampilkan pendekatan akar, nilai fungsi pada pendekatan akar, jumlah iterasi, status konvergensi, dan tabel hasil iterasi.

## 6. Pseudocode

```text
MULAI
  Definisikan fungsi f(x)
  Masukkan batas bawah a, batas atas b,
  toleransi, dan iterasi maksimum

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

  Siapkan tabel riwayat iterasi

  UNTUK iterasi = 1 sampai iterasi maksimum:
      c = (a + b) / 2
      fc = f(c)
      batas_galat = (b - a) / 2

      Catat iterasi, a, b, c, fc, batas_galat

      JIKA fc = 0:
          Tandai akar ditemukan secara tepat
          Hentikan iterasi

      JIKA |fc| <= toleransi ATAU
         batas_galat <= toleransi:
          Tandai toleransi terpenuhi
          Hentikan iterasi

      JIKA fa dan fc memiliki tanda berlawanan:
          b = c
          fb = fc
      SELAIN ITU:
          a = c
          fa = fc

  Tampilkan pendekatan akar c
  Tampilkan nilai f(c)
  Tampilkan jumlah iterasi
  Tampilkan status konvergensi
  Tampilkan tabel riwayat iterasi
SELESAI
```

## 7. Hasil yang Diharapkan

Untuk persamaan:

$$
f(x)=x^3+2x-7
$$

Dengan interval awal \([1,2]\), toleransi \(10^{-6}\), dan batas iterasi maksimum 100, pendekatan akar yang diperoleh adalah sekitar:

$$
\boxed{x\approx1{,}568946}
$$

Nilai fungsi pada pendekatan akar akan mendekati nol.

Dengan batas galat interval sebagai kriteria penghentian, metode Bisection dapat mencapai toleransi $10^{-6}$ dalam 20 iterasi pada contoh ini.

Hasil akhir dapat sedikit berbeda apabila kriteria penghentian atau toleransi yang digunakan berbeda.

## 8. Verifikasi Hasil

Untuk memastikan pendekatan akar sudah benar, masukkan kembali nilai pendekatan akar ke fungsi awal:

$$
f(x)=x^3+2x-7
$$

Apabila hasil perhitungan mendekati nol, pendekatan akar dapat dianggap memenuhi persamaan dalam batas toleransi yang digunakan.

Selain itu, batas galat interval perlu diperiksa untuk memastikan tingkat ketelitian pendekatan akar telah memenuhi kriteria penghentian.

## 9. Catatan Batas Metode

Metode Bisection klasik digunakan untuk mencari akar persamaan nonlinear satu variabel, bukan untuk menyelesaikan sistem persamaan nonlinear yang terdiri atas beberapa variabel.

Metode ini mensyaratkan fungsi kontinu pada interval dan adanya perubahan tanda pada kedua ujung interval. Perubahan tanda menjamin setidaknya terdapat satu akar dalam interval, tetapi tidak selalu menjamin hanya terdapat satu akar.

Keunggulan metode Bisection adalah prosesnya sederhana, stabil, dan memiliki batas galat yang dapat diperkirakan. Kekurangannya adalah konvergensi relatif lambat dibandingkan beberapa metode pencarian akar lainnya.

Apabila instruksi dosen secara khusus meminta penyelesaian sistem nonlinear multivariabel, diperlukan klarifikasi mengenai metode atau bentuk penyederhanaan yang diharapkan.

## 10. Kesimpulan

Metode Bisection merupakan metode numerik untuk mencari pendekatan akar persamaan nonlinear satu variabel dengan membagi interval yang mengapit akar menjadi dua bagian secara berulang.

Berdasarkan contoh \(f(x)=x^3+2x-7\) pada interval awal \([1,2]\), diperoleh pendekatan akar sekitar **1,568946**.

Dengan menggunakan toleransi \(10^{-6}\), metode Bisection dapat menghasilkan pendekatan akar dengan batas galat yang memenuhi toleransi setelah 20 iterasi, apabila menggunakan kriteria batas galat interval.

Dengan demikian, metode Bisection berhasil digunakan untuk menyelesaikan contoh pencarian akar persamaan nonlinear tersebut.
