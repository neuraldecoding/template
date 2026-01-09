# Template Dokumen Ujian Kualifikasi S3
**Program Studi Doktor Informatika - Universitas Telkom**

Template LaTeX ini telah disesuaikan untuk memenuhi standar format Ujian Kualifikasi.

## 📁 Struktur File
- `Template-Ujian-Kualifikasi-DJN.tex` : File utama LaTeX.
- `references.bib` : File database referensi (BibTeX).
- `logo-telkom.png` : Logo universitas (wajib ada).
- `compile-latex.ps1` : Script PowerShell untuk kompilasi otomatis.

## 🚀 Cara Kompilasi (Build)
Untuk menghasilkan PDF yang lengkap dengan Daftar Pustaka, Daftar Isi, Daftar Tabel, Daftar Gambar, dan Daftar Rumus yang benar, Anda harus menjalankan perintah berikut secara berurutan:

### Menggunakan Script PowerShell (Windows) - **Direkomendasikan**
```powershell
.\compile-latex.ps1
```

Script ini akan otomatis menjalankan semua tahapan kompilasi (pdflatex → bibtex → pdflatex × 2) dan menampilkan informasi hasil kompilasi.

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
Ubah data berikut di bagian awal file `.tex` (sekitar baris 198-200):
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
1. Buka file `references.bib`.
2. Tambahkan entri referensi baru (format BibTeX).
3. Di dalam teks (`.tex`), panggil referensi menggunakan:
   - `\parencite{key}` untuk hasil `(Author, 2024)`
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
