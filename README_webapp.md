# Ruang Simulasi Kebijakan Pangan Sumatera Utara

Aplikasi web satu berkas yang menyertai paper **Sumatranomics 2026**:
*Arbitrase Antarwilayah sebagai Titik Ungkit Ketahanan Pangan dan Stabilitas
Inflasi Sumatera Utara: Model Dinamika Sistem dan Optimisasi Kebijakan Banyak Tujuan.*

Penulis: Amrin B, Badan Pusat Statistik Provinsi Sulawesi Tenggara.

## Cara memakai

Buka `dashboard_sumatranomics_2026.html` di peramban mana pun. Tidak ada
pemasangan, tidak ada peladen, tidak ada sambungan internet yang dibutuhkan.
Seluruh data tertanam di dalam berkas.

## Isi

| Bagian | Isi |
|---|---|
| 01 Ringkasan temuan | Enam angka utama dan tiga temuan pokok |
| 02 Integrasi pasar | Half-life penyesuaian harga, simulasi penutupan selisih harga |
| 03 Guncangan harga | Respons kumulatif dengan selang kepercayaan 95 persen |
| 04 Struktur sistem | Diagram sebab akibat dan delapan feedback loop |
| 05 Dominansi feedback | Hasil loop knockout |
| 06 Uji kelayakan model | Enam uji Barlas dan reproduksi perilaku historis |
| 07 Daya jangkau tuas | Peta jangkauan tuas kebijakan terhadap sasaran |
| 08 Penjelajah kebijakan | 128 paket Pareto, pengatur tujuh tuas |
| 09 Ketegaran hasil | Selang persentil pada 60 tarikan parameter |
| 10 Dampak per wilayah | Sebaran dampak pada 33 kabupaten dan kota |
| 11 Cara membaca | Istilah, batas kesimpulan, dan rujukan |

## Panel interpretasi

Panel di sisi kanan menuliskan penjelasan setiap kali pengguna mengklik,
menggeser pengatur, atau berpindah bagian. Seluruh kalimat disusun dari angka
yang benar-benar dihitung pada notebook NB01 sampai NB06, bukan dari perkiraan.

## Sumber angka

Seluruh angka berasal dari keluaran enam notebook pengolahan:

- NB01 fondasi data, 127.328 observasi dari BPS dan Bank Indonesia
- NB02 estimasi struktur keterkaitan, 334 error correction model
- NB03 model dinamika sistem enam komoditas dan 33 wilayah
- NB04 sistem penuh tujuh blok dan analisis dominansi feedback loop
- NB05 optimisasi kebijakan banyak tujuan dengan NSGA-III
- NB06 koreksi definisi objective function, screening tuas, penjalanan ulang

## Lisensi dan atribusi data

Data bersumber dari Badan Pusat Statistik, Bank Indonesia, Badan Pangan
Nasional, dan Badan Informasi Geospasial. Pengolahan dan penafsiran adalah
tanggung jawab penulis.
