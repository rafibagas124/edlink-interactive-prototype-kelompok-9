# Laporan Prototipe Interaktif SEVIMA EdLink

Dokumentasi ini disusun untuk memenuhi **Assignment 3: Interactive Prototyping** pada mata kuliah **Interaksi Manusia dan Komputer (Kode Mata Kuliah: SIN63122)**, Program Studi Sistem Informasi / Informatika, Fakultas Teknologi Komunikasi dan Informatika, **Jakarta Global University**.

---

## 1. Identitas Penyusun

Penyusunan prototipe interaktif dan dokumentasi evaluasi ini dilakukan oleh **Kelompok 9**:

| No | Nama Mahasiswa | Nomor Induk Mahasiswa (NIM) | Peran dan Tanggung Jawab |
| :---: | :--- | :---: | :--- |
| 1 | Rafi Bagas Naufally | 092024090195 | Perancangan Antarmuka Pengguna dan Rekayasa Kode Prototipe Frontend |
| 2 | Panji Widagdo | 092024090212 | Analisis Evaluasi Heuristik, Pengujian Aksesibilitas, dan Traceability Audit |

---

## 2. Deskripsi dan Tujuan Proyek

Proyek ini menghadirkan sebuah prototipe interaktif berbasis web (single-file HTML) yang menyimulasikan perbaikan alur pengumpulan tugas pada aplikasi mobile SEVIMA EdLink, khususnya pengumpulan berkas melalui integrasi Google Drive. 

Prototipe ini dirancang berdasarkan hasil audit evaluasi heuristik dan pengujian aksesibilitas yang telah disusun pada Tugas 2. Tujuannya adalah memvalidasi efektivitas solusi desain antarmuka dalam mengatasi kendala transparansi status, pencegahan kesalahan pemilihan berkas, kejelasan pesan kegagalan jaringan, serta kepatuhan kontras visual berdasarkan standar Web Content Accessibility Guidelines (WCAG 2.2 Level AAA).

---

## 3. Struktur Layar dan State Interaktif

Alur antarmuka prototipe mencakup enam state layar utama yang terhubung secara interaktif:

### Layar S1: Tentang Tugas (Assignment Detail)
Menampilkan informasi rincian tugas kuliah (*Assignment 3 - Interactive Prototyping*, Kelompok 9, tenggat waktu pengumpulan 19 November 2026 pukul 10.30 WIB). Ketika pengguna menekan tombol *Tambahkan Jawaban (Max 10 MB)*, sistem menampilkan lembar bawah (*bottom sheet*) yang secara eksplisit membedakan jalur pengumpulan berkas fisik (*Lampirkan File: PDF, DOCX, Gambar batas 10 MB*) dan tautan daring (*Teks Editor*).

### Layar S2: Media Library (Google Drive Integration)
Menampilkan daftar berkas mahasiswa pada penyimpanan Google Drive. Layar ini memuat pernyataan privasi eksplisit (*"EdLink hanya membaca berkas yang Anda pilih"*), daftar berkas dummy, dan berkas target `Tugas3_Prototype_Kelompok9.pdf (1.8 MB)` yang dapat dipilih langsung oleh pengguna.

### Layar S3: Proses Upload (Dynamic Progress)
Menampilkan visualisasi proses pengunggahan berkas secara bertahap dan dinamis (*"Mengunggah berkas... 60%"*) menggantikan teks statis. Pada layar ini disediakan tombol kendali simulasi untuk menguji skenario sukses (*Lanjut Sukses*) atau skenario gangguan koneksi (*Simulasi Koneksi Terputus*).

### Layar S6: Error and Recovery State
State penanganan kesalahan yang aktif ketika proses pengunggahan terputus. Sistem memberikan umpan balik eksplisit: *"Gagal dikirim: koneksi terputus. Berkas tersimpan otomatis sebagai draf lokal."* Pengguna dapat memilih tombol *Coba Lagi* untuk langsung melanjutkan proses dari draf yang tersimpan tanpa perlu memilih ulang berkas dari awal.

### Layar S4: Preview and Submit
Menampilkan pratinjau lembar pertama dokumen PDF sebelum dikirim agar mahasiswa dapat memverifikasi isi berkas. Layar ini dilengkapi tombol *Ganti Berkas* dengan target sentuh aman (minimal 44 x 44 piksel), tombol utama *Kirim Tugas*, serta *Dialog Konfirmasi Final* yang menampilkan ringkasan berkas, ukuran, dan jaminan bahwa berkas masih dapat diubah sebelum batas waktu.

### Layar S5: Submission Confirmed
Tanda terima digital resmi yang menyatakan tugas berhasil dikirim sebelum tenggat (*"Sudah Dikumpulkan pada 19 Nov 2026 pukul 10.12 WIB"*), dilengkapi nomor pengenal unik (*ID Pengiriman: #EDL-4F2A9C*), tombol *Lihat Berkas*, tombol *Ganti Berkas*, dan tombol *Hapus Jawaban* yang disertai dialog konfirmasi pembatalan.

---

## 4. Matriks Pemenuhan Rekomendasi Audit Tugas 2

Setiap elemen antarmuka pada prototipe ini terhubung langsung dengan kode temuan audit pada Tugas 2:

| Kode Temuan | Parameter Evaluasi | Implementasi Solusi Desain pada Prototipe |
| :---: | :--- | :--- |
| **ACC01** | Rasio Kontras Warna Teks | Teks sekunder menggunakan kode warna `#595555` pada latar belakang putih, menghasilkan rasio kontras 7.35:1 yang melampaui ambang batas minimum WCAG 2.2 Level AAA (7:1). |
| **ACC02** | Ketepatan Umpan Balik Waktu | Tanda terima pada Layar S5 menyajikan waktu pengiriman secara presisi (tanggal, jam, dan menit pengumpulan) sehingga mahasiswa memiliki bukti kepatuhan tenggat waktu. |
| **ACC03** | Indikator Status Dinamis | Layar S3 menyajikan persentase kemajuan unggah secara numerik dan baris progresif aktif, menggantikan teks statis "Mohon tunggu". |
| **ACC04** | Dimensi Target Sentuh | Tombol aksi mikro (seperti tombol *Ganti Berkas* dan tombol navigasi) dirancang dengan area sentuh minimal 44 x 44 piksel guna meminimalkan kesalahan sentuh pada perangkat layar sentuh. |
| **INC01** | Kejelasan Pesan Kesalahan | Layar S6 menyajikan pesan kegagalan yang konstruktif dan menginformasikan bahwa berkas telah diamankan sebagai draf lokal. |
| **INC02** | Adaptasi Pencahayaan Luar Ruangan | Prototipe menyediakan mode kontras tinggi (*High Contrast Mode*) untuk menjamin keterbacaan antarmuka di bawah sinar matahari langsung. |
| **INC03** | Pemisahan Jalur Masukan | Pembeda masukan pada Layar S1 memperjelas batasan kapasitas unggah file fisik (maksimal 10 MB) dibandingkan opsi tautan URL teks editor. |
| **RES01** | Pencegahan Kesalahan Berkas | Layar S4 menyajikan visualisasi pratinjau dokumen PDF dan dialog konfirmasi ganda sebelum eksekusi pengiriman final. |
| **RES02** | Transparansi Hak Akses Data | Menampilkan pernyataan privasi bahwa EdLink hanya memiliki hak baca terhadap dokumen yang dipilih secara eksplisit oleh pengguna. |
| **RES03** | Validitas Bukti Transaksi | Menghasilkan kode identifikasi pengiriman unik (#EDL-4F2A9C) yang dapat disalin sebagai bukti sah penyerahan tugas akademik. |
| **RES04** | Efisiensi Alur Pemulihan | Mekanisme *Coba Lagi* pada Layar S6 memanfaatkan data draf lokal sehingga mahasiswa tidak perlu mengulang tahapan pemilihan berkas dari Google Drive. |
| **RES05** | Aksesibilitas Pembatalan Tindakan | Menyediakan opsi pembatalan yang jelas di setiap titik transisi (pembatalan unggah, pembatalan pengiriman, dan penarikan tugas). |
| **RES06** | Penegakan Batas Waktu Otomatis | Sistem mengunci tombol *Ganti Berkas* dan *Hapus Jawaban* pada Layar S5 secara otomatis apabila simulasi tenggat waktu berakhir diaktifkan. |
| **F-05** | Penerapan Hukum Fitts | Tombol *Batal / Ganti Berkas* dan tombol *Kirim Sekarang* pada dialog konfirmasi dipisahkan dengan jarak yang cukup untuk mencegah ketidaksengajaan klik. |

---

## 5. Petunjuk Penggunaan Prototipe

Antarmuka prototipe terdiri atas dua area kerja utama:
1. **Bingkai Ponsel Cerdas (Pusat Layar)**: Mensimulasikan pengalaman pengguna saat mengoperasikan aplikasi mobile SEVIMA EdLink. Seluruh tombol, kartu berkas, tautan navigasi, dan kotak dialog di dalam bingkai ini dapat diklik secara interaktif.
2. **Panel Kontrol Simulasi (Sisi Kiri Desktop)**: Disediakan khusus untuk kebutuhan pengujian penguji/dosen serta demonstrasi video:
   - **Lompat Cepat Layar (S1 sampai S6)**: Tombol pintas untuk berpindah antar-state secara instan.
   - **Mode Kontras Tinggi (INC02)**: Mengalihkan tema antarmuka ponsel ke gaya monokrom dengan kontras maksimal.
   - **Tenggat Waktu Berakhir (RES06)**: Menguji perilaku sistem ketika batas waktu tugas telah habis, yang secara otomatis mengunci opsi pengubahan dan penghapusan pada Layar S5.
   - **Reset Prototipe**: Mengembalikan seluruh variabel status, data berkas, dan posisi layar ke kondisi awal (Layar S1).
   - **Katalog Rekomendasi IMK**: Menampilkan deskripsi otomatis dari temuan audit yang relevan dengan layar yang sedang aktif.

---

## 6. Petunjuk Menjalankan Aplikasi dan Deployment

### Menjalankan Secara Lokal
Prototipe ini merupakan aplikasi web statis berbasis HTML5, Tailwind CSS (CDN), dan Lucide Icons tanpa memerlukan proses kompilasi (*zero-build*).

Gunakan salah satu perintah berikut pada terminal di dalam folder proyek:
- Menggunakan Python:
  ```bash
  python -m http.server 8080
  ```
- Menggunakan Node.js:
  ```bash
  npx serve -l 8080 .
  ```
Akses aplikasi melalui peramban web pada alamat: `http://localhost:8080/index.html`.

### Deployment ke Vercel
Karena berkas utama telah dinamai `index.html` dan diletakkan pada direktori root, proyek ini siap di-deploy langsung ke Vercel:
1. Hubungkan repositori Git ini ke akun GitHub.
2. Buka dashboard Vercel, pilih *Import Project*, dan arahkan ke repositori ini.
3. Tetapkan *Framework Preset* pada opsi *Other* dan *Root Directory* pada `./`.
4. Tekan *Deploy* untuk mempublikasikan prototipe secara daring.
