# Template LaTeX Tugas Akhir – Departemen Teknologi Informasi ITS

Template ini merupakan adaptasi dari template LaTeX resmi tugas akhir ITS yang dikembangkan oleh **B201 Telematics Laboratory** (repositori asli: `b201lab/template-buku-ta-its`). Versi ini telah disesuaikan untuk kebutuhan Departemen Teknologi Informasi ITS, dengan penyesuaian struktur, berkas, serta penambahan struktur untuk Proposal dan Buku Tugas Akhir.

---

## Daftar Isi

- [Struktur Template](#struktur-template)
- [Instalasi](#instalasi)
- [Cara Menggunakan Template](#cara-menggunakan-template)
- [Kompilasi Dokumen](#kompilasi-dokumen)
- [Varian Template](#varian-template)
- [Troubleshooting](#troubleshooting)
- [Kontribusi](#kontribusi)
- [Issue & Feature Request](#issue--feature-request)
- [Lisensi](#lisensi)

---

## Struktur Template

Repositori ini menggunakan pendekatan **core + variants**, sehingga bagian yang sama untuk semua template hanya ada satu kali (dalam folder `core/`), sementara file yang berbeda untuk tiap versi berada di `variants/`.

```bash
/
├── LICENSE
├── README.md
├── .vscode/              # Konfigurasi VS Code (LaTeX Workshop)
│   └── settings.json
├── core/                 # Komponen inti yang dibagikan ke semua varian
│   ├── abstrak/          # Abstrak Bahasa Indonesia dan Inggris
│   ├── chapter/          # Bab-bab tugas akhir
│   ├── gambar/           # Direktori untuk gambar/ilustrasi
│   ├── lainnya/          # Halaman tambahan (pengesahan, kata pengantar, dll.)
│   ├── program/          # Kode program yang akan disisipkan
│   ├── pustaka/          # Daftar pustaka dan variabel konfigurasi
│   └── sampul/           # Template sampul dalam dan luar
└── variants/             # Varian template untuk berbagai kebutuhan
    ├── buku-ta/          # Buku Tugas Akhir (Laporan Akhir lengkap)
    └── proposal/          # Proposal Tugas Akhir
```

### Penjelasan Folder `core/`

| Folder | Deskripsi |
|--------|-----------|
| **`abstrak/`** | Berisi file `*.tex` untuk abstrak dalam Bahasa Indonesia (`abstrak-id.tex`) dan Bahasa Inggris (`abstrak-en.tex`) |
| **`chapter/`** | Berisi file `*.tex` dari setiap bab (1-pendahuluan.tex, 2-tinjauan-pustaka.tex, dll.) |
| **`gambar/`** | Direktori untuk menyimpan file gambar (`*.jpg`, `*.png`, `*.pdf`, dll.) yang akan digunakan dalam dokumen |
| **`lainnya/`** | Halaman tambahan seperti lembar pengesahan (TA & proposal), kata pengantar, pernyataan keaslian, biografi penulis |
| **`program/`** | File kode program yang akan disisipkan ke dalam dokumen menggunakan package listings |
| **`pustaka/`** | Berisi `pustaka.bib` (daftar referensi) dan `variables.tex` (konfigurasi metadata) |
| **`sampul/`** | Template sampul luar, dalam, dan tipis beserta konten cover (Bahasa Indonesia & Inggris) |

### Penjelasan Folder `variants/`

Setiap varian memiliki file `main.tex` sendiri yang mengatur struktur dokumen sesuai kebutuhan:

- **`buku-ta/`** — Buku Tugas Akhir (Laporan Akhir lengkap dengan Bab 1-5)
- **`proposal/`** — Proposal Tugas Akhir (hanya Bab 1-3: Pendahuluan, Tinjauan Pustaka, Metodologi)

---

## Instalasi

Sebelum menggunakan template ini, Anda perlu menginstal distribusi LaTeX yang sesuai dengan sistem operasi Anda.

### Arch Linux

```bash
sudo pacman -S texlive-basic texlive-bin texlive-latex \
  texlive-latexrecommended texlive-fontsrecommended \
  texlive-xetex texlive-luatex texlive-pictures \
  texlive-publishers texlive-science texlive-binextra \
  texlive-latexextra
```

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install \
  texlive \
  texlive-base \
  texlive-latex-base \
  texlive-latex-recommended \
  texlive-fonts-recommended \
  texlive-xetex \
  texlive-luatex \
  texlive-pictures \
  texlive-publishers \
  texlive-science \
  texlive-latex-extra \
  texlive-extra-utils \
  texlive-bibtex-extra \
  biber
```

## Cara Menggunakan Template

### 1. Pilih Varian Template

Pilih varian yang sesuai dengan kebutuhan Anda:

- **`variants/buku-ta/`** — Untuk buku tugas akhir (laporan akhir lengkap)
- **`variants/proposal/`** — Untuk proposal tugas akhir

### 2. Konfigurasi Metadata Dokumen

Edit file **`core/pustaka/variables.tex`** untuk mengatur informasi pribadi dan dokumen:

```tex
% Nama dan identitas
\newcommand{\name}{Nama Lengkap Anda}
\newcommand{\nrp}{5025 21 XXXX}
\newcommand{\advisor}{Nama Dosen Pembimbing, S.T., M.T}
\newcommand{\coadvisor}{Nama Dosen Co-Pembimbing, S.T., M.T}

% Judul
\newcommand{\tatitle}{Judul Tugas Akhir Bahasa Indonesia}
\newcommand{\engtatitle}{Final Project Title in English}

% Kata kunci
\newcommand{\keywords}{kata kunci, penelitian, topik}

% Dan konfigurasi lainnya...
```

### 3. Isi Konten Dokumen

#### a. **Abstrak**
Edit file di `core/abstrak/`:
- `abstrak-id.tex` — Abstrak dalam Bahasa Indonesia
- `abstrak-en.tex` — Abstrak dalam Bahasa Inggris

#### b. **Bab-Bab**
Edit file di `core/chapter/` sesuai struktur buku:
- `1-pendahuluan.tex` — Latar belakang, rumusan masalah, tujuan, manfaat
- `2-tinjauan-pustaka.tex` — Teori dan penelitian terdahulu
- `3-metodologi.tex` — Metodologi penelitian
- `4-hasil-pembahasan.tex` — Hasil dan pembahasan
- `5-kesimpulan-saran.tex` — Kesimpulan dan saran

#### c. **Gambar**
Simpan file gambar di `core/gambar/` dan gunakan dalam dokumen:

```tex
\begin{figure}[H]
  \centering
  \includegraphics[width=0.8\textwidth]{gambar/nama-file.png}
  \caption{Deskripsi gambar}
  \label{fig:label-gambar}
\end{figure}
```

#### d. **Kode Program**
Simpan file kode di `core/program/` dan sisipkan dalam dokumen:

```tex
\lstinputlisting[language=Python, caption=Deskripsi kode]{program/nama-file.py}
```

#### e. **Daftar Pustaka**
Tambahkan referensi ke `core/pustaka/pustaka.bib` dalam format BibTeX:

```bibtex
@article{AuthorYear,
  author  = {Nama Penulis},
  title   = {Judul Artikel},
  journal = {Nama Jurnal},
  year    = {2024},
  volume  = {10},
  pages   = {1--10}
}
```

Sitasi dalam dokumen menggunakan `\parencite{AuthorYear}` atau `\textcite{AuthorYear}`.

#### f. **Halaman Tambahan**
Edit file di `core/lainnya/`:
- `lembar-pengesahan.tex` / `lembar-pengesahan-en.tex` — Lembar pengesahan TA
- `lembar-pengesahan-proposal.tex` / `lembar-pengesahan-proposal-en.tex` — Lembar pengesahan proposal
- `kata-pengantar.tex` — Kata pengantar
- `biografi-penulis.tex` — Biografi penulis
- `pernyataan-keaslian.tex` / `pernyataan-keaslian-en.tex` — Pernyataan keaslian

> 💡 **Tip**: Setiap file dilengkapi dengan comment yang menjelaskan cara penggunaan dan kustomisasi.

---

## Kompilasi Dokumen

### Metode 1: Menggunakan `pdflatex`

Navigasi ke folder varian yang diinginkan, kemudian jalankan perintah berikut:

```bash
# Masuk ke folder varian, contoh: proposal
cd variants/proposal/

# Kompilasi dokumen (jalankan beberapa kali untuk referensi silang)
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

**Penjelasan:**
1. `pdflatex main.tex` — Kompilasi pertama untuk membuat struktur dokumen
2. `biber main` — Memproses daftar pustaka
3. `pdflatex main.tex` — Kompilasi kedua untuk menyisipkan referensi
4. `pdflatex main.tex` — Kompilasi ketiga untuk finalisasi

### Metode 2: Menggunakan `latexmk` 

`latexmk` akan otomatis menjalankan kompilasi berulang hingga semua referensi terselesaikan:

```bash
cd variants/proposal/
latexmk -pdf main.tex
```

Untuk mengaktifkan mode watch (auto-compile saat file berubah):

```bash
latexmk -pdf -pvc main.tex
```

### Metode 3: Menggunakan VS Code dengan LaTeX Workshop

1. Install extension **LaTeX Workshop** di VS Code
2. Buka file `main.tex` dari varian yang diinginkan
3. Tekan `Ctrl+Alt+B` (Linux/Windows) atau `Cmd+Option+B` (macOS) untuk compile
4. Atau klik ikon ▶️ di pojok kanan atas editor

### Output Kompilasi

Setelah kompilasi berhasil, akan dihasilkan:
- **`main.pdf`** — Dokumen akhir (file utama yang Anda butuhkan)
- `main.aux`, `main.bbl`, `main.blg`, `main.log`, dll. — File auxiliary (dapat diabaikan)

> 💡 **Tip**: Untuk membersihkan file auxiliary, jalankan:
> ```bash
> latexmk -c    # Hapus file temporary
> latexmk -C    # Hapus semua file hasil kompilasi termasuk PDF
> ```

---

## Varian Template

### Perbedaan Proposal dan Buku TA

| Aspek | Proposal | Buku TA |
|-------|----------|------------------|
| **Bab yang Disertakan** | Bab 1-3 (Pendahuluan, Tinjauan Pustaka, Metodologi) | Bab 1-5 (Semua bab termasuk Hasil dan Kesimpulan) |
| **Lembar Pengesahan** | Lembar pengesahan proposal (Indonesia & Inggris) | Lembar pengesahan TA lengkap (Indonesia & Inggris) |
| **Halaman Tambahan** | Minimal (hanya yang diperlukan untuk proposal) | Lengkap (kata pengantar, biografi, pernyataan keaslian, dll.) |
| **Daftar Pustaka** | Ditampilkan di akhir proposal | Ditampilkan di akhir buku |

---

## Troubleshooting

### Error: `! LaTeX Error: File 'xxx.sty' not found`

**Solusi**: Package LaTeX belum terinstal. Jalankan:

```bash
# Ubuntu/Debian
sudo apt install texlive-latex-extra texlive-fonts-extra

# Arch Linux
sudo pacman -S texlive-latexextra

# MiKTeX (Windows) - akan otomatis mengunduh package yang hilang
```

### Error: `! Package biblatex Error: '\biber' not found`

**Solusi**: Install biber untuk memproses bibliografi:

```bash
# Ubuntu/Debian
sudo apt install biber

# Arch Linux
sudo pacman -S biber

# macOS
brew install biber
```

### Referensi/Citation Tidak Muncul

**Solusi**: Pastikan menjalankan kompilasi lengkap:

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

Atau gunakan `latexmk -pdf main.tex` yang otomatis menangani ini.

### Gambar Tidak Muncul

**Penyebab umum:**
1. Path file gambar salah → Pastikan file ada di `core/gambar/`
2. Format gambar tidak didukung → Gunakan `.png`, `.jpg`, atau `.pdf`
3. Package `graphicx` belum dimuat → Sudah included di template

### Error: Font Tidak Ditemukan

**Solusi**: Install font Times New Roman atau gunakan `txfonts` (sudah included):

```bash
# Ubuntu/Debian
sudo apt install texlive-fonts-recommended texlive-fonts-extra

# Arch Linux
sudo pacman -S texlive-fontsrecommended
```

---

## Kontribusi

Kontribusi dalam bentuk **pull request** sangat diterima. Jika Anda ingin berkontribusi:

1. Fork repositori ini
2. Buat branch fitur baru (`git checkout -b fitur-baru`)
3. Commit perubahan Anda (`git commit -m 'Tambah fitur baru'`)
4. Push ke branch Anda (`git push origin fitur-baru`)
5. Buka Pull Request

---

## Issue & Feature Request

Jika Anda menemukan **bug** atau memiliki **permintaan fitur**, silakan buka issue di repositori GitHub ini dengan:

### Untuk Bug Report
- Judul yang jelas dan ringkas
- Deskripsi detail tentang bug
- Langkah-langkah untuk mereproduksi bug
- Screenshot/log error (jika ada)
- Informasi sistem operasi dan versi LaTeX

### Untuk Feature Request
- Judul yang menggambarkan fitur yang diminta
- Deskripsi detail tentang fitur yang diinginkan
- Alasan/masalah yang ingin diselesaikan dengan fitur tersebut
- Contoh penggunaan (jika relevan)

---

## Lisensi

Kode sumber yang ada pada repositori ini dilisensikan di bawah [Lisensi MIT](./LICENSE) dengan kredit penuh kepada **B201 Telematics Laboratory** untuk template dasar.