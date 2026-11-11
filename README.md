# KOMPUTASI NUMERIK

**Tugas Ujian Tengah Semester (UTS)** — Teknik Informatika  
**Nama:** Muhammad Fahmi Amrulloh  
**NIM:** 202511420045

Repository ini berisi dokumentasi algoritma dan implementasi Python untuk dua materi komputasi numerik. Notebook dirancang agar dapat dijalankan secara berurutan maupun per bagian (cell) di Google Colab.

## Daftar proyek

### 1. Sistem Persamaan Linear (SPL) tiga variabel — Eliminasi Gauss

- Dokumen algoritma: [`02-Sistem-Persamaan-Linear/algoritma_spl.md`](02-Sistem-Persamaan-Linear/algoritma_spl.md)
- Notebook terdokumentasi: [`02-Sistem-Persamaan-Linear/SPL_Eliminasi_Gauss_Revisi.ipynb`](02-Sistem-Persamaan-Linear/SPL_Eliminasi_Gauss_Revisi.ipynb)
- [Buka notebook SPL di Google Colab](https://colab.research.google.com/github/FamsGit/Komputasi-Numerik/blob/main/02-Sistem-Persamaan-Linear/SPL_Eliminasi_Gauss_Revisi.ipynb)

Metode yang dipakai adalah Eliminasi Gauss dengan *partial pivoting*, dilanjutkan substitusi mundur. Program memeriksa ukuran matriks, pivot, dan residual hasil perhitungan.

### 2. Persamaan nonlinear satu variabel — Bisection

- Dokumen algoritma: [`03-Metode-Bisection/algoritma_bisection.md`](03-Metode-Bisection/algoritma_bisection.md)
- Notebook terdokumentasi: [`03-Metode-Bisection/Bisection_Nonlinear.ipynb`](03-Metode-Bisection/Bisection_Nonlinear.ipynb)
- [Buka notebook Bisection di Google Colab](https://colab.research.google.com/github/FamsGit/Komputasi-Numerik/blob/main/03-Metode-Bisection/Bisection_Nonlinear.ipynb)

**Catatan konsep:** Bisection klasik adalah metode pencarian akar untuk persamaan nonlinear kontinu dengan satu variabel. Metode ini bukan pemecah langsung sistem nonlinear multivariabel. Contoh pada notebook menggunakan fungsi satu variabel `f(x) = x³ + 2x − 7`; pastikan cakupan ini sesuai dengan arahan dosen.

## Struktur repository

```text
Komputasi-Numerik/
├── README.md
├── 01-Identitas/
│   └── tautan_akun.txt
├── 02-Sistem-Persamaan-Linear/
│   ├── algoritma_spl.md
│   └── SPL_Eliminasi_Gauss_Revisi.ipynb
├── 03-Metode-Bisection/
│   ├── algoritma_bisection.md
│   └── Bisection_Nonlinear.ipynb
├── 04-Prompt-AI/
│   └── prompt_ai.txt
└── 05-Video-Presentasi/
    └── PETUNJUK_VIDEO.md
```

## Identitas dan tautan

Tautan profil GitHub, LinkedIn, dan halaman Google Colab dicatat di [`01-Identitas/tautan_akun.txt`](01-Identitas/tautan_akun.txt). Google Colab menggunakan akun Google untuk proses masuk; tidak ada profil publik Colab yang setara dengan URL profil GitHub/LinkedIn.

## Cara menjalankan notebook

1. Buka tautan Google Colab pada bagian proyek di atas, atau buka `https://colab.research.google.com/`.
2. Pilih **File → Open notebook → GitHub**, lalu masukkan `FamsGit/Komputasi-Numerik`.
3. Pilih notebook yang ingin dijalankan.
4. Jalankan cell dari atas ke bawah dengan **Runtime → Run all**. Cell dapat dijalankan satu per satu setelah cell definisi fungsi dijalankan.
5. Ubah koefisien, ruas kanan, fungsi, interval, atau toleransi pada cell input untuk mencoba kasus lain.

Notebook memakai Python standar sehingga tidak memerlukan instalasi paket tambahan.

## Dokumentasi prompt AI

Prompt yang digunakan selama penyusunan tugas dicatat di [`04-Prompt-AI/prompt_ai.txt`](04-Prompt-AI/prompt_ai.txt). Catatan tersebut perlu diperbarui setiap kali ada prompt baru yang digunakan untuk tugas ini. Jangan mencatat prompt yang tidak benar-benar digunakan.

## Video presentasi

Folder [`05-Video-Presentasi/`](05-Video-Presentasi/) disiapkan untuk dua video MP4: penjelasan SPL dan penjelasan Bisection. Video akhir belum disertakan dalam paket ini karena bagian wajah, suara, dan narasi harus direkam sendiri oleh pemilik tugas. Ikuti spesifikasi di [`05-Video-Presentasi/PETUNJUK_VIDEO.md`](05-Video-Presentasi/PETUNJUK_VIDEO.md).

## Status kelengkapan

- [x] Repository dan identitas dasar
- [x] Algoritma SPL tiga variabel
- [x] Notebook Python SPL terdokumentasi
- [x] Algoritma Bisection
- [x] Notebook Python Bisection terdokumentasi
- [x] Catatan prompt AI awal
- [ ] Verifikasi notebook revisi di Google Colab setelah diunggah
- [ ] Video penjelasan SPL (MP4, maksimal 5 menit)
- [ ] Video penjelasan Bisection (MP4, maksimal 5 menit)
- [ ] Pastikan link repository dicantumkan pada profil LinkedIn
- [ ] Pemeriksaan akhir dan pengumpulan melalui Google Form

**Pembaruan:** tandai checklist setelah setiap item benar-benar selesai; jangan biarkan status `[x]` jika belum diverifikasi.
