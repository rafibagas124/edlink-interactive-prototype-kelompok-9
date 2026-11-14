# SEVIMA EdLink Mobile — Interactive Clickable Prototype
> **Assignment 3 — Interaksi Manusia dan Komputer (SIN63122)**  
> **Program Studi Sistem Informasi / Informatika — Jakarta Global University (JGU)**

---

## 👥 Identitas Pengembang (Kelompok 9)

| Nama Anggota | NIM | Peran |
| :--- | :--- | :--- |
| **Rafi Bagas Naufally** | `092024090195` | UI/UX Designer & Frontend Prototype Engineer |
| **Panji Widagdo** | `092024090212` | HCI Researcher & Accessibility Auditor |

---

## 📱 Ringkasan Proyek

Repositori ini berisi **Interactive Clickable Prototype berbasis web** (single-file `index.html`) yang menyimulasikan redesain alur pengumpulan tugas pada aplikasi mobile **SEVIMA EdLink**, dengan fokus utama integrasi berkas dari **Google Drive**.

Prototipe ini dirancang sebagai artefak implementasi solusi dari temuan evaluasi heuristik dan audit aksesibilitas pada **Tugas 2 IMK**, menghadirkan antarmuka mobile berbingkai ponsel realistis dengan panel kontrol demonstrasi di sisi kiri untuk memudahkan pengujian akademik dan perekaman video demonstrasi.

---

## 🗺️ Alur Layar & State Interaktif (S1 s/d S6)

| State | Nama Layar | Deskripsi Interaksi Utama |
| :---: | :--- | :--- |
| **S1** | **Tentang Tugas (Assignment Detail)** | Menampilkan rincian tugas kuliah (*Assignment 3 - Interactive Prototyping*, Kelompok 9, tenggat waktu 19 Nov 2026 pukul 10.30 WIB). Saat tombol *"Tambahkan Jawaban"* diklik, muncul modal *Bottom Sheet* yang membedakan secara eksplisit jalur pengunggahan berkas fisik (*PDF/DOCX/Gambar maks 10 MB*) vs penyematan tautan URL teks editor. |
| **S2** | **Media Library (Google Drive)** | Menampilkan integrasi penyimpanan awan Google Drive yang dilengkapi pesan transparansi privasi (*"EdLink hanya membaca berkas yang Anda pilih"*), daftar berkas dummy mahasiswa, dan item sasaran yang dapat dipilih: `Tugas3_Prototype_Kelompok9.pdf (1.8 MB)`. |
| **S3** | **Proses Upload (Dynamic Progress)** | Menampilkan visualisasi pengunggahan berkas secara real-time dengan persentase bertahap (*"Mengunggah berkas... 60%"*) menggantikan teks statis. Dilengkapi tombol simulasi percabangan: *"Lanjut Sukses"* (ke S4) atau *"Simulasi Terputus"* (ke S6). |
| **S4** | **Preview & Submit** | Menampilkan pratinjau visual halaman 1 dokumen PDF laporan sebelum dikirim agar mahasiswa yakin berkas tidak tertukar, tombol *"Ganti Berkas"* dengan target sentuh ramah jari (≥ 44×44 px), tombol *"Kirim Tugas"*, serta **Dialog Konfirmasi Final** yang merinci nama berkas, ukuran, dan kebijakan pengubahan sebelum batas waktu. |
| **S5** | **Submission Confirmed** | Tanda terima pengiriman terverifikasi dengan badge hijau *"Sudah Dikumpulkan pada 19 Nov 2026 pukul 10.12 WIB"*, nomor ID Pengiriman unik (`#EDL-4F2A9C`), opsi *"Lihat Berkas"*, *"Ganti Berkas"*, serta tombol *"Hapus Jawaban"* yang disertai dialog konfirmasi pembatalan. |
| **S6** | **Error & Recovery State** | State pemulihan jika terjadi kegagalan jaringan internet saat upload. Menampilkan pesan kesalahan eksplisit: *"Gagal dikirim: koneksi terputus. Berkas tersimpan otomatis sebagai draf lokal"* dan tombol *"Coba Lagi"* yang memulihkan alur pengiriman tanpa perlu memilih berkas dari awal. |

---

## 🔍 Matriks Traceability Temuan Audit Tugas 2

Prototipe ini memvalidasi seluruh rekomendasi perbaikan dari temuan Tugas 2 IMK:

| Kode Temuan | Aspek Evaluasi | Implementasi Solusi pada Prototipe |
| :---: | :--- | :--- |
| **ACC01** | Aksesibilitas Warna & Kontras | Teks sekunder menggunakan warna `#595555` pada latar putih, menghasilkan rasio kontras **7.35:1** yang lolos kualifikasi **WCAG 2.2 Level AAA**. |
| **ACC02** | Kejelasan Bukti Penyerahan | Layar S5 mencantumkan tanggal, jam, dan menit pengumpulan secara eksplisit (*19 Nov 2026 pukul 10.12 WIB*) bukan sekadar label "Terkirim". |
| **ACC03** | Status Pengunggahan Real-Time | Layar S3 menggunakan progress bar dinamis dengan persentase aktif menggantikan label teks statis *"Mohon tunggu"*. |
| **ACC04** | Aksesibilitas Target Sentuh | Tombol navigasi dan aksi mikro (seperti tombol *Ganti Berkas*) memenuhi standar ukuran target sentuh interaktif minimum (≥ 24×24 px hingga 44×44 px). |
| **INC01** | Penanganan Kesalahan (Error Handling) | Pesan kegagalan koneksi di Layar S6 bersifat konstruktif dan informatif, serta menjamin berkas tersimpan aman sebagai draf offline. |
| **INC02** | Keterbacaan Luar Ruangan | Tersedia toggle *"Mode Kontras Tinggi"* pada panel simulasi untuk menguji keterbacaan antarmuka di bawah terik sinar matahari. |
| **INC03** | Kejelasan Jalur Input Berkas | Modal pemilihan metode pengumpulan memisahkan secara tegas antara unggah berkas fisik (kapasitas 10 MB) dan tautan teks editor URL. |
| **RES01** | Pencegahan Kesalahan Berkas | Lembar pratinjau visual PDF pada S4 dan dialog konfirmasi sebelum submit memastikan pengguna tidak salah memilih file. |
| **RES02** | Privasi & Transparansi Izin | Menampilkan deklarasi privasi eksplisit saat menghubungkan Google Drive: *"EdLink hanya membaca berkas yang Anda pilih"*. |
| **RES03** | Bukti Transaksi Unik | Memberikan kode referensi unik (`#EDL-4F2A9C`) sebagai tanda bukti sah pengumpulan tugas di server kampus. |
| **RES04** | Pemulihan Tanpa Redundansi | Fitur *Coba Lagi* dari draf lokal mencegah mahasiswa mengulang alur login dan pencarian file dari awal. |
| **RES05** | Aksesibilitas Pembatalan | Alur pembatalan pengunggahan dan penggantian berkas dapat diakses dengan mudah pada setiap tahapan layar. |
| **RES06** | Penguncian Otomatis Tenggat Waktu | Panel kontrol memiliki toggle *"Tenggat Waktu Berakhir"* yang secara otomatis mengunci dan menonaktifkan tombol *Ganti Berkas* & *Hapus Jawaban* pada S5. |
| **F-05** | Fitts's Law & Safety Margin | Tombol *Batal* dan *Kirim Sekarang* pada dialog konfirmasi dipisahkan dengan jarak aman untuk mencegah salah tekan (accidental tap). |

---

## 🛠️ Tumpukan Teknologi (Tech Stack)

- **HTML5**: Arsitektur Semantic Web & Single-File Application (`index.html`).
- **Tailwind CSS (CDN)**: Styling utilitas responsif, palet WCAG AAA, dan tata letak flex/grid.
- **Lucide Icons**: Library ikon vektor modern, tajam, dan konsisten.
- **Vanilla JavaScript (ES6+)**: Mesin state management ringan tanpa dependensi framework eksternal.

---

## 🚀 Cara Menjalankan Secara Lokal

Cukup jalankan server HTTP statis sederhana di folder proyek:

```bash
# Opsi 1: Menggunakan Python
python -m http.server 8080

# Opsi 2: Menggunakan Node.js / npx serve
npx serve -l 8080 .
```

Buka peramban web pada alamat:  
👉 **`http://localhost:8080/index.html`**

---

## ☁️ Panduan Deploy ke Vercel

Proyek ini telah dikonfigurasi sebagai **Static Web Application** standar tanpa memerlukan langkah *build* (`zero-config`).

### Cara 1: Menggunakan Git & Dashboard Vercel (Direkomendasikan)
1. Buat repositori baru di akun GitHub Anda (misal: `sevima-edlink-hci-prototype`).
2. Push commit lokal ke GitHub:
   ```bash
   git remote add origin https://github.com/<username>/sevima-edlink-hci-prototype.git
   git branch -M main
   git push -u origin main
   ```
3. Buka dashboard [Vercel](https://vercel.com/) dan klik **"Add New..."** → **"Project"**.
4. Import repositori GitHub tersebut.
5. Biarkan pengaturan default (*Framework Preset: Other*, *Root Directory: ./*), lalu klik **"Deploy"**.

### Cara 2: Menggunakan Vercel CLI Langsung
```bash
npx vercel --prod
```
Ikuti petunjuk di terminal untuk menghubungkan ke akun Vercel dan situs akan langsung aktif dalam hitungan detik.
