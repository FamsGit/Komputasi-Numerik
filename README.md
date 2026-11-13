# Numerical Computation | Komputasi Numerik

<p align="center">
  <strong>Numerical Methods Implementation Using Python</strong>
  <br>
  A collection of numerical algorithms developed as part of an academic project in Informatics Engineering.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Google-Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white" />
  <img src="https://img.shields.io/badge/Status-Academic%20Project-2563EB?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Repository-Public-16A34A?style=for-the-badge&logo=github&logoColor=white" />
</p>

---

## Overview

**Komputasi Numerik** merupakan proyek akademik yang membahas penerapan metode numerik untuk menyelesaikan permasalahan matematika menggunakan bahasa pemrograman Python.

Repository ini dikembangkan sebagai dokumentasi pembelajaran, implementasi algoritma, serta eksplorasi proses perhitungan numerik secara sistematis dan terstruktur.

Setiap metode dilengkapi dengan dasar teori, algoritma penyelesaian, implementasi Python, penjelasan kode, dan hasil pengujian.

## Project Modules

### 01. Sistem Persamaan Linear — Eliminasi Gauss

Implementasi metode Eliminasi Gauss dengan Partial Pivoting untuk menyelesaikan sistem persamaan linear tiga variabel.

**Cakupan pembahasan:**
- Representasi sistem persamaan dalam matriks augmented.
- Pemilihan elemen pivot.
- Pertukaran baris (row swapping).
- Eliminasi elemen di bawah pivot.
- Substitusi mundur (back substitution).
- Verifikasi hasil perhitungan.

**Contoh sistem persamaan:**

$$
\begin{aligned}
4x + y - z &= 3 \\
2x + 5y + z &= 15 \\
x - y + 3z &= 8
\end{aligned}
$$

**Files:**
- [Algoritma SPL](02-SPL-Eliminasi-Gauss/algoritma_spl.md)
- [Python Notebook — SPL](02-SPL-Eliminasi-Gauss/SPL_Eliminasi_Gauss.ipynb)

### 02. Persamaan Nonlinear — Metode Bisection

Implementasi metode Bisection untuk menentukan pendekatan akar persamaan nonlinear satu variabel.

**Cakupan pembahasan:**
- Pendefinisian fungsi nonlinear.
- Penentuan interval awal.
- Pemeriksaan perubahan tanda fungsi.
- Perhitungan titik tengah interval.
- Pembaruan interval pencarian.
- Proses iterasi berdasarkan toleransi.
- Evaluasi hasil pendekatan akar.

**Contoh fungsi:**

$$
f(x) = x^3 + 2x - 7
$$

**Files:**
- [Algoritma Bisection](03-SPNL-Bisection/algoritma_bisection.md)
- [Python Notebook — Bisection](03-SPNL-Bisection/Bisection_Nonlinear.ipynb)

> Note: Metode Bisection standar digunakan untuk mencari akar persamaan nonlinear satu variabel. Metode ini tidak secara langsung menyelesaikan sistem nonlinear multivariabel.

---

## Repository Structure

```text
Komputasi-Numerik/
│
├── README.md
│
├── 01-Identitas/
│   └── tautan_akun.txt
│
├── 02-SPL-Eliminasi-Gauss/
│   ├── algoritma_spl.md
│   └── SPL_Eliminasi_Gauss.ipynb
│
├── 03-SPNL-Bisection/
│   ├── algoritma_bisection.md
│   └── Bisection_Nonlinear.ipynb
│
├── 04-Prompt-AI/
│   └── prompt_ai.txt
│
└── 05-Video-Presentasi/
    ├── penjelasan_spl.mp4
    └── penjelasan_bisection.mp4
```

## Technologies

| Technology | Purpose |
|---|---|
| Python | Numerical algorithm implementation |
| NumPy | Matrix and numerical operations |
| Google Colab | Cloud-based Python execution |
| GitHub | Version control and project documentation |
| Markdown | Algorithm and technical documentation |

## Learning Objectives

Melalui proyek ini, pembelajaran difokuskan pada:

1. Memahami konsep dasar komputasi numerik.
2. Menerjemahkan permasalahan matematika menjadi algoritma.
3. Mengimplementasikan metode numerik menggunakan Python.
4. Menganalisis proses dan hasil perhitungan.
5. Mengembangkan dokumentasi teknis dan pengelolaan proyek menggunakan GitHub.

## Project Information

| Information | Details |
|---|---|
| Student | Muhammad Fahmi Amrulloh |
| Student ID | 202511420045 |
| Study Program | Teknik Informatika |
| Project | Komputasi Numerik |
| Academic Year | 2026 |

## Documentation & Portfolio

- **GitHub Repository:** [FamsGit/Komputasi-Numerik](https://github.com/FamsGit/Komputasi-Numerik)
- **LinkedIn:** [Muhammad Fahmi Amrulloh](https://www.linkedin.com/in/fahmi-amrul/)
- **Google Colab:** Notebook tersedia melalui direktori proyek masing-masing.

## Disclaimer

This repository is developed for academic and educational purposes. The implementations are intended to demonstrate the fundamental concepts and practical application of numerical methods using Python.

---

<p align="center">
  <strong>LEARN • COMPUTE • ANALYZE • INNOVATE</strong>
  <br>
  <sub>Numerical Computation Project — Informatics Engineering</sub>
</p>
