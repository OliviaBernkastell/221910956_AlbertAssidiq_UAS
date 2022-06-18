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
1. Masukkan Kedua kelompok
