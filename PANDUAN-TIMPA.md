# PANDUAN TIMPA FILE - Hz LogHM V7.1

## File yang TINGGAL TIMPA LANGSUNG (upload, replace)
Upload file-file ini ke root repo `Hz-LogHM`, pilih replace/overwrite:

- `manifest.json` → timpa yang lama
- `sw.js` → timpa yang lama
- `twa-manifest.json` → timpa yang lama (host & startUrl sudah dibetulkan)
- `.nojekyll` → tambahkan kalau belum ada
- `.gitignore` → tambahkan/timpa
- folder `icons/` (isi `icon-192.png` & `icon-512.png`) → tambahkan folder baru

## File yang HARUS DITEMPEL MANUAL: index.html

Ini SATU-SATUNYA file yang tidak saya sertakan utuh, karena isi app (logic HM/OT/BBM/drawer) Bos ada di sana dan saya tidak punya source lengkapnya. Caranya:

1. Buka `index.html` di GitHub → klik ikon pensil (Edit).
2. Cari baris `<head>` paling atas. Tepat setelah `<head>`, sebelum `<title>`, **tempel 3 baris ini**:

```html
<link rel="manifest" href="./manifest.json">
<meta name="theme-color" content="#2563eb">
<link rel="apple-touch-icon" href="./icons/icon-192.png">
```

3. Scroll ke paling bawah, cari `</body>`. Tepat **sebelum** `</body>`, tempel ini:

```html
<script>
if ('serviceWorker' in navigator) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('./sw.js');
  });
}
</script>
```

4. Klik "Commit changes" langsung ke branch `main`.

## Setelah semua ditimpa/ditempel

1. Tunggu ± 1 menit, cek tab **Actions** → pastikan centang hijau.
2. Tes buka `https://hannezt19.github.io/Hz-LogHM/manifest.json` di browser HP → harus muncul teks JSON, bukan 404.
3. Scan ulang di pwabuilder.com/reportcard pakai `https://hannezt19.github.io/Hz-LogHM/`.

Kalau masih ada yang merah setelah ini, kirim screenshot report card-nya lagi ya Bos.
