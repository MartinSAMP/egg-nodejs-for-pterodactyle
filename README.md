# Martin Node.js Egg

## Deskripsi
Egg untuk Pterodactyl Panel yang mendukung aplikasi Node.js versi 1 sampai 24. Dibuat oleh Martin untuk menyediakan lingkungan yang kompatibel dengan berbagai versi Node.js, dengan dukungan TypeScript, auto-update dari Git, dan manajemen paket yang fleksibel.

## Fitur
- ✅ Dukungan Node.js versi 1 hingga 24
- ✅ Dukungan TypeScript (otomatis deteksi .ts atau .js)
- ✅ Auto Update - Pull otomatis dari Git saat startup
- ✅ Instalasi & Uninstall paket npm dinamis
- ✅ Integrasi dengan Git untuk clone repository
- ✅ Mendukung package-lock.json dan yarn.lock
- ✅ Optimasi untuk versi Node.js lama dan baru
- ✅ Dukungan repository Git privat dengan autentikasi

## Cara Penggunaan

### Instalasi Otomatis dari Git
1. Isi variabel **Git Repo Address** dengan URL repository Git Anda (contoh: `https://github.com/username/repo`)
2. Atur **Install Branch** jika menggunakan branch selain default (contoh: `main`, `dev`)
3. Untuk repository privat, isi **Git Username** dan **Git Access Token**
4. Aktifkan **Auto Update** (`1` atau `true`) jika ingin otomatis pull terbaru saat startup
5. Egg akan secara otomatis meng-clone repository dan menginstal dependensi

### Upload Manual
1. Set variabel **User Uploaded Files** ke `1` atau `true`
2. Upload file aplikasi Anda melalui file manager atau SFTP
3. Pastikan file `package.json` ada jika memerlukan dependensi
4. Dependensi akan diinstal saat server dimulai

### Konfigurasi File Utama
- Isi **Main file** dengan path file utama Anda:
  - Untuk JavaScript: `src/index.js` atau `main.js`
  - Untuk TypeScript: `src/index.ts` atau `app.ts`
- Sistem otomatis mendeteksi ekstensi dan menggunakan `node` untuk .js atau `ts-node --esm` untuk .ts
- Tambahkan **Node Arguments** untuk argumen tambahan (contoh: `--port=3000 --env=production`)

### Manajemen Paket Tambahan
- **Additional Node packages**: Install paket tambahan saat startup (pisahkan dengan spasi, contoh: `express lodash moment`)
- **Uninstall Node packages**: Hapus paket yang tidak diperlukan (pisahkan dengan spasi, contoh: `old-package deprecated-lib`)

## Variabel Lingkungan

| Variabel | Deskripsi | Default | Contoh |
|----------|-----------|---------|--------|
| GIT_ADDRESS | URL repository Git untuk di-clone | (kosong) | `https://github.com/user/repo` |
| BRANCH | Branch Git yang akan di-clone | (kosong) | `main`, `develop` |
| USER_UPLOAD | Lewati instalasi otomatis jika upload manual | `0` | `0` (false) / `1` (true) |
| AUTO_UPDATE | Pull otomatis dari Git saat startup | `0` | `0` (false) / `1` (true) |
| NODE_PACKAGES | Paket npm tambahan untuk diinstal | (kosong) | `express dotenv cors` |
| UNNODE_PACKAGES | Paket npm yang akan di-uninstall | (kosong) | `old-package unused-lib` |
| USERNAME | Username Git untuk repository privat | (kosong) | `your-username` |
| ACCESS_TOKEN | Personal Access Token Git | (kosong) | `ghp_xxxxxxxxxxxx` |
| MAIN_FILE | File utama aplikasi | `src/index.js` | `app.js`, `src/server.ts` |
| NODE_ARGS | Argumen tambahan untuk Node.js | (kosong) | `--max-old-space-size=512` |

## Docker Images Tersedia
Egg ini mendukung berbagai versi Node.js melalui image Docker dari `ghcr.io/parkervcp/yolks`:
- Node.js 1 hingga 24 tersedia
- Pilih versi yang sesuai dengan kebutuhan aplikasi Anda
- Versi default: Node.js 20

## Catatan Penting
- Egg ini menggunakan image Docker dari `ghcr.io/parkervcp/yolks`
- Untuk versi Node.js di bawah 4, akan digunakan metode instalasi legacy (`--legacy-bundling`)
- File `package.json` diperlukan untuk instalasi dependensi otomatis
- Untuk TypeScript, pastikan `ts-node` terinstal atau gunakan versi Node.js yang mendukung ESM
- Auto Update hanya berfungsi jika repository di-clone melalui Git (bukan upload manual)
- Git Access Token direkomendasikan daripada password untuk keamanan yang lebih baik

## Troubleshooting
- **Instalasi gagal**: Periksa apakah `GIT_ADDRESS` valid dan repository tidak privat tanpa autentikasi
- **Module not found**: Pastikan `NODE_PACKAGES` berisi semua dependensi yang diperlukan atau `package.json` lengkap
- **TypeScript error**: Pastikan file `.ts` dan gunakan versi Node.js yang mendukung ESM (14+)
- **Auto update tidak berfungsi**: Pastikan `AUTO_UPDATE=1` dan server di-start dari repository Git (bukan upload manual)

## Kontak
Dibuat oleh: Martin (martinyy09@gmail.com)
