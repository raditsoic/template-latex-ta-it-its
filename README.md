# Template LaTeX Tugas Akhir – Departemen Teknologi Informasi ITS

Template ini merupakan adaptasi dari template LaTeX resmi tugas akhir ITS yang dikembangkan oleh **B201 Telematics Laboratory** (repositori asli: `b201lab/template-buku-ta-its`). Versi ini telah disesuaikan untuk kebutuhan Departemen Teknologi Informasi ITS, dengan penyesuaian struktur, berkas, serta penambahan beberapa varian template (proposal & laporan akhir, Bahasa Indonesia & Bahasa Inggris).

## Struktur Template

Repositori ini menggunakan pendekatan core + variants, sehingga bagian yang sama untuk semua template hanya ada satu kali (dalam folder `core/`), sementara file yang berbeda untuk tiap versi berada di `variants/`.

```bash
/
├── LICENSE
├── README.md
├── core/                 # Komponen bagian
│   ├── abstrak/
│   ├── bab/
│   ├── gambar/
│   ├── lainnya/
│   ├── program/
│   ├── pustaka/
│   └── sampul/
└── variants/             # Varian template
    ├── proposal-id/
    ├── proposal-en/
    ├── final-id/
    └── final-en/
```

**Penjelasan Singkat Folder**

- `core/` — Isi template utama (struktur bab, gaya, sampul, variabel, dll.).
- `variants/` — Berisi override dan main.tex versi khusus, misalnya:
- `proposal-id` → Proposal Bahasa Indonesia
- `final-en` → Laporan akhir Bahasa Inggris

## Cara Menggunakan Template

Bagian utama dokumen terletak pada file [`main.tex`](./main.tex) yang digunakan untuk mengatur package LaTeX yang digunakan serta file lain yang akan diinputkan pada dokumen.
Setelah kompilasi dilakukan, hasilnya akan ada beberapa file `main` dengan format yang berbeda.
Yang terutama adalah file `main.pdf` yang merupakan hasil akhir dari proses kompilasi dokumen.

Selain file `main.tex`, ada juga beberapa bagian lain dari template ini yang bisa diubah, seperti:

- **[`abstrak`](./abstrak)**, berisi file `*.tex` untuk abstrak dalam Bahasa Indonesia dan Bahasa Inggris.
- **[`bab`](./bab)**, berisi file `*.tex` dari setiap bab yang akan dimasukkan pada buku tugas akhir.
- **[`gambar`](./gambar)**, berisi file `*.jpg`, `*.png`, maupun format gambar lain yang akan dimasukkan pada buku tugas akhir.
- **[`lainnya`](./lainnya)**, berisi file `*.tex` dari halaman lain seperti lembar pengesahan, kata pengantar, biografi penulis, dsb. yang akan dimasukkan pada buku tugas akhir.
- **[`program`](./program)**, berisi file kode program yang akan dimasukkan pada dokumen.
- **[`pustaka/pustaka.bib`](./pustaka/pustaka.bib)**, berisi daftar pustaka yang akan dimasukkan pada dokumen.
- **[`pustaka/variables.tex`](./pustaka/variables.tex)**, berisi variabel-variabel yang memuat nama, nrp, dan hal-hal lain yang dapat disesuaikan dengan kebutuhan penulis.
- **[`sampul`](./sampul)**, berisi file `*.tex` dari sampul luar dan dalam untuk buku tugas akhir.

> Penjelasan lebih lanjut mengenai penggunaan template ini akan dijelaskan dengan comment yang tersedia pada setiap file yang ada.


## Lisensi

Kode sumber yang ada pada repositori ini dilisensikan di bawah [lisensi MIT](./LICENSE) dengan kredit penuh kepada B201 Telematics Laboratory untuk template dasar.