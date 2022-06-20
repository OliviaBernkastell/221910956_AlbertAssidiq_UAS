# Dashboard Informasi
Data dari BPS tentang Kemiskinan

## Profile
- Nim       : 221910956
- Nama      : Albert Assidiq
- Kelas     : 3SD2
- Dashboard : https://public.tableau.com/app/profile/albert.assidiq/viz/uas_16554903769940/DashboardInformasi?publish=yes

## Alur Pengerjaan
1. Cari data di [bps.go.id](https://www.bps.go.id/) mengenai kemiskinan
2. Melakukan *preprocessing* karena struktur tabel belum sesuai
3. Buka Tableau dan pilih data yang tadi di ambil
4. Membuat Diagram Peta
5. Membuat Line Chart
6. Membuat Matriks Korelasi
7. Membuat Paralel Koordinat
8. Membuat Dashboard
9. Mengevaluasi

## 1. Mencari Data
Ke web BPS lalu cari data:
- Persentase Penduduk Yang Hidup di Bawah Garis Kemiskinan Nasional Berdasarkan Kelompok Umur 2015-2021
  - Kelompok umur terbagi 2 menjadi 18< dan >= 18 tahun
- Garis Kemiskinan Menurut Provinsi dan Daerah Perkotaan Semester 1 (Maret) Dari tahun 2016-2021
  - Garis Kemiskinan merupakan representasi dari jumlah rupiah minimum yang dibutuhkan untuk memenuhi kebutuhan pokok minimum makanan yang setara dengan 2100 kilokalori per kapita per hari dan kebutuhan pokok bukan makanan
- Gini Ratio Perkotaan Semester 1 (Maret) Dari tahun 2016-2021
  - Nilai Rasio Gini berkisar antara 0 hingga 1. Nilai Rasio Gini yang semakin mendekati 1 mengindikasikan tingkat ketimpangan yang semakin tinggi
  - Rasio Gini bernilai 0 menunjukkan adanya  pemerataan pendapatan yang sempurna, atau setiap orang memiliki pendapatan yang sama
  - Sedangkan, Rasio Gini bernilai 1 menunjukkan ketimpangan yang sempurna, atau satu orang memiliki segalanya sementara orang-orang lainnya tidak memiliki apa-apa
- Persentase Penduduk Miskin (P0) Menurut Provinsi dan Daerah Perkotaan Semester 1 (Maret) Tahun 2016-2021
  - Angka yang ditunjukkan oleh HCI-P0 menunjukkan proporsi penduduk miskin di suatu wilayah. Persentase penduduk miskin yang tinggi menunjukkan bahwa tingkat kemiskinan di suatu wilayah juga tinggi
- Indeks Kedalaman Kemiskinan (P1) Menurut Provinsi dan Daerah Perkotaan Semester 1 (Maret) Tahun 2016-2021
  - Ukuran rata-rata kesenjangan pengeluaran masing-masing penduduk miskin terhadap garis kemiskinan
  - Nilai agregat dari poverty gap index menunjukkan biaya mengentaskan kemiskinan dengan membuat target transfer yang sempurna terhadap penduduk miskin dalam hal tidak adanya biaya transaksi dan faktor penghambat
  - Semakin kecil nilai poverty gap index, semakin besar potensi ekonomi untuk dana pengentasan kemiskinan berdasarkan identifikasi karakteristik penduduk miskin dan juga untuk target sasaran bantuan dan program
- Indeks Keparahan Kemiskinan (P2) Menurut Provinsi dan Daerah Perkotaan Semester 1 (Maret) Tahun 2016-2021
  - Indeks yang memberikan informasi mengenai gambaran penyebaran pengeluaran di antara penduduk miskin
  - Semakin tinggi nilai indeks, semakin tinggi ketimpangan pengeluaran di antara penduduk miskin

![image](https://user-images.githubusercontent.com/78963679/174429631-2f8b626f-6bf9-4f11-a0de-7553d5a23f35.png)

## 2. *preprocessing*
Mengubah Struktur data yang awalnya seperti :

![image](https://user-images.githubusercontent.com/78963679/174429646-13ac3624-a87c-4fd9-9296-a6ddee623279.png)

Menjadi :

![image](https://user-images.githubusercontent.com/78963679/174429651-35ff220a-4b19-450b-836b-080fb61527e0.png)

Lakukan hal ini kepada semua data yang diamnbil sehingga mudah di read Tableau.

## 3. Masukkan Data ke Tableau
Karena 1 data memiliki beberapa tabel, harus dibuat relasi agar terhubung

![image](https://user-images.githubusercontent.com/78963679/174430582-1803c7fb-91ce-4252-88df-7226739643af.png)

Ada juga tabel yang tidak bisa di *join* sehingga dibuat *datasource* baru

![image](https://user-images.githubusercontent.com/78963679/174431827-c91601e5-e884-4f28-9665-d93dab22ec47.png)


## 4. Diagram Peta
Disini saya ingin melihat perkembangan garis kemiskinan setiap provinsi dari tahun 2016-2021

Cara:
1. Masukkan kolom nama provinsi ke detail
2. Langitude dan Longitude akan autogenerate
3. Masukkan Longitude di Kolom, Langitude di baris
4. Buat Parameter untuk memilih tahun dan *Calculated Field* untuk memilih data
5. Masukkan *Calculated Field* tadi ke color
6. Klick kanan Parameter lalu tekan *show filter*
7. Lakukan hal yang sama pada *Calculated Field*

![image](https://user-images.githubusercontent.com/78963679/174430760-b9cb2792-5fa4-4722-b029-17bc97401caa.png)

## 5 Line Chart
Disini ingin ditampilkan data Persentase Penduduk Yang Hidup di Bawah Garis Kemiskinan Nasional Berdasarkan Kelompok Umur dari tahun ke tahun

Cara:
1. Buat Parameter untuk memilih tahun dan *Calculated Field* untuk memilih kelompok umur
2. Masukkan Kedua *Calculated Field* ke *row*
3. Tahun di *column*
4. Klik kanan di variabel baris, tekan *dual axis*
5. Klik kanan *header* di kanan/kiri grafik, tekan *sincronyze axis*
6. Klik kanan *header* lagi, tekan hide
7. Masukkan *measure names* ke *color*
8. Klick kanan Parameter lalu tekan *show filter*

![image](https://user-images.githubusercontent.com/78963679/174431325-fb627a85-7de0-4b24-a3df-ee51a8db80eb.png)

## 6 Matriks Korelasi
Membuat matrix korelasi antara P0, P1 dan P2, apakah mereka mempunyai korelasi yang positif

Cara:
1. Buat Parameter untuk memilih tahun dan 3 *Calculated Field* untuk memilih tahun
2. Masukkan Ketiga *Calculated Field* ke *row* dan *column*
3. Klick kanan Parameter lalu tekan *show filter*

![image](https://user-images.githubusercontent.com/78963679/174431503-cb4e987d-5d74-44b3-99ac-64fa2326d171.png)

## 7. Paralel Koordinat
Ingin dilihat visualisai data multivariat dan provinsi sebagai objeknya, sebelum itu harus dipilih variabelnya

Variabel terpilih:
- Garis Kemiskinan
- Ratio Gini
- P0
- P1
- P2

Cara:
1. Buat Parameter untuk memilih tahun dan 5 *Calculated Field* untuk tahun
2. Masukka kelima *Calculated Field* ke *measure value*
3. Buat 5 *Calculated Field* dengan rumus
![image](https://user-images.githubusercontent.com/78963679/174432217-a863fc98-bf8b-429f-bd1f-48860462ea62.png)
4. Lalu masukkan ke dalam hitungan *Calculated Field* di no 2
5. Pilih semua variabel, klik kanan -> *compute using* -> provinsi
6. Ubah jadi *line*
7. P0 sebagai pemisah warna supaya bisa liat, dimana letak variabel lain ketika P0 memiliki nilai sekian
![image](https://user-images.githubusercontent.com/78963679/174432339-cc3c7954-a981-4b3c-adc4-705dfeead008.png)

## 8. Dashboard Informasi
Desainnya adalah Diagram peta paling atas karena menonjol, selanjutnya Paralel Koordinat karena mencakup 5 variabel, yang dibawahnya adalah matrix korelasi karena mencakup 3 variabel. Ketiga diagram tadi memiliki parameter Tahun yang sehingga disatukan, jadi yang terakhir adalah diagram garis.

![image](https://user-images.githubusercontent.com/78963679/174432525-105604ac-766d-4fae-91a0-841d183ef779.png)

## 9. Evaluasi
Saya mengevaluasi dashboard ini dengan 3 dimensi yaitu *Usefulness, Usability, Aesthetics*. Sehingga dibuat pertanyaan dalam kuesioner seusai dengan dimensi evaluasi. Lalu dijawab dengan angka 1-5, dimana angka 1 berarti sangat tidak setuju dan 5 sangat setuju.

*Usefulness*:
1. Saya menganggap Dashboard ini sangat berguna (F1)
2. Fungsi Dashboard sangat tepat untuk menampilkan kemiskinan di Indonesia (F2)
3. Dengan bantuan Dashboard ini saya dapat menerima informasi dengan mudah (F3)

*Usability*:
1. Dashboard ini mudah digunakan (U1)
2. Prosedur pengoperasian Dashboard mudah dipahami (U2)

*Aesthetics*:
1. Dashboard ini dirancang dengan kreatif (A1)
2. Desain Dashboard terlihat menarik (A2)

Responden yang dipilih adalah mahasiswa STIS yang dipilih secara random. Didapat 29 mahasiswa dengan 9 perempuan dan 20 laki-laki.

Barikut tabel *summary* pertanyaan evaluasi

| Pertanyaan  | Rata-rata | Standar Deviasi |
| ------------- | ------------- | ------------- |
| F1  | 4.379310 | 0.6768516 |
| F2  | 3.965517 | 1.0170953 |
| F3  | 4.310345 | 0.9298021 |
| U1  | 4.344828 | 0.7209053 |
| U2  | 4.275862 | 0.8407714 |
| A1  | 4.137931 | 0.7427814 |
| A2  | 4.172414 | 0.8048498 |

 Semua pertanyaan memiliki mean diatas 4 dan standar deviasi dibawah 1 selain F2. Ini berarti evaluasi di F2 tidak sebaik di pertanyaan lain.
 
 | Dimensi  | Rata-rata |
| ------------- | ------------- |
| *Usefulness*  | 4.218391 |
| *Usability*   | 4.310345 |
| *Aesthetics*  | 4.155172 |
 
Dapat disimpulkan bahwa sebagian besar orang setuju dengan ketiga dimensi. Artinya dashboard informasi ini berguna, bisa digunakan, dan menarik.
