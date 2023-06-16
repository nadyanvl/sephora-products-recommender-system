# Laporan Proyek Machine Learning (Predictive Analytics) - Nadya Novalina
## Judul: Prediksi Harga Saham Unilever Indonesia menggunakan LSTM
## Domain Proyek
Perkembangan pasar saham dan investasi semakin menarik minat banyak orang. Salah satu tantangan yang dihadapi oleh para investor adalah memprediksi pergerakan harga saham di masa depan untuk mengambil keputusan investasi yang lebih baik. Dalam proyek ini, dilakukan prediksi harga saham perusahaan Unilever Indonesia menggunakan metode LSTM (Long Short-Term Memory) berdasarkan data historis yang diperoleh dari Yahoo Finance open dataset. Tujuan utama proyek ini adalah membantu investor dalam mengoptimalkan keputusan investasi mereka dengan memberikan prediksi harga saham yang lebih akurat.

LSTM digunakan dalam proyek ini karena dapat mengatasi data time series yang kompleks, seperti harga saham, dan mampu menangkap pola dan tren jangka panjang dalam data historis.
Penelitian dalam beberapa tahun terakhir juga telah menunjukkan bahwa model jaringan LSTM sangat efektif dalam prediksi harga saham. LSTM mampu menangkap pola yang kompleks dalam data time series, termasuk pergerakan harga saham yang cenderung berubah-ubah dan dipengaruhi oleh banyak faktor. 

Beberapa penelitian dalam beberapa tahun terakhir telah menunjukkan efektivitas model jaringan LSTM dalam prediksi harga saham. Sebagai contoh, penelitian [1] menggunakan LSTM untuk prediksi saham dan mencapai nilai RMSE sebesar 0.00918 pada parameter Open/Close dengan epoch 500. Penelitian [2] juga menggunakan LSTM untuk prediksi saham dan memperoleh nilai MSE sebesar 0.0015. Selain itu, penelitian [3] membandingkan model LSTM, ARIMA, dan ANN untuk prediksi saham dengan hasil yang menunjukkan bahwa LSTM memberikan performa yang lebih baik.

Dengan memanfaatkan metode LSTM, proyek ini bertujuan untuk memberikan prediksi harga saham Unilever Indonesia yang lebih akurat, terutama dalam jangka waktu yang lebih panjang. Hal ini akan membantu para investor dalam membuat keputusan investasi yang lebih baik dan mengoptimalkan hasil investasi mereka.

## Business Understanding
Proyek ini bertujuan untuk mengembangkan model prediksi harga saham perusahaan Unilever Indonesia menggunakan metode LSTM. Model ini akan dilatih menggunakan data historis harga saham Unilever Indonesia dari IHGS untuk memprediksi pergerakan harga saham di masa depan pada data uji.

Dengan menggunakan model prediksi yang akurat, investor dapat memperoleh wawasan mendalam tentang pergerakan harga saham Unilever Indonesia. Informasi ini membantu investor dalam pengambilan keputusan investasi yang lebih cerdas, menghindari keputusan impulsif, serta mengendalikan risiko secara efektif. Selain itu, dengan prediksi yang akurat, investor dapat mengoptimalkan hasil investasi mereka.

Secara keseluruhan, penggunaan model prediksi harga saham yang akurat memiliki dampak positif yang signifikan. Investor dapat membuat keputusan investasi yang lebih cerdas, mengendalikan risiko dengan lebih baik, dan meningkatkan potensi keuntungan dalam pasar saham. Selain itu, hal ini juga meningkatkan kepercayaan investor terhadap keputusan investasi mereka, membantu mereka mencapai tujuan investasi, dan meningkatkan hasil investasi secara keseluruhan.

### Problem Statements
Investor seringkali sulit memprediksi harga saham (contoh: Unilever Indonesia) di masa depan, yang membuat mereka kesulitan dalam mengambil keputusan investasi. Pasar saham seringkali berfluktuasi dengan cepat dan banyak faktor yang memengaruhi harga saham, sehingga sulit untuk membuat prediksi yang akurat. Oleh karena itu, dibutuhkan pendekatan yang dapat membantu investor dalam memprediksi harga saham Unilever Indonesia dengan lebih baik.

### Goals
- Mengembangkan model prediksi harga saham yang akurat menggunakan metode LSTM.
- Membantu investor dalam membuat keputusan investasi yang lebih baik berdasarkan prediksi harga saham yang akurat.
- 
### Solution statements
- Melakukan tuning parameter pada model LSTM, seperti ukuran lapisan LSTM, dropout rate, dan jumlah neuron pada hidden layer.
- Mengimplementasikan model LSTM yang lebih kompleks, dengan menambahkan lapisan LSTM tambahan, peningkatan jumlah neuron pada hidden layer.
- Melakukan preprocessing data dengan menggunakan MinMaxScaler untuk melakukan Feature Scaling pada data harga saham. Dengan menggunakan MinMaxScaler, skala data harga saham dapat disesuaikan sehingga nilainya berada dalam rentang 0 hingga 1. Hal ini membantu menghindari perbedaan skala yang signifikan antara fitur-fitur dan memastikan pengaruh yang seimbang terhadap model LSTM.

## Data Understanding
Dataset yang digunakan berasal dari  [Yahoo Finance Dataset](https://finance.yahoo.com/quote/UNVR.JK?p=UNVR.JK&.tsrc=fin-srch). Dataset ini berisi data historis harian saham Unilever Indonesia dari 3 Januari 2005 hingga 9 Juni 2023. Dataset terdiri dari 4563 baris data dan 7 kolom yaitu: Date, Open, Low, High, Close, Adj Close, dan Volume.

### Detail variabel-variabel pada UNVR dataset adalah sebagai berikut:
- Date = Tanggal dan waktu transaksi saham
- Open = Harga pembukaan
- Low = Harga terendah dalam rentang waktu
- High = Harga tertinggi dalam rentang waktu
- Close = Harga penutupan
- Adj Close = Harga penutupan setelah penyesuaian untuk semua pemisahan dan pembagian dividen yang berlaku
- Volume = Total volume yang diperdagangkan dalam rentang waktu tersebu

## Data Preparation
Data historis harga saham Unilever Indonesia dari IHGS diimpor menggunakan library Pandas dan disajikan dalam bentuk DataFrame. Selanjutnya, dilakukan pemahaman terhadap data tersebut dengan menampilkan grafik harga saham Unilever Indonesia dari waktu ke waktu. Grafik ini membantu dalam melihat tren dan pola pergerakan harga saham perusahaan.
Berikut grafik visualisasi dataset:

![image](https://github.com/nadyanvl/StockPricePrediction/blob/main/assets/Grafik%20UNVR.png)

Setelah itu, dilakukan Feature Scaling menggunakan MinMaxScaler untuk menormalkan data harga saham sebelum dimasukkan ke dalam model LSTM. 

Data juga dibagi menjadi data latih (train) dan data uji (test) dengan perbandingan 80:20 menggunakan fungsi split_data. Dengan menggunakan 80% data sebagai data latih, model dapat belajar dari sebagian besar pola dan tren dalam data yang tersedia. Hal ini membantu dalam membangun model yang lebih mampu melakukan generalisasi pada data baru. Dan dengan menyisihkan 20% data sebagai data uji, kita memiliki set data yang independen untuk menguji kinerja model yang telah dilatih. Data uji yang tidak digunakan dalam proses pelatihan memberikan ukuran yang lebih objektif tentang seberapa baik model dapat menggeneralisasi pada data yang belum pernah dilihat sebelumnya dan dapat mengidentifikasi apakah model memiliki masalah overfitting atau tidak.

## Modeling
Proyek ini menggunakan model LSTM (Long Short-Term Memory) untuk memprediksi harga saham Unilever Indonesia. Model ini dikembangkan menggunakan TensorFlow dengan Sequential API. LSTM adalah jenis arsitektur jaringan saraf rekurensi (RNN) yang secara khusus dirancang untuk memproses data berurutan, seperti data harga saham. Keunggulan LSTM terletak pada kemampuannya dalam menangani masalah memori jangka panjang, di mana ia dapat mengingat dan menggunakan informasi masa lalu untuk memprediksi masa depan. Dalam LSTM, terdapat sel memori yang menggantikan neuron tradisional di lapisan tersembunyi jaringan. Dengan adanya sel memori ini, jaringan mampu menghubungkan informasi jarak jauh dalam urutan waktu, memungkinkan pemahaman yang dinamis terhadap struktur data dari waktu ke waktu, serta memberikan kemampuan prediksi yang lebih akurat.

Model LSTM yang dikembangkan memiliki beberapa layer, yaitu layer LSTM, Dropout, dan Dense. Ukuran lapisan LSTM, dropout rate, dan jumlah neuron pada hidden layer diubah untuk mencari konfigurasi yang optimal. Hal ini bertujuan untuk meningkatkan performa model dalam memprediksi harga saham dengan lebih akurat.
Detail Model sebagai berikut:

![image](https://github.com/nadyanvl/StockPricePrediction/blob/main/assets/Model%20UNVR.png)

Proses pelatihan model dilakukan dengan mengkompilasi model menggunakan optimizer Adam dengan learning rate 0.001 dan loss function Huber. Selama pelatihan, digunakan callbacks EarlyStopping untuk menghentikan pelatihan jika mae pada data validasi sudah cukup kecil.

## Evaluation
Evaluasi model dilakukan menggunakan data uji. Prediksi harga saham dilakukan pada data uji dan hasilnya dibandingkan dengan harga saham aktual, serta dilakukan plotting grafik harga saham aktual dan harga saham yang diprediksi.

![image](https://github.com/nadyanvl/StockPricePrediction/blob/main/assets/Prediksi%20UNVR.png)

Beberapa metrik evaluasi digunakan untuk mengukur performa model prediksi harga saham seperti Mean Absolute Error (MAE), Root Mean Square Error (RMSE), dan Mean Absolute Percentage Error (MAPE). 

- Mean Absolute Error (MAE): selisih absolut rata-rata antara nilai yang diprediksi oleh model (prediksi dalam sampel satu langkah ke depan) dan data historis yang diamati.
- Root Mean Square Error (RMSE): Akar kuadrat dari MSE. MSE adalah jumlah selisih kuadrat antara nilai yang diprediksi oleh model dan nilai yang diamati, yang kemudian dibagi dengan jumlah titik data historis dikurangi jumlah parameter dalam model. 
- MAPE (Mean Absolute Percentage Error): Selisih persentase absolut rata-rata antara nilai yang diprediksi oleh model dan nilai data yang diamati.

Metrik evaluasi ini memberikan gambaran sejauh mana model dapat memprediksi harga saham Unilever Indonesia dengan akurat. Semakin rendah nilai MAE dan RMSE, semakin baik performa model dalam melakukan prediksi yang akurat. 

Hasil evaluasi yang diperoleh adalah sebagai berikut:
| Metrics  | Value |
| ------------- | ------------- |
| MAE (Mean Avsolute Error)  | 0.009871991375308926  |
| RSME (Root Mean Squared Error)  | 0.013863547909730151  |
| MAPE (Mean Absolute Percent Error)  | 0.017773489787324806  |

Model yang telah dibangun menghasilkan hasil evaluasi yang baik dalam memprediksi harga saham. MAE, RMSE, dan MAPE yang rendah menunjukkan bahwa model memiliki tingkat kesalahan yang rendah dan mampu mendekati nilai sebenarnya dengan akurasi yang baik.

## Kesimpulan
Berdasarkan hasil evaluasi, model yang telah dibangun menunjukkan performa yang baik dalam memprediksi harga saham. Dalam melakukan evaluasi model, MAE, RMSE, dan MAPE yang rendah menunjukkan bahwa model memiliki tingkat kesalahan yang rendah dan mampu mendekati nilai sebenarnya dengan akurasi yang baik.

## Daftar Pustaka
[[1]](https://www.ijsr.net/archive/v6i4/ART20172755.pdf) M. Roondiwala, H. Patel, and S. Varma, “Predicting Stock Prices Using LSTM,” International Journal of Science and Research (IJSR) ISSN, vol. 6, no. 4, pp. 2319–7064, 2017, Available: https://www.ijsr.net/archive/v6i4/ART20172755.pdf
[[2]](https://core.ac.uk/download/pdf/270292706.pdf) A. Arfan and D. Lussiana, “Prediksi Harga Saham Di Indonesia Menggunakan Algoritma Long Short-Term Memory,” Universitas Gunadarma Jl. Margonda Raya No, vol. 3, no. 1, pp. 2581–2327, 2019, Accessed: Jun. 16, 2023. [Online]. Available: https://core.ac.uk/download/pdf/270292706.pdf
[[3]](https://doi.org/10.1051/e3sconf/202021801026) Q. Ma, “Comparison of ARIMA, ANN and LSTM for Stock Price Prediction,” E3S Web of Conferences, vol. 218, p. 01026, 2020, doi: https://doi.org/10.1051/e3sconf/202021801026.
