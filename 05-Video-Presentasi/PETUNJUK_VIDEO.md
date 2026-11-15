# Petunjuk Video Presentasi

Dokumen ini berisi informasi dan urutan pembahasan dua video UTS Komputasi Numerik. Kedua video dibuat dalam format MP4 dan disusun berdasarkan implementasi notebook pada repositori ini.

## Daftar Video

| Materi | File Video |
|---|---|
| Sistem Persamaan Linear — Eliminasi Gauss dengan Partial Pivoting | [SPL-Eliminasi-Gauss.mp4](./SPL-Eliminasi-Gauss.mp4) |
| Sistem Persamaan Nonlinear — Metode Bisection | [SPNL-Bisection.mp4](./SPNL-Bisection.mp4) |

## Video 1 — SPL: Eliminasi Gauss dengan Partial Pivoting

### Urutan Pembahasan

1. **Pembukaan.** Menampilkan wajah dan memperkenalkan nama, NIM, program studi, serta topik presentasi.
2. **Menampilkan repositori GitHub.** Memperlihatkan repositori Komputasi Numerik dan notebook SPL yang digunakan.
3. **Membuka notebook di Google Colab.** Menjelaskan secara singkat susunan notebook dan tahapan implementasi.
4. **Menjelaskan permasalahan.** Memperkenalkan sistem persamaan linear tiga variabel, matriks koefisien, dan vektor konstanta.
5. **Menjelaskan fungsi pendukung.** Memperlihatkan fungsi `tampilkan_matriks` untuk menampilkan matriks selama proses perhitungan.
6. **Menjelaskan implementasi algoritma.** Menguraikan fungsi utama `eliminasi_gauss_partial_pivoting`, termasuk pembentukan matriks augmented, pemilihan pivot dengan Partial Pivoting, eliminasi maju, dan substitusi mundur.
7. **Menampilkan proses perhitungan.** Menjalankan program dan memperlihatkan tahapan eliminasi hingga terbentuk matriks segitiga atas. Pada contoh ini, pemilihan pivot tidak memerlukan pertukaran baris.
8. **Menampilkan hasil dan verifikasi.** Memperlihatkan solusi akhir `x = 1`, `y = 2`, dan `z = 3`, serta hasil residual yang bernilai nol.
9. **Kesimpulan.** Merangkum hasil penyelesaian sistem persamaan linear menggunakan Eliminasi Gauss dengan Partial Pivoting.

## Video 2 — SPNL: Metode Bisection

### Urutan Pembahasan

1. **Pembukaan.** Menampilkan wajah dan memperkenalkan nama, NIM, program studi, serta topik presentasi.
2. **Menampilkan repositori GitHub.** Memperlihatkan repositori Komputasi Numerik dan notebook Bisection yang digunakan.
3. **Membuka notebook di Google Colab.** Menjelaskan secara singkat susunan notebook dan tahapan implementasi.
4. **Menjelaskan permasalahan.** Memperkenalkan fungsi `f(x) = x³ + 2x - 7` dengan interval awal `[1, 2]`. Nilai fungsi pada kedua ujung interval memiliki tanda berlawanan, sehingga interval tersebut dapat digunakan untuk memulai metode Bisection.
5. **Menjelaskan fungsi dan parameter.** Memperlihatkan definisi fungsi, interval awal, toleransi `10⁻⁶`, dan batas maksimum iterasi.
6. **Menjelaskan implementasi algoritma.** Menguraikan fungsi `metode_bisection`, perhitungan titik tengah, pemilihan subinterval berdasarkan perubahan tanda, dan perhitungan batas galat interval.
7. **Menampilkan proses iterasi.** Menjalankan program dan memperlihatkan tabel iterasi untuk menunjukkan interval yang semakin menyempit.
8. **Menampilkan hasil dan verifikasi.** Memperlihatkan status konvergensi, jumlah iterasi, pendekatan akar sekitar `1.5689458847`, serta pemeriksaan batas galat interval terhadap toleransi.
9. **Kesimpulan.** Merangkum cara kerja metode Bisection dan hasil pendekatan akar yang diperoleh.

## Ketentuan dan Pemeriksaan Video

- Kedua video menggunakan format MP4.
- Durasi setiap video tidak melebihi 5 menit.
- Wajah dan suara sendiri ditampilkan pada bagian pembukaan dengan durasi minimal 15 detik.
- Penjelasan materi menggunakan narasi suara sendiri.
- Tulisan, kode, tabel, dan hasil perhitungan harus terlihat serta dapat dibaca.
- Audio dan video diperiksa kembali setelah proses ekspor.
- Nama file mengikuti daftar pada bagian **Daftar Video** di atas.

## Lokasi Berkas

Kedua file MP4 disimpan dalam folder ini pada repositori GitHub sebagai bagian dari dokumentasi proyek.

Untuk memudahkan pemutaran dan akses, kedua video presentasi juga tersedia melalui Google Drive:

**[Buka Folder Video Tugas 1 - UTS Komputasi Numerik](https://drive.google.com/drive/folders/1c5leSJKcPWhSW0mMvhpTMceTWJzo-Ced?usp=sharing)**

Folder tersebut berisi:
- SPL-Eliminasi-Gauss.mp4
- SPNL-Bisection.mp4
