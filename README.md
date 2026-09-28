# Peta Dufan — Dunia Fantasi Ancol

Peta interaktif Dunia Fantasi (Dufan) Ancol yang sekaligus menjadi media belajar
fisika. Seluruh aplikasi berada dalam satu berkas HTML statis tanpa proses build:
buka `index.html` di browser, selesai.

## Menjalankan

Buka langsung:

```
xdg-open index.html      # Linux
open index.html          # macOS
```

Atau lewat server statis (disarankan agar font web ikut termuat):

```
python3 -m http.server 8000
# lalu buka http://localhost:8000
```

## Isi

**Peta.** Ilustrasi SVG taman (viewBox 640×1000) yang bisa digeser dan di-zoom
dengan sentuh maupun tetikus, memuat Laut Jawa, pantai, plaza, area parkir, jalur
pejalan kaki, dan pepohonan. Sepuluh kawasan ditandai: Asia, Hikayat, Eropa,
Amerika, Indonesia, Kidz Fantasy (indoor), Istana Boneka, Yunani, Dunia Kartun,
dan Jakarta.

**34 wahana**, masing-masing digambar dan dianimasikan sendiri dengan CSS
keyframes atau `animateMotion` — bianglala berputar, Kora-Kora mengayun, Hysteria
menembak ke atas, kereta Halilintar menyusuri lintasan, Niagara-Gara mencipratkan
air. Wahana dikelompokkan sebagai ekstrem (11), keluarga (17), dan anak (6);
wahana yang sedang tutup diberi label di peta.

**Panel wahana.** Mengetuk sebuah wahana membuka bottom sheet berisi kawasan,
jenis wahana, tingkat sensasi, dan deskripsi singkat.

**Bagian fisika.** Tiap wahana punya penjelasan konsep, uraian naratif, dan
rumus-rumus yang dirender sebagai SVG MathJax (sudah di-pra-render dan
disematkan, jadi tidak perlu memuat MathJax saat halaman dibuka).

**30 lab mini interaktif** dalam tujuh jenis simulasi: bandul (`pendulum`),
kereta di lintasan (`coaster`), gerak melingkar (`circular`), jatuh bebas dari
menara (`drop`), tabrakan bumper car (`collision`), gaya apung (`buoy`), dan
bidang miring (`incline`). Tiap lab punya scene SVG, slider parameter, pembacaan
besaran secara langsung, dan bar energi potensial/kinetik.

## Catatan

- Angka pada lab adalah nilai model untuk keperluan belajar, bukan spesifikasi
  resmi wahana. Wahana yang punya spesifikasi publik (misalnya sudut ayun 75°
  pada Kora-Kora) diberi catatan tersendiri di panelnya.
- Mendukung mode gelap otomatis (`prefers-color-scheme`) dan menghormati
  `prefers-reduced-motion`.
- Tata letak aman untuk ponsel berlayar berlekuk (`env(safe-area-inset-*)`).
- Satu-satunya sumber daya eksternal adalah Google Fonts (Fraunces dan Plus
  Jakarta Sans); tanpa jaringan, halaman tetap berfungsi dengan font sistem.
