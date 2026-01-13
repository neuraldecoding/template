# Template Dokumen Ujian Kualifikasi S3
**Program Studi Doktor Informatika - Universitas Telkom**

Template LaTeX ini telah disesuaikan untuk memenuhi standar format Ujian Kualifikasi.

## 📁 Struktur File
- `kualifikasi.tex` : File utama LaTeX.
- `references.bib`, `all.bib`, `visual.bib`, `transeeg.bib` : File database referensi (BibTeX).
- `logo-telkom.png` : Logo universitas (wajib ada).
- `compile-latex.ps1` : Script PowerShell untuk kompilasi otomatis.
- `chapters/` : Direktori berisi file-file bab (bab1.tex, bab2.tex, bab3.tex, ringkasan.tex, lampiran.tex).

## 📦 Instalasi Package LaTeX

Template ini memerlukan beberapa package LaTeX yang harus diinstall terlebih dahulu. Gunakan **TeX Live Manager (tlmgr)** untuk instalasi.

### Instalasi Otomatis (Semua Package Sekaligus)
```bash
tlmgr install mathptmx psnfss courier helvet amsmath babel geometry setspace titlesec graphicx hyperref booktabs array caption enumitem parskip fancyhdr tocloft tabularx longtable ragged2e biblatex logreq bibtex
```

### Instalasi Manual (Per Package)
Jika instalasi otomatis gagal, install satu per satu:

```bash
# Font packages
tlmgr install mathptmx psnfss courier helvet

# Math and language
tlmgr install amsmath babel

# Page layout and formatting
tlmgr install geometry setspace titlesec parskip

# Graphics and figures
tlmgr install graphicx

# Hyperlinks and references
tlmgr install hyperref

# Tables
tlmgr install booktabs array tabularx longtable

# Captions and lists
tlmgr install caption enumitem tocloft

# Headers and footers
tlmgr install fancyhdr

# Text formatting
tlmgr install ragged2e

# Bibliography (BibLaTeX)
tlmgr install biblatex logreq bibtex
```

### Verifikasi Instalasi
Setelah instalasi, verifikasi dengan:
```bash
tlmgr list --only-installed | grep -E "(mathptmx|biblatex|longtable|ragged2e)"
```

### Catatan untuk TinyTeX
Jika menggunakan TinyTeX, package akan otomatis terinstall saat kompilasi pertama kali. Pastikan koneksi internet aktif.

## 🚀 Cara Kompilasi (Build)
Untuk menghasilkan PDF yang lengkap dengan Daftar Pustaka, Daftar Isi, Daftar Tabel, Daftar Gambar, dan Daftar Rumus yang benar, Anda harus menjalankan perintah berikut secara berurutan:

### Menggunakan Script PowerShell (Windows) - **Direkomendasikan**
```powershell
.\compile-latex.ps1
```

Script ini akan otomatis menjalankan semua tahapan kompilasi (pdflatex → bibtex → pdflatex × 2) dan menampilkan informasi hasil kompilasi.

### Menggunakan Terminal / Command Prompt
```bash
pdflatex kualifikasi.tex
bibtex kualifikasi
pdflatex kualifikasi.tex
pdflatex kualifikasi.tex
```

### Menggunakan Editor LaTeX (TexMaker, TeXStudio, Overleaf)
Biasanya cukup menekan tombol **Build** atau **Compile**. Pastikan konfigurasi editor menggunakan urutan: `PDFLaTeX -> BibTeX -> PDFLaTeX -> PDFLaTeX`.

## 📝 Panduan Penggunaan

### 1. Data Diri & Judul
Ubah data berikut di bagian awal file `.tex` (sekitar baris 236-239):
```latex
\myTitle{Judul Disertasi Anda}
\myNIM{303012510004}
\myName{Rolly Maulana Awangga}
\myYear{2026}
```

### 2. Menulis Konten
Konten disertasi diorganisir dalam direktori `chapters/`:
- **Ringkasan**: Edit file `chapters/ringkasan.tex`
- **Pendahuluan**: Edit file `chapters/bab1.tex`
- **Literature Review**: Edit file `chapters/bab2.tex`
- **Teori/Metode Terkait**: Edit file `chapters/bab3.tex`
- **Lampiran**: Edit file `chapters/lampiran.tex`

### 3. Menambahkan Tabel
Gunakan environment `table` dengan `\caption{}`:
```latex
\begin{table}[htbp]
    \centering
    \caption{Judul Tabel Anda}
    \label{tab:nama_label}
    \begin{tabular}{...}
        % isi tabel
    \end{tabular}
\end{table}
```

Tabel akan otomatis muncul di **DAFTAR TABEL** setelah kompilasi.

### 4. Menambahkan Gambar
Gunakan environment `figure` dengan `\caption{}`:
```latex
\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.5\textwidth]{nama_file.png}
    \caption{Judul Gambar Anda}
    \label{fig:nama_label}
\end{figure}
```

Gambar akan otomatis muncul di **DAFTAR GAMBAR** setelah kompilasi.

### 5. Menambahkan Rumus/Persamaan
Gunakan environment `equation` dengan `\myequations{}`:
```latex
\begin{equation}
    E = mc^2
    \label{eq:einstein}
\end{equation}
\myequations{Persamaan Einstein}
```

**Penting**: Command `\myequations{deskripsi}` wajib ditambahkan setelah `\end{equation}` agar rumus muncul di **DAFTAR RUMUS**.

### 6. Tabel State-of-the-Art
Gunakan format `tabularx` yang sudah disediakan.
- Tambahkan baris baru dengan format:
  ```latex
  No & \textcite{kunci_referensi} & Tujuan & Metode & Hasil \\ \addlinespace
  ```
- Gunakan `\addlinespace` antar baris agar lebih rapi.

### 7. Menambahkan Referensi
1. Buka file bibliography yang sesuai:
   - `references.bib` - Referensi umum
   - `all.bib` - Semua referensi
   - `visual.bib` - Referensi terkait visual
   - `transeeg.bib` - Referensi terkait EEG
2. Tambahkan entri referensi baru (format BibTeX).
3. Di dalam teks (`.tex`), panggil referensi menggunakan:
   - `\cite{key}` atau `\parencite{key}` untuk hasil `(Author, 2024)`
   - `\textcite{key}` untuk hasil `Author (2024)`

### 8. Format Sitasi
Template ini sudah diatur otomatis menghasilkan format:
- **Style**: (Author, Year)
- **Pemisah**: Tanda koma (,)
- **Penghubung**: Simbol Ampersand (&)
- **Warna**: Hitam

## 📋 Daftar-Daftar yang Tersedia
Template ini secara otomatis menghasilkan:
1. **DAFTAR ISI** - Daftar semua section dan subsection
2. **DAFTAR TABEL** - Daftar semua tabel yang memiliki `\caption{}`
3. **DAFTAR GAMBAR** - Daftar semua gambar yang memiliki `\caption{}`
4. **DAFTAR RUMUS** - Daftar semua rumus yang memiliki `\myequations{}`

Semua daftar akan terisi otomatis setelah kompilasi 2-3 kali.

## ⚠️ Troubleshooting
- **Error "Language indonesian not found"**: Abaikan saja jika PDF tetap ter-generate. Ini warning minor dari package biblatex.
- **Tanda Tanya (?) pada referensi**: Jalankan `bibtex` lalu `pdflatex` 2x lagi.
- **Judul Daftar Isi bukan "DAFTAR ISI"**: Pastikan perintah `\renewcommand{\contentsname}{DAFTAR ISI}` tetap ada setelah `\begin{document}`.
- **Daftar masih kosong**: Jalankan pdflatex minimal 2-3 kali untuk memperbarui semua daftar.
- **Script PowerShell error**: Gunakan `powershell -ExecutionPolicy Bypass -File compile-latex.ps1`.

## 📄 Lisensi
Template ini didistribusikan di bawah lisensi **GNU General Public License v3.0** (GPLv3). Lihat file LICENSE untuk informasi lebih lanjut.
