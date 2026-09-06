# Ketahanan Pangan dan Dinamika Harga Sumatera Utara

Model dinamika sistem dan optimisasi kebijakan banyak tujuan untuk 33 kabupaten dan kota di
Provinsi Sumatera Utara. Repositori ini memuat notebook pengolahan, naskah paper, dan aplikasi
web interaktif yang disusun untuk *Call for Paper* 7th Sumatranomics 2026, Bank Indonesia.

Pertanyaan yang dijawab: instrumen kebijakan mana yang benar-benar dapat menyentuh harga pangan
di tingkat daerah, seberapa besar dampaknya, dan kesimpulan mana yang masih bertahan ketika
parameter model digeser sepanjang selang kepercayaannya.

---

## Ringkasan temuan

Tingkat harga pangan rata-rata tidak dapat diturunkan oleh instrumen yang berada dalam kendali
pemerintah daerah pada horizon tiga tahun. Yang dapat diubah adalah keseragaman harga
antarwilayah dan kepastian pasokan.

| Temuan | Angka |
| --- | --- |
| Model koreksi kesalahan yang diestimasi | 334 pasangan wilayah dan komoditas, 85,3 persen bertanda benar dan signifikan |
| Dominansi loop arbitrase antarwilayah | sekitar 154 kali loop terkuat berikutnya |
| Pasangan instrumen dan sasaran yang bernilai nol eksak | 19 dari 32 |
| Paket kebijakan tidak terdominasi pada pagu 0,599 triliun rupiah | 128 paket, biaya 0,066 sampai 0,598 triliun rupiah |
| Paket kompromi terpilih menurut *minimax regret* | biaya 0,296 triliun rupiah, layak anggaran pada 96,7 persen replikasi |
| Dampak paket kompromi | sebaran harga antarwilayah menyempit 7,88 persen, kekurangan pasokan hilang, nilai tukar petani naik 0,010 poin indeks |
| Perbandingan biaya untuk sasaran yang sama | dukungan produksi 251 kali lebih murah daripada cadangan dengan operasi pasar |

Tidak satu pun dari 128 paket menurunkan tingkat harga pangan tertimbang penduduk. Sebanyak 126
paket menurunkan kekurangan pasokan, dan hanya 66 paket menurunkan tingkat kemiskinan. Arah
dampak terhadap kemiskinan dinyatakan tidak konklusif karena berubah tanda antarreplikasi
parameter, dan hal itu dilaporkan apa adanya.

---

## Isi repositori

```
.
├── notebooks/
│   ├── 01_Fondasi_Data_Sumut_Sumatranomics2026.ipynb
│   ├── 02_Estimasi_Struktur_Keterkaitan_Sumut.ipynb
│   ├── 03_Model_Dinamika_Sistem_Sumut.ipynb
│   ├── 04_Sistem_Penuh_CLD_dan_SFD_Sumut.ipynb
│   ├── 05_Optimisasi_Kebijakan_dan_Dashboard_Sumut.ipynb
│   └── 06_Koreksi_Tujuan_dan_Optimisasi_Ulang_Sumut.ipynb
├── data/
│   ├── DataSumateraUtaraBPSterekstrak.xlsx
│   ├── Data_Sumut_IHK_Inflasi_Harga_20202026.xlsx
│   ├── NTP_Sumatera_Utara_20202026_Terstruktur.xlsx
│   └── Diagram_Timbang_NTP_2018_Sumatera_Utara.xlsx
├── dashboard/
│   └── dashboard_sumatranomics_2026.html
├── paper/
│   └── Paper_Sumatranomics_2026_Sumatera_Utara.docx
└── README.md
```

### Peran setiap notebook

| Notebook | Isi |
| --- | --- |
| 01 | Pembersihan data, audit anomali BPS, penyeragaman kode wilayah, dan pembentukan panel wilayah, komoditas, dan bulan |
| 02 | Estimasi *error correction model* per pasangan wilayah dan komoditas, *local projection* untuk penjalaran guncangan, serta klaster spasial |
| 03 | Perakitan model dinamika sistem, kalibrasi parameter, dan rangkaian uji validasi Barlas |
| 04 | *Causal loop diagram*, *stock and flow diagram*, dan analisis dominansi loop melalui *loop knockout* |
| 05 | Optimisasi NSGA-III atas enam sasaran dan penyusunan berkas dashboard |
| 06 | Definisi tujuan final, optimisasi ulang, propagasi ketidakpastian dengan *common random numbers*, dan uji konsistensi otomatis |

Setiap notebook memuat sel interpretasi otomatis yang hanya membaca nilai hasil perhitungan,
sehingga narasinya berubah mengikuti data dan tidak pernah ditulis di muka.

---

## Cakupan dan data

- 33 kabupaten dan kota, yaitu seluruh anggota populasi, sehingga tidak dilakukan penarikan sampel
- 6 komoditas endogen: beras, cabai merah, cabai rawit, bawang merah, bawang putih, dan kentang,
  bersama-sama menyusun 8,04 persen keranjang indeks harga konsumen Sumatera Utara
- 1.194 variabel keadaan pada versi blok pangan, 1.485 pada versi tujuh blok
- Horizon simulasi kebijakan 36 bulan, periode validasi 72 bulan
- 96 parameter diestimasi: 39 berpresisi tinggi, 12 sedang, dan 45 rendah atau tidak terukur

Sumber data: Badan Pusat Statistik, Bank Indonesia, Badan Pangan Nasional, dan Badan Informasi
Geospasial. Berkas mentah tidak diunggah ulang di sini bila lisensinya membatasi redistribusi.
Tautan unduhan tercantum pada sel pertama Notebook 01.

Parameter berpresisi rendah tidak dipakai sebagai nilai tunggal. Nilainya ditelusuri sepanjang
selang kepercayaan pada seluruh simulasi, sehingga ketidakpastiannya ikut terbawa sampai ke hasil
kebijakan.

---

## Menjalankan notebook

Diuji pada Python 3.11.14 dengan JupyterLab.

```bash
git clone https://github.com/<pengguna>/<repositori>.git
cd <repositori>
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

Paket utama yang dipakai: `pandas`, `numpy`, `scipy`, `statsmodels`, `linearmodels`, `pymoo`,
`geopandas`, `matplotlib`, `openpyxl`, `xlsxwriter`, dan `pdfplumber`.

Notebook dijalankan berurutan dari 01 sampai 06 karena setiap tahap membaca luaran tahap
sebelumnya. Skrip pemasangan folder Google Drive berjalan otomatis dan mengenali lingkungan macOS,
Windows, Linux, maupun Google Colab. Letakkan berkas data pada folder bernama `Clean Data Sumut`
di lokasi yang sama.

Waktu jalan penuh sekitar satu sampai dua jam pada mesin dengan empat inti, sebagian besar
dihabiskan pada pencarian NSGA-III dan propagasi ketidakpastian.

---

## Aplikasi web

Berkas `dashboard/dashboard_sumatranomics_2026.html` bersifat mandiri, satu berkas, tanpa proses
pembangunan dan tanpa peladen. Cukup buka melalui peramban.

Sebelas bagian yang tersedia: ringkasan temuan, integrasi pasar, guncangan harga, struktur sistem
dinamik, dominansi loop, uji kelayakan model, daya jangkau instrumen, simulasi paket kebijakan,
ketahanan hasil, dampak per wilayah, dan cara membaca.

Beberapa hal yang dapat dilakukan di dalamnya:

- Menelusuri kedelapan *feedback loop* satu per satu pada *causal loop diagram* berisi 15 besaran
  dan 22 tautan sebab akibat, lengkap dengan tafsir tiap loop
- Menyusun paket kebijakan sendiri melalui tujuh pengatur, dengan lima titik awal siap pakai
  termasuk paket acuan yang dilaporkan pada naskah
- Membaca dampak paket kompromi pada seluruh 33 wilayah, termasuk wilayah yang justru dirugikan
- Membuka glosarium 30 istilah yang menjelaskan konsep di balik setiap metode

Angka yang ditampilkan selalu berasal dari simulasi yang benar-benar dijalankan. Ketika pengatur
digeser, aplikasi menunjukkan paket tersimulasi terdekat, bukan hasil interpolasi.

Fon diambil dari Google Fonts. Tanpa sambungan internet, tampilan turun ke fon sistem dan seluruh
isinya tetap terbaca.

---

## Catatan metodologi

Model dibangun dari empat lapis yang saling menyambung.

1. **Integrasi pasar.** Kecepatan penyesuaian harga kabupaten terhadap acuan provinsi diestimasi
   dengan *error correction model* mengikuti Engle dan Granger (1987), lalu diterjemahkan menjadi
   *half-life*. Penjalaran guncangan antarindeks diperkirakan dengan *local projection* mengikuti
   Jorda (2005).
2. **Dinamika sistem.** Parameter hasil estimasi dirakit menjadi model dinamika sistem tujuh blok,
   lalu diuji dengan rangkaian pemeriksaan Barlas (1996). Kekuatan setiap loop diukur melalui
   *loop knockout*.
3. **Optimisasi.** Tujuh instrumen kebijakan dioptimalkan atas enam sasaran sekaligus dengan
   NSGA-III (Deb dan Jain, 2014), di bawah pagu satu persen belanja daerah gabungan.
4. **Ketahanan.** Enam puluh paket diuji ulang pada 60 penarikan parameter acak dengan
   *common random numbers*, dan paket kompromi dipilih menurut *minimax regret* (Savage, 1951).

Seluruh tujuan didefinisikan sebagai selisih tingkat akhir terhadap skenario tanpa intervensi pada
bulan yang sama, bukan sebagai laju pertumbuhan terhadap keadaan awal. Kebijakan yang bekerja
sejak bulan pertama akan menggeser titik awalnya sendiri, sehingga definisi berbasis laju
menghasilkan tanda yang menyesatkan.

Notebook 06 memuat uji konsistensi yang menghentikan eksekusi bila nilai tujuan agregat tidak
sama dengan rata-rata tertimbang penduduk atas tingkat harga akhir per kabupaten.

---

## Batas kesimpulan

Bagian ini sengaja dicantumkan agar hasil tidak dikutip melampaui yang ditopang data.

Yang boleh disimpulkan:

- Peringkat antarkebijakan pada lima sasaran yang rasio daya bedanya di atas satu
- Arah pengaruh pada sasaran yang seluruh selang persentilnya berada di satu sisi garis nol
- Pernyataan bahwa suatu instrumen tidak menyentuh suatu sasaran, sebab angkanya nol eksak
- Perbandingan biaya antarinstrumen untuk mencapai sasaran yang sama

Yang tidak boleh disimpulkan:

- Peringkat antarkebijakan pada kekurangan pasokan, sebab rasio daya bedanya hanya 0,20
- Pertukaran antara tingkat harga pangan, nilai tukar petani, dan sebaran harga antarwilayah,
  sebab ketiganya redundan dengan korelasi peringkat di atas 0,99
- Arah dampak kebijakan terhadap tingkat kemiskinan, sebab paket kompromi hanya membaik pada
  31,7 persen penarikan parameter
- Tingkat mutlak pertumbuhan PDRB, sebab koreksi kondisi awal stok modal membuat tingkatnya tidak
  lagi setara pengamatan
- Angka mana pun sebagai ramalan. Model ini menurunkan akibat logis dari struktur yang sudah
  diukur, dan tidak dirancang sebagai alat peramalan.

---

## Rujukan utama

- Barlas, Y. (1996). Formal aspects of model validity and validation in system dynamics.
  *System Dynamics Review, 12*(3), 183-210.
- Deb, K., dan Jain, H. (2014). An evolutionary many-objective optimization algorithm using
  reference-point-based nondominated sorting approach, part I. *IEEE Transactions on Evolutionary
  Computation, 18*(4), 577-601. https://doi.org/10.1109/TEVC.2013.2281535
- Engle, R. F., dan Granger, C. W. J. (1987). Co-integration and error correction: Representation,
  estimation, and testing. *Econometrica, 55*(2), 251-276.
- Jorda, O. (2005). Estimation and inference of impulse responses by local projections.
  *American Economic Review, 95*(1), 161-182.
- Ravallion, M. (1986). Testing market integration. *American Journal of Agricultural Economics,
  68*(1), 102-109.
- Savage, L. J. (1951). The theory of statistical decision. *Journal of the American Statistical
  Association, 46*(253), 55-67.
- Sterman, J. D. (2000). *Business dynamics: Systems thinking and modeling for a complex world*.
  Irwin McGraw-Hill.

Daftar pustaka lengkap tercantum pada naskah paper.

---

## Cara mengutip

```bibtex
@techreport{barata2026pangan,
  author      = {Barata, Amrin},
  title       = {Ketahanan Pangan dan Dinamika Harga Sumatera Utara:
                 Model Dinamika Sistem dan Optimisasi Kebijakan Banyak Tujuan},
  institution = {7th Sumatranomics, Bank Indonesia},
  year        = {2026},
  address     = {Palembang, Indonesia}
}
```

---

## Penulis dan lisensi

Amrin Barata, Badan Pusat Statistik Provinsi Sulawesi Tenggara.

Pandangan yang disampaikan pada repositori ini merupakan pandangan penulis dan tidak mewakili
lembaga tempat penulis bekerja maupun penyelenggara Sumatranomics.

Kode dan notebook berada di bawah lisensi MIT. Data mengikuti ketentuan penggunaan masing-masing
lembaga penerbit.
