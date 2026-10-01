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
dengan sentuh maupun tetikus. Latarnya digambar berlapis: rumput bertekstur,
Laut Jawa bergradasi dengan awan dan perahu yang hanyut, garis pantai berombak
beserta buih, pohon berbatang dengan tiga gumpalan daun, pohon kelapa di tepi
pantai, kolam, serta properti taman berupa lampu jalan, bangku, kios, dan
petak bunga. Jalur pejalan kaki digambar tiga lapis (tepi, badan, garis tengah)
dan tiap wahana diberi bayangan lembut dari lapisan tersendiri.

Delapan kawasan ditandai dengan bentuk organik dan garis putus-putus di
dalamnya, memakai warna yang sama dengan legenda peta informasi resmi: Eropa
(biru), Asia (merah), Yunani (abu), Amerika (cokelat), Indonesia (kuning),
Hikayat (hijau), Jakarta (oranye), dan Dunia Kartun (merah muda). Kidz Fantasy
digambar sebagai bangunan karena memang kawasan dalam ruangan.

Saat peta dipaskan ke layar, tinggi header dan panel yang sedang mengintip ikut
diperhitungkan supaya taman tidak tertutup keduanya — selama itu tidak membuat
peta menyusut lebih dari sepuluh persen.

**Wahana**, masing-masing digambar dan dianimasikan sendiri dengan CSS keyframes
atau `animateMotion` — bianglala berputar, Kora-Kora mengayun, Hysteria menembak
ke atas, kereta Halilintar menyusuri lintasan, Niagara-Gara mencipratkan air.

Isi dan tata letaknya mengikuti dua sumber resmi Dufan: peta informasi cetak
(untuk posisi kawasan dan letak tiap wahana) dan daftar 31 wahana beserta 2 live
show (untuk wahana apa saja yang beroperasi dan pembagian kategorinya). Jadi
pengelompokannya persis seperti daftar resmi: 10 wahana ekstrem, 9 wahana
keluarga, dan 12 wahana anak.

Di luar ke-31 itu ada tiga tambahan: Tembak Jitu, yang ada di peta cetak sebagai
permainan ketangkasan dan bukan wahana; serta Kicir-Kicir dan Rajawali, yang
masih tercetak di peta tetapi tidak ada dalam daftar wahana beroperasi sehingga
diberi label "tidak beroperasi" di peta. Dua live show diwakili Pentas Prestasi
di Kawasan Yunani dan Pertunjukan Indoor Dufan di gedung Kidz Fantasy.

**Dua tampilan.** Tombol Peta / Daftar di bagian atas halaman memilih antara
peta dan grid kartu wahana; tidak ada lagi daftar yang tersembunyi di balik
panel. Di sebelahnya ada tombol tema dengan tiga keadaan: Auto (ikut sistem),
Terang, dan Gelap. Pilihan tema disimpan di browser.

**Daftar wahana** berupa grid kartu, bukan deretan teks. Tiap kartu menampilkan
animasi wahana itu sendiri — gambarnya disalin langsung dari peta, lengkap
dengan animasinya — plus nama, kawasan, dan garis warna sesuai kategori.

**Panel wahana.** Mengetuk sebuah wahana membuka panel dengan urutan: animasi
wahana di paling atas, lalu lab mini interaktif, lalu penjelasan fisika beserta
fotonya, dan tombol aksi di bagian bawah. Pada layar potret panel muncul sebagai
bottom sheet; pada layar lanskap yang cukup lebar (mulai 640 px) panel berpindah
ke sisi kanan sebagai sidebar setinggi layar, dan area peta ikut menyusut supaya
tidak ada bagian peta yang tertutup panel.

**Bagian fisika.** Tiap wahana dijelaskan dalam empat sampai lima bagian
bersubjudul (cara kerjanya, fisika yang bekerja, apa yang tubuh rasakan, dan apa
yang bisa dicoba di lab), ditutup rumus-rumus yang dirender sebagai SVG MathJax
(sudah di-pra-render dan disematkan, jadi tidak perlu memuat MathJax saat
halaman dibuka).

**30 lab mini interaktif** dalam tujuh jenis simulasi: bandul (`pendulum`),
kereta di lintasan (`coaster`), gerak melingkar (`circular`), jatuh bebas dari
menara (`drop`), tabrakan bumper car (`collision`), gaya apung (`buoy`), dan
bidang miring (`incline`). Tiap lab punya scene SVG, slider parameter, pembacaan
besaran secara langsung, dan bar energi potensial/kinetik. Semua lab berjalan
otomatis begitu panel dibuka dan mengulang sendiri; tombol ⏸ di panel
menghentikan seluruh animasi, termasuk animasi di kartu.

## Logo

Logo Dufan dan Ancol disematkan sebagai data URI PNG di dalam objek `LOGO` pada
bagian `<head>`, jadi halaman tetap satu berkas dan logonya tetap tampil tanpa
koneksi. Ketiganya dipakai di empat tempat: wordmark Dufan di header, papan nama
Ancol di dekat gerbang pada peta, keduanya sebagai kredit di bagian bawah daftar
wahana, dan tanda "A" berbintang milik Ancol sebagai ikon tab (favicon serta
apple-touch-icon, dipasang dari skrip saat halaman dimuat).

Logo Dufan dan Ancol adalah milik PT Pembangunan Jaya Ancol Tbk. Proyek ini
proyek belajar mandiri, bukan aplikasi resmi, dan hal itu dinyatakan di bagian
kredit dalam aplikasinya.

## Menambahkan foto wahana

Panel fisika punya slot foto untuk tiap wahana. Selama slot masih kosong, yang
tampil adalah kotak bergaris putus-putus. Untuk mengisinya, tambahkan entri ke
objek `PHOTOS` di dalam `index.html` dengan kunci berupa id wahana:

```js
var PHOTOS = {
  halilintar: 'data:image/jpeg;base64,/9j/4AAQ...',
  hysteria:   'foto/hysteria.jpg'
};
```

Nilainya boleh berupa data URI (halaman tetap utuh satu berkas dan bisa dibuka
tanpa internet) atau path/URL gambar biasa. Id wahana bisa dilihat pada daftar
`RIDES` di berkas yang sama.

## Catatan

- Angka pada lab adalah nilai model untuk keperluan belajar, bukan spesifikasi
  resmi wahana. Wahana yang punya spesifikasi publik (misalnya sudut ayun 75°
  pada Kora-Kora) diberi catatan tersendiri di panelnya.
- Mode gelap bisa dipilih lewat tombol tema, dan secara bawaan mengikuti sistem
  (`prefers-color-scheme`). Animasi juga menghormati `prefers-reduced-motion`.
- Tata letak aman untuk ponsel berlayar berlekuk (`env(safe-area-inset-*)`).
- Satu-satunya sumber daya eksternal adalah Google Fonts (Fraunces dan Plus
  Jakarta Sans); tanpa jaringan, halaman tetap berfungsi dengan font sistem.
