# Peta Dufan — Dunia Fantasi Ancol

Peta interaktif Dunia Fantasi (Dufan) Ancol yang sekaligus menjadi media belajar
fisika. Seluruh aplikasi berada dalam satu berkas HTML statis tanpa proses build:
buka `index.html` di browser, selesai.

## Menerbitkan lewat GitHub Pages

Repositori ini sudah siap disajikan apa adanya: `index.html` ada di akar dan
berkas `.nojekyll` membuat GitHub menyajikan berkas tanpa melewati Jekyll.
Tinggal satu setelan yang harus dinyalakan sekali oleh pemilik repositori:

**Settings → Pages → Build and deployment → Source: Deploy from a branch**,
pilih branch `claude/tender-allen-v2l7a3` dengan folder `/ (root)`, lalu Save.

Setelah itu setiap dorongan ke branch tersebut otomatis memperbarui situsnya di
`https://aliftowew.github.io/dufan-edulab/`. Setelan ini tidak bisa dinyalakan
dari skrip maupun dari GitHub Actions, karena token bawaan Actions tidak
berwenang membuat situs Pages.

## Menjalankan secara lokal

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

**Chrome yang ringkas.** Bagian atas layar hanya berisi judul dan dua tombol,
**Filter** dan **Menu**, yang masing-masing membuka popover. Filter memuat
saringan kategori wahana serta saringan fase dan kelas, lengkap dengan hitungan
wahana yang sedang ditampilkan; tombolnya diberi titik merah saat ada saringan
aktif. Menu memuat pilihan tampilan (Peta, Daftar wahana, Kurikulum), tombol tema
tiga keadaan (Auto, Terang, Gelap) yang pilihannya disimpan di browser, dan
tombol jeda animasi. Kontrol zoom peta mengambang di pojok kiri bawah, terpisah
dari panel, sehingga tidak ada kontrol yang muncul dua kali.

**Daftar wahana** berupa grid kartu, bukan deretan teks. Tiap kartu menampilkan
animasi wahana itu sendiri — gambarnya disalin langsung dari peta, lengkap
dengan animasinya — plus nama, kawasan, dan garis warna sesuai kategori.

**Halaman wahana.** Mengetuk sebuah wahana membuka halaman penuh, bukan panel
sepotong. Mulai lebar 900 px halaman itu terbagi dua kolom: kolom kiri yang
menempel saat digulir berisi animasi wahana dan lab mini, kolom kanan berisi
bacaannya. Di bawah 900 px keduanya menumpuk menjadi satu kolom.

Kolom kiri hanya menempel di pinggir atas kalau isinya muat satu layar. Kalau
lab mininya lebih tinggi dari layar, titik tempelnya dihitung ulang supaya kolom
itu ikut bergulir dulu sampai baris terbawahnya terlihat, baru menempel — jadi
tidak ada bagian lab yang terpotong dan tak bisa dicapai. Perhitungan ini
diperbarui saat ukuran jendela berubah dan saat tinggi lab berubah.

Isi kolom kanan berurutan: identitas wahana, **Dasar yang dipakai** (kartu konsep
seperti energi kinetik dan gaya sentripetal, teksnya mengikuti fase), **Fisika di
balik wahana** dengan rumus disisipkan tepat setelah paragraf yang
menjelaskannya, **Aktivitas murid** sesuai fase dan jenis wahananya, lalu blok
kurikulum.

Mengganti saringan sementara halaman wahana terbuka tidak menutup atau memuat
ulang halaman itu. Hanya kolom kanan yang digambar ulang pada kedalaman fase
yang baru; posisi gulir tetap di tempatnya dan animasi di kolom kiri terus
berjalan. Lab mini hanya dipasang ulang kalau perubahannya melintasi batas Fase
B/C, karena di situ bentuk rumusnya memang berganti.

Wahana yang sedang dibuka juga tidak lagi ditutup paksa ketika saringan baru
tidak memuatnya. Halamannya tetap terbuka dengan satu keterangan singkat bahwa
wahana itu di luar saringan yang aktif.

## Kartu misi dan kuis

Halilintar dan Hysteria memuat dua bagian tambahan yang mengikuti rancangan
guru: **Kartu misi di lokasi** dan **Kuis pasca-kunjungan**. Keduanya hanya
muncul setelah fase dipilih pada tombol Filter, dan isinya berganti mengikuti
fase itu.

Kartu misi berisi 10 misi per fase per wahana, dari "Detektif Gerak" untuk Fase
B sampai "Physics Researcher" untuk Fase F. Setiap misi bisa langsung diisi di
aplikasi: kolom isian, daftar bernomor, kotak centang, dan tabel data. Jawaban
disimpan di `localStorage` peramban murid sendiri, tidak dikirim ke mana pun,
dan bertahan setelah halaman ditutup atau dimuat ulang. Penghitung di atas
kartu menunjukkan berapa misi yang sudah terisi, tiap misi yang sudah diisi
diberi tanda centang, dan satu tombol mengosongkan seluruh kartu itu.

Kuis pasca-kunjungan tersedia untuk Fase B, D, E, dan F. Pilihan gandanya
langsung memberi tahu benar atau salah beserta perhitungannya, sedangkan tiap
uraian menyimpan jawaban yang diharapkan di balik satu tombol untuk dibuka guru.
Pedoman skornya ikut dicantumkan. Fase C belum ada kuisnya dalam rancangan, dan
aplikasi menyatakan itu apa adanya.

Fase yang dipilih ikut diingat `localStorage`, jadi rombongan yang membuka
aplikasi lagi di lokasi tidak perlu memilih jenjangnya berulang kali.

Halaman wahana tidak memuat tombol navigasinya sendiri. Peta, daftar wahana,
dan kurikulum semuanya satu tempat saja, yaitu tombol Menu. Menutup halaman
lewat tombol kembali sekaligus membawa peta ke wahana yang barusan dibaca.

**Bilah atas tetap.** Judul atau tombol kembali di kiri, Filter dan Menu di
kanan, posisinya tidak bergeser saat halaman dibuka atau ditutup.

**Rel daftar wahana.** Mulai lebar 1024 px, sisi kiri yang tadinya kosong diisi
rel berisi kartu wahana yang ikut mengikuti saringan, sehingga lebar layar laptop
terpakai dan daftar selalu terlihat.

**Bagian fisika.** Tiap wahana dijelaskan dalam empat sampai lima bagian
bersubjudul (cara kerjanya, fisika yang bekerja, apa yang tubuh rasakan, dan apa
yang bisa dicoba di lab), ditutup rumus-rumus yang dirender sebagai SVG MathJax
(sudah di-pra-render dan disematkan, jadi tidak perlu memuat MathJax saat
halaman dibuka).

**Lab mini interaktif** dalam sembilan jenis simulasi: bandul (`pendulum`),
kereta di lintasan (`coaster`), gerak melingkar (`circular`), jatuh bebas dari
menara (`drop`), tabrakan bumper car (`collision`), gaya apung (`buoy`), bidang
miring (`incline`), saluran air dan perahu model (`flow`), serta sensor cahaya
dan logika (`logika`). Kesembilannya sengaja dibuat sepadan dengan tabel
"Praktikum Model Pasangan Wahana" pada kurikulum.

Tiap lab punya scene SVG, slider parameter, pembacaan besaran secara langsung,
bar energi potensial/kinetik, dan **rumus hidup** di atas slidernya: rumus utama
lab ditampilkan dengan tiap variabel sebagai kotak tersendiri, kotak variabel
yang sedang digeser menyala, dan baris di bawahnya memperlihatkan angka yang
disubstitusikan beserta hasilnya. Semua lab berjalan otomatis begitu panel dibuka
dan mengulang sendiri; tombol jeda animasi ada di Menu.

**Kedalaman isi mengikuti fase.** Saat saringan fase aktif, seluruh halaman
wahana menyesuaikan diri. Pada Fase B dan C, kartu konsep memakai bahasa
sehari-hari tanpa lambang, narasinya memakai versi sederhana dua bagian, rumus
tidak ditampilkan, lab mengganti rumus dengan satu kalimat penjelas, dan
pembacaan besarannya dipangkas menjadi dua yang terpenting. Fase D dan E memakai
penjelasan menengah dengan dua rumus utama, sedangkan Fase F memakai penjelasan
lanjut dengan seluruh rumusnya. Fase yang sedang dipakai muncul sebagai label
kecil di kepala lab.

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

## Kurikulum

Aplikasi ini dipetakan ke *Kurikulum Pembelajaran Sains dan Fisika Kontekstual
Berbasis Wahana Dunia Fantasi*, kurikulum suplemen Fase B sampai F yang memakai
wahana Dufan sebagai konteks dan tidak menggantikan Capaian Pembelajaran
nasional. Pemetaannya ada di objek `KURIKULUM` dalam `index.html`: lima fase, 26
tujuan pembelajaran, dan untuk tiap wahana daftar fase, daftar TP, pasangan
praktikum di sekolah, serta status datanya.

Tampilan **Kurikulum** di header menyediakan:

- kartu tiap fase berisi fokus materi, keterampilan proses, dan produk akhirnya;
- aktivitas murid per fase dan per jenis wahana, yang muncul langsung di halaman
  wahana saat fasenya dipilih;
- tombol **Saring peta**, yang meredupkan wahana di luar fase itu (saringan yang
  sama juga tersedia lewat tombol Filter di header, dengan label kelasnya);
- daftar tujuan pembelajaran yang bisa diketuk untuk menyaring peta sekaligus
  menyusun rute;
- **Susun rute**, yang mengurutkan kunjungan mulai dari Gerbang Utama lalu selalu
  ke wahana terdekat berikutnya, dan menggambar nomor urutnya di peta;
- **Lembar kerja**, yang menghasilkan LKPD siap cetak berisi tujuan pembelajaran,
  tabel prediksi pra-kunjungan, tabel pengamatan per wahana lengkap dengan besaran
  yang diukur, tabel praktikum model di sekolah, dan pertanyaan refleksi.

Panel tiap wahana juga menampilkan blok *Dalam kurikulum*: fase yang dilayani,
tujuan pembelajaran yang didukung beserta bunyinya, pasangan praktikum di
sekolah, dan status data (terverifikasi, observasional, atau bersyarat) sesuai
klasifikasi yang diminta kurikulum.

## Foto wahana

Halaman wahana memuat foto asli di bawah judul **Fisika di balik wahana**. Foto
dikecilkan ke lebar maksimum 640 px, disimpan sebagai JPEG mutu 58, lalu disandi
menjadi data URI pada objek `FOTO` di dalam `index.html`. Dengan begitu aplikasi
tetap satu berkas dan tetap bisa dibuka tanpa jaringan di lokasi.

33 dari 34 wahana sudah berfoto, ditambah Pentas Prestasi dan pertunjukan
indoor. Rumah Riana belum ada fotonya, jadi di halamannya masih tampil kotak
bergaris putus-putus.

Hak cipta foto ada pada pemiliknya. `FOTO_KREDIT` menyimpan nama pemilik dan
halaman sumber tiap foto, dan keduanya ditulis pada keterangan di bawah foto
beserta tautan ke halaman asalnya. Sebagian besar berasal dari situs resmi
Ancol, sisanya dokumentasi arsip yang tercantum sumbernya.

Untuk mengganti atau menambah foto, sunting entri pada `FOTO` dengan kunci
berupa id wahana (lihat daftar `RIDES` di berkas yang sama). Nilainya boleh data
URI atau path/URL gambar biasa.

## Catatan

- Angka pada lab adalah nilai model untuk keperluan belajar, bukan spesifikasi
  resmi wahana. Wahana yang punya spesifikasi publik (misalnya sudut ayun 75°
  pada Kora-Kora) diberi catatan tersendiri di panelnya.
- Mode gelap bisa dipilih lewat tombol tema, dan secara bawaan mengikuti sistem
  (`prefers-color-scheme`). Animasi juga menghormati `prefers-reduced-motion`.
- Tata letak aman untuk ponsel berlayar berlekuk (`env(safe-area-inset-*)`).
- Satu-satunya sumber daya eksternal adalah Google Fonts (Fraunces dan Plus
  Jakarta Sans); tanpa jaringan, halaman tetap berfungsi dengan font sistem.
