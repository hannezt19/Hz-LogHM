# Hz LogHM - LocBook V7.1

Heavy Equipment Log - aplikasi pencatatan HM, OT, dan BBM harian untuk sopir/operator di perkebunan tebu.

**Package Android:** `com.hz.logHM`
**Live web version:** https://hannezt19.github.io/Hz-LogHM/

## Struktur Proyek

| File/Folder | Fungsi |
|---|---|
| `index.html` | Aplikasi utama (satu file HTML+CSS+JS) |
| `manifest.json` | Konfigurasi PWA (nama, ikon, warna tema) |
| `sw.js` | Service worker untuk cache offline versi web |
| `icons/` | Ikon aplikasi (192px & 512px) |
| `capacitor.config.json` | Konfigurasi app native Capacitor |
| `package.json` | Daftar dependency Capacitor |
| `.github/workflows/build-android.yml` | Workflow otomatis build APK lewat GitHub Actions |
| `.nojekyll` | Penanda agar GitHub Pages tidak memfilter file |

## Cara Update Aplikasi (dari HP, tanpa laptop)

1. Edit `index.html` langsung di GitHub (ketuk file → ikon pensil → edit → Commit changes ke branch `main`).
2. Buka tab **Actions** → workflow **"Build Android APK"** → **Run workflow**.
3. Tunggu 3-8 menit sampai selesai (centang hijau).
4. Buka run yang barusan selesai, scroll ke bagian **Artifacts**, download:
   - **LogHM-release-apk** — kalau signing key (secrets) sudah di-setup, ini APK signed yang bisa langsung update tanpa uninstall.
   - **LogHM-debug-apk** — kalau secrets belum di-setup, ini APK debug (perlu uninstall app lama dulu sebelum install).
5. Ekstrak APK dari file `.zip` hasil download, install ke HP.

## Signing Key (untuk build release/signed)

Repo ini sudah di-setup dengan GitHub Secrets untuk signing otomatis:
- `KEYSTORE_BASE64` — keystore `locbook-release-key.jks` dalam format base64
- `KEYSTORE_PASSWORD` — password keystore
- `KEY_ALIAS` — `loghm`
- `KEY_PASSWORD` — password key

File keystore asli (`.jks`) **tidak pernah** disimpan di repo ini — hanya versi base64-nya sebagai secret terenkripsi.

## Catatan

- Web version (GitHub Pages) dan app native (APK via Capacitor) berbagi source code yang sama (`index.html`).
- Data tersimpan lokal di penyimpanan privat aplikasi (via Capacitor WebView) — lebih aman dari cache Chrome dibanding versi TWA/PWA sebelumnya.
- Jalur lama (PWABuilder + TWA manual) sudah tidak dipakai lagi.
