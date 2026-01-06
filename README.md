# Template Dokumen Ujian Kualifikasi S3
**Program Studi Doktor Informatika - Universitas Telkom**

Template LaTeX ini telah disesuaikan untuk memenuhi standar format Ujian Kualifikasi.

## 📁 Struktur File
- `Template-Ujian-Kualifikasi-DJN.tex` : File utama LaTeX.
- `references.bib` : File database referensi (BibTeX).
- `logo-telkom.png` : Logo universitas (wajib ada).

## 🚀 Cara Kompilasi (Build)
Untuk menghasilkan PDF yang lengkap dengan Daftar Pustaka dan Daftar Isi yang benar, Anda harus menjalankan perintah berikut secara berurutan:

### Menggunakan Terminal / Command Prompt
```bash
pdflatex Template-Ujian-Kualifikasi-DJN.tex
bibtex Template-Ujian-Kualifikasi-DJN
pdflatex Template-Ujian-Kualifikasi-DJN.tex
pdflatex Template-Ujian-Kualifikasi-DJN.tex
```

### Menggunakan Editor LaTeX (TexMaker, TeXStudio, Overleaf)
Biasanya cukup menekan tombol **Build** atau **Compile**. Pastikan konfigurasi editor menggunakan urutan: `PDFLaTeX -> BibTeX -> PDFLaTeX -> PDFLaTeX`.

## 📝 Panduan Penggunaan

### 1. Data Diri & Judul
Ubah data berikut di bagian awal file `.tex` (sekitar baris 160-an, sebelum `\begin{document}`):
```latex
\myTitle{JUDUL DISERTASI ANDA DI SINI}
\myNIM{1234567890}
\myName{Nama Lengkap Anda}
\myYear{2026}
```

### 2. Menulis Konten
- **Pendahuluan**: Edit di bawah section `BAB 1 PENDAHULUAN`.
- **Literature Review**: Edit di bawah section `BAB 2 LITERATURE REVIEW`.
- **Metodologi**: Edit di bawah section `BAB 3 TEORI / METODE TERKAIT`.

### 3. Tabel State-of-the-Art
Gunakan format `tabularx` yang sudah disediakan.
- Tambahkan baris baru dengan format:
  ```latex
  No & \textcite{kunci_referensi} & Tujuan & Metode & Hasil \\ \addlinespace
  ```
- Gunakan `\addlinespace` antar baris agar lebih rapi.

### 4. Menambahkan Referensi
1. Buka file `references.bib`.
2. Tambahkan entri referensi baru (format BibTeX).
3. Di dalam teks (`.tex`), panggil referensi menggunakan:
   - `\parencite{key}` untuk hasil `(Author, 2024)`
   - `\textcite{key}` untuk hasil `Author (2024)`

### 5. Format Sitasi
Template ini sudah diatur otomatis menghasilkan format:
- **Style**: (Author, Year)
- **Pemisah**: Tanda koma (,)
- **Penghubung**: Simbol Ampersand (&)
- **Warna**: Hitam

## ⚠️ Troubleshooting
- **Error "Language indonesian not found"**: Abaikan saja jika PDF tetap ter-generate. Ini warning minor dari package biblatex.
- **Tanda Tanya (?) pada referensi**: Jalankan `bibtex` lalu `pdflatex` 2x lagi.
- **Judul Daftar Isi bukan "DAFTAR ISI"**: Pastikan perintah `\renewcommand{\contentsname}{DAFTAR ISI}` tetap ada setelah `\begin{document}`.

##  Lisensi
Template ini didistribusikan di bawah lisensi **GNU General Public License v3.0** (GPLv3). Lihat file LICENSE untuk informasi lebih lanjut.
