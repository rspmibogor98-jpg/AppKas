# Aplikasi Pengelolaan Uang Kas — GitHub Pages

Aplikasi kas bersama: anggota, iuran per bulan, transaksi pemasukan/pengeluaran, laporan PDF/Excel, PIN Admin, backup/restore, dan opsional Firebase Firestore.

## Cara Deploy ke GitHub Pages (3 menit)

### Opsi A — Upload lewat web GitHub (paling gampang, tanpa install apa-apa)
1. Buka https://github.com/new — buat repo baru, misal `aplikasi-kas`
   - Pilih **Public**
   - Centang **Add a README file** (boleh tidak)
   - Klik **Create repository**
2. Di halaman repo, klik **Add file > Upload files**
3. Upload file `index.html` dari folder ini (drag & drop)
4. Klik **Commit changes**
5. Masuk ke **Settings > Pages**
   - **Build and deployment > Branch:** pilih `main` dan folder `/ (root)`
   - Klik **Save**
6. Tunggu 1-2 menit. Link jadi: `https://USERNAME.github.io/aplikasi-kas/`
   - Ganti `USERNAME` dengan username GitHub lu, dan `aplikasi-kas` dengan nama repo lu.

### Opsi B — Pakai Git di laptop
```bash
git clone https://github.com/USERNAME/aplikasi-kas.git
cd aplikasi-kas
# copy index.html ke sini
git add index.html
git commit -m "Deploy aplikasi kas"
git push origin main
```
Lalu aktifkan Pages seperti langkah 5 di atas.

## Cara Pakai
- **Login:** Admin (PIN default `1234`) bisa edit semua. User hanya lihat & laporan.
- **Home:** saldo, pemasukan, pengeluaran, ringkasan iuran bulan ini.
- **Iuran:** pilih bulan, klik "Tandai Lunas" — otomatis masuk ke Pemasukan.
- **Transaksi:** tambah pemasukan/pengeluaran.
- **Laporan:** filter Per Bulan / Multi Bulan / Tanggal Tertentu, lalu Download PDF / Excel (header sudah merge + lebar kolom auto).
- **Pengaturan:** ganti Nama Kas, Nilai Iuran, tambah/edit/hapus anggota, ganti/reset PIN, Backup/Restore JSON.
- **Firebase (opsional):** isi config di Pengaturan > Koneksi Firebase, centang "Gunakan Firebase", klik Simpan & Koneksikan, lalu **Sync Sekarang**.
  - Data tersimpan di Firestore: collection `kas_data` / doc `utama`.
  - Kalau muncul `permission-denied`, di Firebase Console > Firestore > Rules ganti jadi `allow read, write: if true;` lalu Publish.

## Catatan Penting
- Versi GitHub ini pakai **LocalStorage** browser + Firebase, bukan database bawaan Meta AI. Jadi kalau buka di HP lain / browser lain, datanya beda kecuali sudah konek Firebase yang sama.
- Untuk data bareng-bareng satu tim, **wajib** konek ke Firebase yang sama di semua HP.
- Jangan commit file backup `.json` yang berisi data asli ke repo Public kalau ada data sensitif.

## File
- `index.html` — satu file saja, semua fitur di dalamnya. Tidak perlu build / npm.
- `.nojekyll` — biar GitHub Pages tidak mengabaikan file yang diawali underscore.
