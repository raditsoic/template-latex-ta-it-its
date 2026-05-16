# Template LaTeX Tugas Akhir – Departemen Teknologi Informasi ITS

Template ini merupakan adaptasi dari template LaTeX resmi tugas akhir ITS yang dikembangkan oleh **B201 Telematics Laboratory** (repositori asli: `b201lab/template-buku-ta-its`). Versi ini telah disesuaikan untuk kebutuhan Departemen Teknologi Informasi ITS, dengan penyesuaian struktur, berkas, serta penambahan struktur untuk Proposal dan Buku Tugas Akhir.

---

## Daftar Isi

- [Quick Start](#quick-start)
- [Struktur Template](#struktur-template)
- [Instalasi](#instalasi)
- [VSCode Setup](#vscode-setup)
- [Cara Menggunakan Template](#cara-menggunakan-template)
- [Kompilasi Dokumen](#kompilasi-dokumen)
- [Varian Template](#varian-template)
- [Development Workflow](#development-workflow)
- [Reference Folder](#reference-folder)
- [Troubleshooting](#troubleshooting)
- [Kontribusi](#kontribusi)
- [Issue & Feature Request](#issue--feature-request)
- [Lisensi](#lisensi)

---

## Quick Start

Jika Kamu ingin langsung memulai tanpa membaca dokumentasi lengkap:

### 1. Clone Repository

```bash
git clone <repository-url>
cd template-latex-ta-it-its
```

### 2. Setup LaTeX (Pilih salah satu)

**Windows (MiKTeX):**

- Download dan install dari https://miktex.org/download
- Saat setup, pilih "Install missing packages on-the-fly"

**Linux (Ubuntu/Debian):**

```bash
sudo apt install texlive texlive-latex-extra texlive-fonts-extra biber
```

**macOS:**

```bash
brew install basictex
sudo tlmgr update --all
sudo tlmgr install biber latexmk
```

### 3. Setup VSCode (Windows)

```bash
# Copy template settings
cp .vscode/settings.local.json.example .vscode/settings.local.json

# Edit .vscode/settings.local.json dan ganti <YOUR_USERNAME> dengan username Windows Kamu
```

### 4. Edit Metadata

Buka `core/pustaka/variables.tex` dan update informasi pribadi:

```tex
\newcommand{\name}{Nama Lengkap Kamu}
\newcommand{\nrp}{5025 21 XXXX}
\newcommand{\tatitle}{Judul Tugas Akhir Kamu}
```

### 5. Mulai Menulis

- Edit file di `core/chapter/` untuk konten
- Edit file di `core/abstrak/` untuk abstrak
- Simpan gambar di `core/gambar/`

### 6. Compile

Buka `variants/buku-ta/main.tex` atau `variants/proposal/main.tex` di VSCode, tekan `Ctrl+Alt+B` untuk compile, atau gunakan:

```bash
cd variants/buku-ta
latexmk -pdf main.tex
```

---

## Struktur Template

Repositori ini menggunakan pendekatan **core + variants**, sehingga bagian yang sama untuk semua template hanya ada satu kali (dalam folder `core/`), sementara file yang berbeda untuk tiap versi berada di `variants/`.

```bash
/
├── LICENSE
├── README.md
├── .gitignore
├── .vscode/              # Konfigurasi VS Code (LaTeX Workshop)
│   ├── settings.json                          # Konfigurasi global (shared)
│   └── settings.local.json.example            # Template untuk konfigurasi lokal
├── core/                 # Komponen inti yang dibagikan ke semua varian
│   ├── abstrak/          # Abstrak Bahasa Indonesia dan Inggris
│   ├── chapter/          # Bab-bab tugas akhir (1-5)
│   ├── gambar/           # Direktori untuk gambar/ilustrasi
│   ├── lainnya/          # Halaman tambahan (pengesahan, kata pengantar, dll.)
│   ├── program/          # Kode program yang akan disisipkan
│   ├── pustaka/          # Daftar pustaka (pustaka.bib) dan variabel konfigurasi (variables.tex)
│   └── sampul/           # Template sampul dalam dan luar beserta gambar
├── variants/             # Varian template untuk berbagai kebutuhan
│   ├── buku-ta/          # Buku Tugas Akhir (Laporan Akhir lengkap)
│   └── proposal/         # Proposal Tugas Akhir
└── reference/            # File referensi (PDF thesis, template, dll.) - tracked by git
```

### Penjelasan Folder `core/`

| Folder         | Deskripsi                                                                                                                                                                                                                                                                        |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`abstrak/`** | Berisi file `*.tex` untuk abstrak dalam Bahasa Indonesia (`abstrak-id.tex`) dan Bahasa Inggris (`abstrak-en.tex`)                                                                                                                                                                |
| **`chapter/`** | Berisi file `*.tex` dari setiap bab:<br/>• `1-pendahuluan.tex` — Pendahuluan<br/>• `2-tinjauan-pustaka.tex` — Tinjauan pustaka<br/>• `3-metodologi.tex` — Metodologi<br/>• `4-hasil-pembahasan.tex` — Hasil dan pembahasan<br/>• `5-kesimpulan-saran.tex` — Kesimpulan dan saran |
| **`gambar/`**  | Direktori untuk menyimpan file gambar (`*.jpg`, `*.png`, `*.pdf`, dll.) yang akan digunakan dalam dokumen. Pastikan nama file sederhana tanpa spasi                                                                                                                              |
| **`lainnya/`** | Halaman tambahan seperti lembar pengesahan (TA & proposal), kata pengantar, pernyataan keaslian, biografi penulis                                                                                                                                                                |
| **`program/`** | File kode program yang akan disisipkan ke dalam dokumen menggunakan package listings (contoh: `*.py`, `*.java`, `*.cpp`)                                                                                                                                                         |
| **`pustaka/`** | • `pustaka.bib` — Daftar referensi dalam format BibTeX<br/>• `variables.tex` — Konfigurasi metadata (nama, NIM, dosen, judul, dll.)                                                                                                                                              |
| **`sampul/`**  | Template sampul luar, dalam, dan tipis beserta konten cover (Bahasa Indonesia & Inggris), plus folder `gambar/` untuk menyimpan cover image                                                                                                                                      |

### Penjelasan Folder `variants/`

Setiap varian memiliki file `main.tex` sendiri yang mengatur struktur dokumen sesuai kebutuhan:

- **`buku-ta/`** — Buku Tugas Akhir (Laporan Akhir lengkap dengan Bab 1-5)
- **`proposal/`** — Proposal Tugas Akhir (hanya Bab 1-3: Pendahuluan, Tinjauan Pustaka, Metodologi)

---

## Instalasi

Sebelum menggunakan template ini, Kamu perlu menginstal distribusi LaTeX yang sesuai dengan sistem operasi Kamu.

### Windows (MiKTeX) — Rekomendasi untuk User Windows

1. Download MiKTeX installer dari https://miktex.org/download
2. Jalankan installer dan pilih:
   - **Installation scope**: "Just for me" atau "For all users"
   - **Preferred paper**: "A4"
   - **Install missing packages on-the-fly**: **Pilih YES** (penting untuk auto-download packages)
3. Setelah instalasi selesai, pastikan `biber` terinstall:
   ```bash
   biber --version
   ```

Dengan pengaturan ini, Kamu tidak perlu secara manual mengunduh package yang hilang.

### macOS

```bash
# Install using Homebrew
brew install basictex

# Update TeX packages
sudo tlmgr update --all

# Install additional required packages
sudo tlmgr install \
  latexmk \
  biber \
  xetex \
  babel-indonesian
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
  biber latexmk
```

### Arch Linux

```bash
sudo pacman -S texlive-basic texlive-bin texlive-latex \
  texlive-latexrecommended texlive-fontsrecommended \
  texlive-xetex texlive-luatex texlive-pictures \
  texlive-publishers texlive-science texlive-binextra \
  texlive-latexextra biber
```

## Cara Menggunakan Template

### 1. Pilih Varian Template

Pilih varian yang sesuai dengan kebutuhan Kamu:

- **`variants/buku-ta/`** — Untuk buku tugas akhir (laporan akhir lengkap)
- **`variants/proposal/`** — Untuk proposal tugas akhir

### 2. Konfigurasi Template (Format Halaman)

Template sudah dikonfigurasi dengan **twoside (double-sided printing)** sesuai **panduan institusi ITS**:

**Panduan Resmi ITS:**
> Buku TA dicetak bolak-balik (untuk menghemat kertas), namun pastikan awal bab ada di halaman gasal.
> Buku TA cukup diberi klip.

**Format Saat Ini:**

Kedua varian template (`buku-ta/` dan `proposal/`) menggunakan twoside dengan konfigurasi:

```tex
\documentclass[12pt,twoside]{report}
\usepackage[a4paper,top=30mm,inner=30mm,outer=20mm,bottom=25mm,twoside]{geometry}
```

**Karakteristik twoside:**
- ✅ Cetak dua sisi dengan margin bergantian (inner=binding side, outer=free side)
- ✅ Halaman kosong ditambahkan otomatis agar chapter dimulai di halaman gasal (kanan)
- ✅ Page numbering bergantian (genap di kiri, ganjil di kanan)
- ✅ Cukup diberi klip (tidak perlu binding mahal)

**Mengubah ke Oneside:**

Jika ingin mengubah ke format single-sided, edit file `variants/buku-ta/main.tex` atau `variants/proposal/main.tex`:

```tex
% Ubah dari:
\documentclass[12pt,twoside]{report}
% Menjadi:
\documentclass[12pt,oneside]{report}

% Dan ubah geometry dari:
\usepackage[a4paper,top=30mm,inner=30mm,outer=20mm,bottom=25mm,twoside]{geometry}
% Menjadi:
\usepackage[a4paper,top=30mm,left=30mm,right=20mm,bottom=25mm]{geometry}
```

### 3. Konfigurasi Metadata Dokumen

Edit file **`core/pustaka/variables.tex`** untuk mengatur informasi pribadi dan dokumen:

```tex
% Nama dan identitas
\newcommand{\name}{Nama Lengkap Kamu}
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

## VSCode Setup

### Instalasi Extension

1. Buka VS Code
2. Pergi ke **Extensions** (Ctrl+Shift+X)
3. Cari dan install: **LaTeX Workshop** by James Yu

### Konfigurasi Settings

Repository ini sudah menyediakan konfigurasi LaTeX Workshop yang siap pakai. Ada dua file settings:

#### `settings.json` (Shared - tracked by git)

File ini berisi konfigurasi yang sama untuk semua user:

- Build recipes (Quick Build, Full Build)
- PDF viewer settings
- Format preferences

Semua orang di team akan mendapat pengaturan yang sama.

#### `settings.local.json` (User-specific - NOT tracked)

File ini untuk path lokal dan preferensi personal Kamu:

**Setup awal:**

```bash
# Windows: Copy template ke file lokal
copy .vscode\settings.local.json.example .vscode\settings.local.json

# macOS/Linux:
cp .vscode/settings.local.json.example .vscode/settings.local.json
```

**Edit `settings.local.json`:**

- **Windows**: Ganti `<YOUR_USERNAME>` dengan username Windows Kamu
- **macOS/Linux**: Ganti path sesuai output dari `which pdflatex` dan `which xelatex`

Contoh untuk Windows:

```json
{
    "latex-workshop.latex.tools": [
        {
            "name": "pdflatex",
            "command": "C:\\Users\\namakamu\\AppData\\Local\\Programs\\MiKTeX\\miktex\\bin\\x64\\pdflatex.exe",
            ...
        }
    ]
}
```

File `settings.local.json` sudah di-ignore oleh `.gitignore`, jadi tidak akan pernah ter-commit ke repository.

### Menggunakan LaTeX Workshop

**Compile:**

- Keyboard: `Ctrl+Alt+B` (Windows/Linux) atau `Cmd+Option+B` (macOS)
- Menu: Klik ikon LaTeX Workshop di sidebar, lalu klik ikon ▶️ di file editor

**View PDF:**

- Auto-open di tab saat compile berhasil
- Atau klik "View LaTeX PDF File" di VS Code

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

- **`main.pdf`** — Dokumen akhir (file utama yang Kamu butuhkan)
- `main.aux`, `main.bbl`, `main.blg`, `main.log`, dll. — File auxiliary (dapat diabaikan)

> 💡 **Tip**: Untuk membersihkan file auxiliary, jalankan:
>
> ```bash
> latexmk -c    # Hapus file temporary
> latexmk -C    # Hapus semua file hasil kompilasi termasuk PDF
> ```

---

## Varian Template

### Perbedaan Proposal dan Buku TA

| Aspek                   | Proposal                                            | Buku TA                                                       |
| ----------------------- | --------------------------------------------------- | ------------------------------------------------------------- |
| **Bab yang Disertakan** | Bab 1-3 (Pendahuluan, Tinjauan Pustaka, Metodologi) | Bab 1-5 (Semua bab termasuk Hasil dan Kesimpulan)             |
| **Lembar Pengesahan**   | Lembar pengesahan proposal (Indonesia & Inggris)    | Lembar pengesahan TA lengkap (Indonesia & Inggris)            |
| **Halaman Tambahan**    | Minimal (hanya yang diperlukan untuk proposal)      | Lengkap (kata pengantar, biografi, pernyataan keaslian, dll.) |
| **Daftar Pustaka**      | Ditampilkan di akhir proposal                       | Ditampilkan di akhir buku                                     |

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

## Development Workflow

### Branch Naming Convention

Untuk kolaborasi yang terstruktur, gunakan branch naming berikut:

| Prefix      | Deskripsi                           | Contoh                          |
| ----------- | ----------------------------------- | ------------------------------- |
| `feat/`     | Fitur baru                          | `feat/tambah-bibliography`      |
| `fix/`      | Bug fix                             | `fix/gambar-tidak-muncul`       |
| `docs/`     | Dokumentasi                         | `docs/update-readme`            |
| `refactor/` | Refactoring tanpa mengubah behavior | `refactor/restructure-chapters` |
| `chore/`    | Maintenance, tooling, config        | `chore/update-gitignore`        |

### Commit Message Guidelines

Gunakan format yang deskriptif:

```
<type>: <deskripsi singkat>

<deskripsi panjang (opsional)>

Fixes #123 (jika applicable)
```

Contoh:

```
feat: add chapter 4 content and results discussion

- Add analysis of experimental results
- Include performance comparison tables
- Update figure references

Relates to #15
```

### Git Workflow untuk Kontributor

1. Fork repositori
2. Clone fork Kamu: `git clone https://github.com/your-username/template-latex-ta-it-its.git`
3. Buat branch fitur: `git checkout -b feat/deskripsi-fitur`
4. Commit perubahan dengan pesan yang deskriptif
5. Push ke branch: `git push origin feat/deskripsi-fitur`
6. Buka Pull Request ke branch `main`

---

## Reference Folder

Folder `reference/` digunakan untuk menyimpan file referensi dan contoh yang berguna untuk pengembangan template.

### Isi Reference Folder

| File               | Deskripsi                                                           |
| ------------------ | ------------------------------------------------------------------- |
| **PDF Thesis**     | Contoh thesis yang sudah jadi sebagai referensi format dan struktur |
| **Template Files** | File template alternatif atau backup                                |
| **Documentation**  | Dokumentasi tambahan tentang template ITS                           |

### Menambahkan File Referensi

1. Letakkan file di folder `reference/`
2. File akan otomatis di-track oleh git (folder ini adalah exception dari `.gitignore`)
3. Gunakan nama file yang deskriptif: `judul-thesis-nama-author-tahun.pdf`

### Git Tracking untuk Reference

Folder `reference/` memiliki exception khusus di `.gitignore`:

```
# Exception: track reference files
!reference/
!reference/**
```

Ini memastikan file di folder `reference/` tetap ter-track meskipun memiliki format `.pdf`, `.docx`, dll.

---

## Kontribusi

Kontribusi dalam bentuk **pull request** sangat diterima! 🎉

### Langkah-Langkah Berkontribusi

Lihat bagian [Development Workflow](#development-workflow) untuk:

- **Branch naming convention** — Gunakan prefix yang sesuai (`feat/`, `fix/`, `docs/`, dll.)
- **Commit message guidelines** — Tulis commit message yang deskriptif dan informatif
- **Git workflow** — Step-by-step untuk fork, branch, dan PR

### Hal-Hal yang Dihargai dalam Kontribusi

- ✅ Perbaikan dokumentasi dan README
- ✅ Bug fixes dengan explanation yang jelas
- ✅ Improvement pada template structure
- ✅ Penambahan contoh dan referensi
- ✅ Perbaikan compatibility di berbagai OS
- ✅ Translation ke bahasa lain

### Sebelum Membuka PR

1. Pastikan branch Kamu up-to-date dengan `main`
2. Test compile dengan baik (gunakan `latexmk -pdf main.tex`)
3. Review PR Kamu sendiri sebelum submit
4. Deskripsi PR dengan jelas tentang perubahan yang dilakukan

---

## Issue & Feature Request

Jika Kamu menemukan **bug** atau memiliki **permintaan fitur**, silakan buka issue di repositori GitHub ini dengan:

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
