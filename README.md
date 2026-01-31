# Martin Node.js Egg

## Deskripsi
Egg untuk Pterodactyl Panel yang mendukung aplikasi Node.js versi 1 sampai 24. Dibuat oleh Martin untuk menyediakan lingkungan yang kompatibel dengan berbagai versi Node.js.

## Fitur
- Dukungan Node.js versi 1 hingga 24
- Otomatis instalasi dependensi npm
- Integrasi dengan Git untuk clone repository
- Mendukung package-lock.json dan yarn.lock
- Optimasi untuk versi Node.js lama dan baru

## Cara Penggunaan

### Instalasi Otomatis dari Git
1. Isi variabel `GIT_ADDRESS` dengan URL repository Git Anda
2. Atur `BRANCH` jika menggunakan branch selain default
3. Untuk repository privat, isi `USERNAME` dan `ACCESS_TOKEN`
4. Egg akan secara otomatis meng-clone repository dan menginstal dependensi

### Upload Manual
1. Set variabel `USER_UPLOAD` ke `true` atau `1`
2. Upload file aplikasi Anda melalui file manager atau SFTP
3. Dependensi akan diinstal saat server dimulai

### Variabel Startup
- `STARTUPSCRIPT`: Perintah untuk menjalankan aplikasi (default: `node main.js`)
- `NODE_PACKAGES`: Paket npm tambahan yang ingin diinstal secara global (pisahkan dengan spasi)

## Variabel Lingkungan

| Variabel | Deskripsi | Default |
|----------|-----------|---------|
| STARTUPSCRIPT | Perintah untuk menjalankan aplikasi Node.js | `node main.js` |
| NODE_PACKAGES | Paket npm tambahan untuk diinstal secara global | (kosong) |
| GIT_ADDRESS | URL repository Git | (kosong) |
| BRANCH | Branch Git yang akan di-clone | (kosong) |
| USERNAME | Username Git untuk repository privat | (kosong) |
| ACCESS_TOKEN | Token akses Git untuk repository privat | (kosong) |
| USER_UPLOAD | Mode upload manual | `false` |

## Catatan
- Egg ini menggunakan image Docker dari ghcr.io/parkervcp/yolks
- Untuk versi Node.js di bawah 4, akan digunakan metode instalasi legacy
- File package.json diperlukan untuk instalasi dependensi otomatis
- Server akan otomatis menjalankan `npm install` jika folder node_modules tidak ditemukan
