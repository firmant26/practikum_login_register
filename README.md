# JUDUL		    : APLIKASI LOGIN & REGISTRASI SEDERHANA(FLUTTER)
# MATA KULIAH	: PEMROGRAMAN PERANGKAT BERGERAK
# NAMA		    : MOCH. FIRMAN TRISWANDA
# NIM			    : 362458302013
# KELAS		    : 2B TRPL
# TANGGAL		  : 15 SEPTEMBER 2025

**1. PENDAHULUAN**
**1.1 Latar Belakang**
Di era aplikasi mobile sekarang, hampir semua layanan memerlukan akun agar data pengguna aman dan pengalaman bisa dipersonalisasi. Praktikum ini mengajarkan konsep dasar membuat halaman masuk (login) dan pendaftaran (register) menggunakan Flutter, skill yang penting buat bikin aplikasi nyata.
**1.2 Tujuan Praktikum**
Tujuan praktikum ini antara lain:
  - Membuat tampilan antarmuka untuk halaman login dan registrasi.
  - Menguasai penggunaan widget dasar Flutter (mis. Scaffold, TextField, ElevatedButton).
  - Mempelajari navigasi antar layar dengan Navigator.
  - Menyimpan input pengguna sementara di memori program.
  - Memahami apa yang terjadi saat tombol diklik (event handling).
**1.3 Alat dan Bahan**
  - Flutter SDK
  - Android Studio atau VS Code (dengan plugin Flutter)
  - Emulator Android/iOS atau perangkat fisik untuk uji coba

**2. DESAIN & KONSEP (WIREFRAME)**
**2.1 Wireframe Halaman Login**
Halaman login berisi: ikon/app title, input email, input password, tombol Login, dan link menuju halaman registrasi. Tujuannya sederhana: alur masuk cepat dan jelas.
**2.2 Wireframe Halaman Registrasi**
Halaman registrasi berisi: input nama lengkap, email, password, tombol Register, dan link untuk kembali ke halaman login. Desain dibuat simpel supaya pengguna mudah mengisi data.

**3. IMPLEMENTASI & PEMBAHASAN**
**3.1 Struktur Proyek**
Struktur folder yang dipakai:
<img width="163" height="162" alt="image" src="https://github.com/user-attachments/assets/8fc52f32-1b28-4775-b44c-11f1ccb66e98" />
user_data.dart berfungsi sebagai penyimpanan sementara (mirip database sederhana).
**3.2 Penjelasan Kode Penting**
main.dart
	File ini adalah titik awal program (runApp). Di sini juga diatur tema dasar aplikasi dan halaman awal (login).
data/user_data.dart
	Menyimpan data pengguna dalam Map dengan format: email -> { fullName, password }. Data ini hanya sementara selama aplikasi jalan (tidak persist ke storage).
register_page.dart
	Halaman untuk mendaftarkan akun baru. Langkah kerjanya: ambil input nama/email/password, cek apakah semua terisi, lalu simpan ke userData. Jika berhasil, tampilkan dialog sukses dan kembali ke halaman login. Kalau kosong, tampilkan dialog error.
login_page.dart
	Halaman untuk autentikasi. Ketika tombol login ditekan, aplikasi mengecek apakah email ada di userData dan password cocok. Kalau benar, navigasi ke HomePage sambil mengirim fullName. Kalau salah, muncul dialog “Login Gagal”.
home_page.dart
	Halaman setelah login menampilkan salam dan nama pengguna. Terdapat tombol logout yang mengembalikan user ke halaman login dan menghapus riwayat navigasi agar tidak bisa kembali dengan tombol back.
**3.3 Hal-hal Teknis yang Perlu Diperhatikan**
  - Gunakan TextEditingController untuk membaca nilai input.
  - Untuk password gunakan obscureText: true.
  - Navigasi antar halaman memakai Navigator.push, Navigator.pop, dan Navigator.pushReplacement sesuai kebutuhan.
  - Penyimpanan saat ini masih volatile (pakai Map); kalau mau persist gunakan shared_preferences atau database.

**4. HASIL PENGUJIAN**
**4.1 Langkah Uji Coba**
  1. Tampilan halaman Login.
     <img width="496" height="792" alt="image" src="https://github.com/user-attachments/assets/d187007c-add5-4ea5-8053-e08239eb10f9" />
  2. Pilih Sign Up, kemudian isi nama/email/password → tekan Register.
     <img width="496" height="830" alt="image" src="https://github.com/user-attachments/assets/b65ae1cd-1b1b-46e9-bef7-8577f3eced11" />
     <img width="496" height="802" alt="image" src="https://github.com/user-attachments/assets/c325d2d4-d567-4604-ac78-777e00360eac" />
  3. Kembali ke Login, lalu masukkan email/password yang didaftarkan → tekan Login.
     <img width="494" height="777" alt="image" src="https://github.com/user-attachments/assets/f89bed29-8f45-4c74-8e05-2fc4997ee69d" />
  4. Jika semua benar, aplikasi menampilkan halaman Home dengan nama lengkap.
     <img width="495" height="745" alt="image" src="https://github.com/user-attachments/assets/458a04be-6ecc-40aa-a410-27e220974e4b" />
**4.2 Latihan untuk Eksplorasi Lebih Lanjut**
  1. Validasi Input: Tambahkan validasi yang lebih baik. Misalnya, cek apakah email
  memiliki format yang benar (mengandung ’@’) atau password memiliki panjang
  minimal 6 karakter.
  SOURCE CODE:
  (register_page.dart)
  <img width="1426" height="1422" alt="image" src="https://github.com/user-attachments/assets/695e1ca4-2413-4417-8956-88a2220f7cd1" />
  DISPLAY:
  Ketika Email tidak mengandung '@'.
  <img width="495" height="794" alt="image" src="https://github.com/user-attachments/assets/073a7e4b-918e-4046-9dd4-9446f10e54ec" />
  Ketika Password tidak memiliki panjang minimal 6 karakter.
  <img width="499" height="811" alt="image" src="https://github.com/user-attachments/assets/67aa5654-5bf9-40ba-a91c-46d41c6fd4a0" />
  2. Tampilkan/Sembunyikan Password: Tambahkan ikon mata pada TextField password yang bisa ditekan untuk menampilkan atau menyembunyikan teks password.
  SOURCE CODE:
  <img width="1332" height="1348" alt="image" src="https://github.com/user-attachments/assets/548483eb-f5ed-464e-8c32-f292ade729d0" />
  DISPLAY:
  Ketika menampilkan password
  <img width="494" height="752" alt="image" src="https://github.com/user-attachments/assets/3ee4b81a-dfea-45fb-a22a-677828c3821f" />
  Ketika menyembunyikan password
  <img width="497" height="796" alt="image" src="https://github.com/user-attachments/assets/0b3ea0a1-0441-4ecc-a1a0-8e1cb9de3daa" />
  3. Animasi Sederhana: Tambahkan Hero widget pada ikon di halaman login dan registrasi agar ada transisi animasi yang halus.
  SOURCE CODE(register_page.dart):
  <img width="996" height="678" alt="image" src="https://github.com/user-attachments/assets/27723319-d4b0-4f3c-852d-292f8eada418" />
  4. Simpan Sesi Login: Coba gunakan package shared_preferences untuk menyimpan status login. Jadi, saat aplikasi ditutup dan dibuka lagi, pengguna tidak perlu login ulang jika sesinya masih aktif.
  SOURCE CODE:
  (puspec.yaml)
  <img width="742" height="528" alt="image" src="https://github.com/user-attachments/assets/5e8b420a-1383-403f-8091-6ffd9207a6d2" />
  (login_page.dart)
  <img width="1426" height="1088" alt="image" src="https://github.com/user-attachments/assets/668a9768-b7e6-4e33-b0db-487bafaf746b" />

**5. KESIMPULAN**
Praktikum ini berhasil menunjukkan cara membuat UI dasar untuk login dan registrasi di Flutter. Navigasi antar layar dan pengiriman data antar halaman berhasil diterapkan. Penyimpanan data menggunakan Map bekerja untuk demonstrasi, tetapi tidak aman untuk aplikasi sesungguhnya.

**6. DAFTAR PUSTAKA**
  - Modul Praktikum Flutter    : Pembuatan Form Login & Registrasi (2025)
  - Dokumentasi resmi Flutter  : https://docs.flutter.dev  
