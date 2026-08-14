### **6.  Bab 2. Pemahaman Data dan Pra Pemrosesan Data** 

- 2.1 Deskripsi dan Eksplorasi Data 

   - Sumber data 

   - Jenis data dan karakteristiknya 

   - Ulasan kualitas data 

   - Eksplorasi data ( _Exploratory Data Analysis_ ), tampilkan grafik dan _insight_ -nya 

- 2.2 Pra-pemrosesan Data ( _cleaning, encoding, scaling, augmenting_ , dll sesuai kebutuhan) 

- 2.3 Penentuan Model 

# **<u>Struktur Penilaian:</u>** 

- **Assignment I (30%)** → **fokus kepada rencana eksperimen mulai dari pengumpulan data,** **_preprocessing,_ hingga penentuan model** 

- _Assignment_ II (30%) → fokus kepada pengembangan model (bandingkan minimal 2 model) atau _training_ dan evaluasi model 

- _Final Project_ (AOL) (40%) → fokus pada hasil revisi _project_ dan pengembangan _end-to-end machine learning system,_ beserta saran pengembangan ke depannya 

3 | P a g e 

BINUS UNIVERSITY GRADUATE PROGRAM 

**Daftar Isi** 

## **Daftar Gambar** 

|No.|Judul Gambar|Halaman/Bagian|
|---|---|---|
|Gambar 1|Distribusi Kelas Target Machine Failure dan Frekuensi per Failure Mode|Bab 2.1 Eksplorasi Data|
|Gambar 2|Distribusi Fitur Sensor per Kelas Kegagalan (KDE Plot)|Bab 2.1 Eksplorasi Data|
|Gambar 3|Boxplot Fitur Sensor: Normal vs Machine Failure|Bab 2.1 Eksplorasi Data|
|Gambar 4|Heatmap Korelasi Fitur Sensor vs Machine Failure|Bab 2.1 Analisis Korelasi|
|Gambar 5|Scatter Plot Zona Kegagalan: RPM vs Torque dan Tool Wear vs Torque|Bab 2.1 Analisis Korelasi|
|Gambar 6|Deteksi dan Penanganan Outlier: Sebelum vs Sesudah Winsorization|Bab 2.2 Pra-Pemrosesan|
|Gambar 7|Distribusi Kelas Machine Failure: Sebelum vs Sesudah SMOTE|Bab 2.2 Pra-Pemrosesan|
|Gambar 8|KDE Distribusi Fitur Turunan: Power, Strain, dan Temp_diff|Bab 2.2 Feature Engineering|
|Gambar 9|Flowchart Pipeline Eksperimen Predictive Maintenance|Bab 2.3 Penentuan Model|



## **Daftar Tabel** 

|No.|Judul Tabel|Halaman/Bagian|
|---|---|---|
|Tabel 1|Informasi Dataset AI4I 2020|Bab 2.1|
|Tabel 2|Deskripsi Lengkap 14 Fitur Dataset|Bab 2.1|
|Tabel 3|Statistik Deskriptif Fitur Sensor Numerik|Bab 2.1|
|Tabel 4|Distribusi Kelas Target Machine Failure|Bab 2.1|
|Tabel 5|Frekuensi dan Persentase per Failure Mode|Bab 2.1|
|Tabel 6|Korelasi Fitur terhadap Machine Failure|Bab 2.1|
|Tabel 7|Ringkasan Kualitas Data|Bab 2.1|
|Tabel 8|Kolom yang Dihapus dan Alasannya|Bab 2.2|
|Tabel 9|Rencana Feature Engineering|Bab 2.2|
|Tabel 10|Rencana Penanganan Outlier|Bab 2.2|
|Tabel 11|Rencana Encoding Fitur Kategorikal|Bab 2.2|
|Tabel 12|Rencana Standardisasi Fitur|Bab 2.2|
|Tabel 13|Distribusi Kelas Sebelum dan Sesudah SMOTE|Bab 2.2|
|Tabel 14|Pembagian Dataset Train/Validasi/Test|Bab 2.2|



5 | P a g e 

|Tabel 15|Perbandingan Karakteristik Model|Bab 2.3|
|---|---|---|
|Tabel 16|Rencana Hyperparameter yang Dioptimalkan|Bab 2.3|
|Tabel 17|Metrik Evaluasi dan Prioritas Konteks Manufaktur|Bab 2.3|
|Tabel 18|Ringkasan Pipeline Eksperimen|Bab 2.3|



6 | P a g e 

## **Bab 1. Pendahuluan** 

## **1.1 Latar Belakang Masalah** 

Dalam era Industri 4.0, keberlanjutan operasional mesin produksi merupakan faktor penentu daya saing perusahaan manufaktur. Kegagalan mesin yang tidak terduga (unplanned downtime) menyebabkan kerugian finansial yang sangat besar  mulai dari biaya perbaikan darurat, penghentian lini produksi, hingga keterlambatan pengiriman yang merusak reputasi bisnis. Pendekatan konvensional berupa _reactive maintenance_ (perbaikan setelah kerusakan) dan _preventive maintenance_ (perbaikan terjadwal) terbukti tidak efisien: reactive maintenance menanggung biaya kerusakan besar, sementara preventive maintenance sering mengganti komponen yang sebenarnya masih layak pakai 

_Predictive Maintenance_ (PdM) berbasis machine learning menawarkan paradigma baru: memprediksi kapan dan jenis kegagalan apa yang akan terjadi berdasarkan data sensor real-time dari mesin. Dengan demikian, intervensi teknis dapat dilakukan tepat waktu  tidak terlalu dini dan tidak terlambat. Studi menunjukkan bahwa implementasi PdM berhasil meningkatkan efisiensi operasional secara signifikan dan mengurangi downtime tak terencana di berbagai sektor industri, dari otomotif hingga manufaktur baja.[3][1] 

Penelitian ini mengangkat permasalahan **prediksi kegagalan mesin industri sebagai masalah klasifikasi** menggunakan dataset AI4I 2020 Predictive Maintenance yang mencerminkan kondisi operasional mesin milling industri nyata. Model prediksi yang dibangun diharapkan dapat menjadi fondasi sistem peringatan dini (early warning system) bagi tim maintenance di lantai produksi.[5] 

## **1.2 Tujuan dan Ruang Lingkup** 

## **Tujuan Penelitian:** 

- a) Mengidentifikasi parameter sensor mesin (suhu, torsi, kecepatan, keausan alat) yang paling berkontribusi terhadap kegagalan mesin 

- b) Membangun model prediksi klasifikasi biner: apakah mesin akan mengalami kegagalan atau beroperasi normal 

- c) Membandingkan performa minimal dua algoritma machine learning dalam menangani data imbalanced (kegagalan mesin jauh lebih jarang dari kondisi normal) 

7 | P a g e 

- d) Mengidentifikasi jenis moda kegagalan (failure modes) yang paling sering terjadi sebagai 

dasar kebijakan maintenance berbasis risiko 

## **Ruang Lingkup:** 

1. **Dataset** : AI4I 2020 Predictive Maintenance Dataset (UCI Machine Learning Repository / Kaggle) 

2. **Target variabel primer** : <mark>Machine failure</mark> (biner: 1 = Gagal, 0 = Normal) 

3. **Target variabel sekunder (opsional)** : Multi-class failure modes (TWF, HDF, PWF, OSF, RNF) 

4. **Jenis masalah** : Binary Classification (utama) + Multi-class Classification (lanjutan) 

5. **Model yang dibandingkan** : Random Forest dan XGBoost 

6. **Baseline** : Logistic Regression 

7. **Evaluasi** : Accuracy, Precision, Recall, F1-Score, ROC-AUC 

8 | P a g e 

## **Bab 2. Pemahaman Data dan Pra-Pemrosesan Data** 

## **2.1 Deskripsi dan Eksplorasi Data** 

## **Sumber Data** 

Dataset yang digunakan adalah **AI4I 2020 Predictive Maintenance Dataset** , dikembangkan oleh Stephan Matzka dari HTW Berlin untuk mensimulasikan kondisi operasional mesin milling industri yang realistis. Dataset ini tersedia secara publik di UCI Machine Learning Repository dan Kaggle.[4] 

**Tabel 1 Informasi Dataset AI4I 2020** 

|**Atribut**|**Keterangan**|
|---|---|
|**Dataset**||
|**Nama**<br>**Dataset**|AI4I 2020 Predictive Maintenance Classification Dataset|
|**Pengembang**|Stephan Matzka, HTW Berlin, Jerman|
|**Sumber**<br>**Primer**|UCI Machine Learning Repository (Dataset ID: 601)|
|**Link Kaggle**|https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-<br>classification|
|**Link UCI**|https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset|
|**Lisensi**|CC BY 4.0|
|**Konteks**<br>**Industri**|Milling machine (mesin frais) di lingkungan manufaktur|



Dataset ini sengaja digunakan karena data predictive maintenance nyata dari industri sangat sulit diperoleh baik karena rahasia bisnis maupun regulasi privasi industri. Melihat dataset AI4I 2020 dirancang agar secara statistik merepresentasikan pola kegagalan mesin industri yang sesungguhnya, sehingga valid sebagai benchmark akademik maupun pengembangan model produksi.[6] 

9 | P a g e 

## **Jenis Data dan Karakteristiknya** 

Struktur lengkap dataset AI4I 2020 adalah sebagai berikut:[8][4] 

|Parameter|Nilai|
|---|---|
|**Jumlah Baris (Observasi)**|10.000 baris|
|**Jumlah Kolom (Fitur)**|14 kolom|
|**Tipe Data**|Numerik (float, integer) dan Kategorikal (string)|
|**Missing Values**|Tidak ada|
|**Target Variabel Primer**|Machine failure(0 = Normal, 1 = Gagal)|
|**Target Variabel Sekunder**|5 Failure Modes (TWF, HDF, PWF, OSF, RNF)|
|**Rasio Kelas Target Primer**|~96.6% Normal vs ~3.4% Failure (sangat imbalanced)|



## **Deskripsi Lengkap 14 Fitur Dataset:** 

Berdasarkan hasil loading data di Google Colab menggunakan <mark>pd.read_csv()</mark> , dataset AI4I 2020 memiliki dimensi **(10.000, 14)** artinya 10.000 baris observasi dan 14 kolom fitur.[5] 

# Block 1 — Import & Load Data import pandas as pd import numpy as np import matplotlib.pyplot as plt import seaborn as sns from sklearn.preprocessing import StandardScaler from sklearn.model_selection import train_test_split, StratifiedKFold from sklearn.linear_model import LogisticRegression from sklearn.ensemble import RandomForestClassifier from xgboost import XGBClassifier from imblearn.over_sampling import SMOTE from sklearn.metrics import classification_report, confusion_matrix, roc_auc_score import warnings warnings.filterwarnings('ignore') 

df = pd.read_csv('ai4i2020.csv') 

10 | P a g e 



|UDI<br>Product<br>ID<br>Type<br>Air temperature<br>[K]<br>Process temperature<br>[K]|Rotational speed<br>[rpm]|Torque|[Nm]<br>Tool wear<br>[min]|Machine failure<br>TWF<br>HDF<br>PWF<br>OSF<br>RNF|
|---|---|---|---|---|
|°<br>1<br>M14860<br>M<br>298.1<br>308.6|1551||428<br>ie}|ie}<br>ie}<br>ie)<br>fe)<br>ie}<br>ie}|
|1<br>2<br>L47181<br>L<br>298.2<br>308.7|1408||46.3<br>3|ie}<br>ie}<br>ie}<br>te}<br>ie}<br>ie}|
|a<br>3<br>L47182<br>L<br>298.1<br>308.5|1498||49.4<br>5|0<br>ie)<br>fe)<br>ie)<br>fe)<br>fe)|
|3<br>4<br>L47183<br>E<br>298.2<br>308.6|1433||39.5<br>7|ie}<br>ie}<br>ie}<br>ie}<br>ie}<br>ie}|
|4<br>5<br>L47184<br>L<br>298.2<br>308.7|1408||40.0<br>9|ie)<br>ie)<br>ie)<br>ie}<br>ie)<br>ie)|









## **Ulasan Kualitas Data** 

## **Kekuatan dataset:** 

- Tidak ada missing values pipeline preprocessing lebih efisien 

- 10.000 observasi memberikan ukuran yang cukup representatif untuk modeling ML 

- Fitur sensor memiliki distribusi statistik yang jelas dan terdokumentasi (random walk, distribusi normal) 

- Multi-label failure modes memungkinkan analisis yang lebih mendalam (binary + multi-class) 

- Digunakan dalam banyak jurnal akademik bidang Predictive Maintenance dan Industry 4.0 

## **Tabel .7 Ringkasan Kualitas Data** 

|**Aspek**|**Status**|**Keterangan**|
|---|---|---|
|Missing Values|Tidak ada|df.isnull().sum()menghasilkan 0 untuk semua kolom|
|Tipe Data|Konsisten|Float64, Int64, dan Object (sesuai karakteristik fitur)|
|Imbalanced Class|Sangat Ekstrem|Rasio Normal:Failure ≈ 96.6% : 3.4%|
|Kolom Tidak Informatif|Ada 2 kolom|UDI (hanya index) dan Product ID (redundan dengan Type)|
|Outlier|Ada|Terutama pada Rotational speed [rpm]|
|Dataset Sintetis|Perlu dicatat|Bukan data sensor fisik nyata, namun statistik realistis|



## **Tantangan/Keterbatasan:** 

- **Ketidakseimbangan kelas ekstrem** : hanya ~3.4% observasi merupakan kegagalan mesin rasio ~28:1 antara kelas normal dan kelas failure. Ini adalah tantangan imbalanced data yang paling signifikan di antara ketiga studi kasus[9] 

- Dataset bersifat sintetis (bukan data sensor nyata dari mesin fisik), sehingga pola kegagalannya lebih "bersih" dari data industri sesungguhnya[6] 

- Beberapa failure modes sangat jarang terjadi: RNF hanya 0.1% dari total data hampir tidak bisa dimodelkan secara terpisah 

12 | P a g e 

## **Eksplorasi Data (Exploratory Data Analysis)** 

## **A. Statistik Deskriptif Fitur Numerik** 

**Tabel 3. Statistik Deskriptif Fitur Sensor Numerik** 

|**Fitur**|**Mean**|**Min**|**Max**|**Std Dev**|**Distribusi**|
|---|---|---|---|---|---|
|Air temperature [K]|~300.0|295.3|304.5|~2.0|Near normal|
|Process temperature [K]|~310.0|305.7|313.8|~1.5|Near normal|
|Rotational speed [rpm]|~1539|1168|2886|~179.3|Right-skewed|
|Torque [Nm]|~39.99|3.8|76.6|~9.97|Near normal|
|Tool wear [min]|~107.9|0|253|~63.7|Near uniform|



## **B. Distribusi Kelas Target (Machine Failure)** 

**Tabel 4. Distribusi Kelas Target Machine Failure** 

|**Kelas**|**Jumlah**|**Persentase**|
|---|---|---|
|0 – Normal|~9.661|~96.6%|
|1 – Machine Failure|~339|~3.4%|



Rasio imbalanced yang ekstrem ini merupakan tantangan utama yang harus ditangani secara serius sebelum training model. Tanpa penanganan, model akan cenderung selalu memprediksi "Normal" dan tetap mendapatkan accuracy semu ~96% namun gagal total dalam mendeteksi kegagalan mesin.[9] 

## **C. Distribusi Failure Modes (Multi-label)** 

**Tabel.5 Frekuensi dan Persentase per Failure Mode** 

|**Failure Mode**|**Kode**|**Deskripsi**|**Jumlah Kasus**|**Persentase**|
|---|---|---|---|---|
|Heat Dissipation Failure|HDF|Kegagalan sistem pendinginan|~115|~1.15%|
|Overstrain Failure|OSF|Beban mekanis berlebih|~98|~0.98%|
|Power Failure|PWF|Daya di luar rentang aman|~95|~0.95%|
|Tool Wear Failure|TWF|Keausan alat potong berlebih|~46|~0.46%|



13 | P a g e 





<!-- Start of picture text -->
Distribusi Kelas Target: Machine Failure Frekuensi per Failure Mode<br>10000<br>HDF 115<br>8000<br>OsF 98<br>6000<br>€<br>S8 PWF 95<br>4000<br>TWF 46<br>2000<br>RNF 19<br>oO 0 1 () 20 40 60 80 100 120<br>Machine failure<br><!-- End of picture text -->





<!-- Start of picture text -->
Distribusi Fitur Sensor per Kelas Kegagalan<br>Distribusi: Air temperature [K] Distribusi: Process temperature [K] Distribusi: Rotational speed [rpm]<br>3 fFailure=0 ©) failure=0 3 failure=0<br>(3 Failure=1 ©) failure=1 0.0030 (3 failure=1<br>0.20 0.30<br>025 0.0025<br>0.15<br>a8>coro a8>i0.20os a&>c0.00200.0015<br>0.10 0.0010<br>0.05<br>0.05 0.0005<br>0.00 294-296 «= 298 = 300. 302-304 306 0.00 306 308 310 312 314 0.0000 1000 1500 2000 2500 3000<br>Air temperature [K] Process temperature [K] Rotational speed [rpm]<br>Distribusi: Torque [Nm] Distribusi: Too! wear [min] Lo<br>0.040 [= failure=0 0.007: = failure=o<br>= failure=1 [= failure=1<br>0.035<br>0.006 0.8<br>0.030<br>0.005<br>0.025 0.6<br>2 2 0.004<br>a§ 0.020 &5<br>0.003 0.4<br>0.015<br>0.002<br>0.010<br>0.2<br>0.005 0.001<br>0.000 () 20 40 60 80 0.000 -50 0 50 100 150 200 250 300 0.00.0 0.2 0.4 0.6 08 10<br>Torque [Nm] Tool wear [min]<br><!-- End of picture text -->





<!-- Start of picture text -->
Distribusi Fitur Sensor: Normal vs Failure<br>Boxplot: Air temperature [K] Boxplot: Process temperature [K] Boxplot: Rotational speed [rpm]<br>304 314 g<br>313 2750 g i<br>312 2500 8<br>o=x Zg 311 EE 2250 °°<br>rd @ 310 Q<br>3 0 = = 2000 °<br>8 298 &3 308 =B& 1750<br>1500<br>307<br>296 306 8 1250<br>0) 1 0) 1 0) 1<br>Machine failure Machine failure Machine failure<br>80 Boxplot: Torque [Nm] Boxplot: Tool wear [min] Loa<br>250<br>70<br>08<br>60 200<br>= 50 =c 150 0.6<br>"30e 3e 100 0.4<br>20 8 50 0.2<br>10 i<br>8 0<br>() 1 0 1 0.0 0.0 0.2 0.4 0.6 08 1.0<br>Machine failure Machine failure<br><!-- End of picture text -->

Gambar 3 mengkonfirmasi temuan sebelumnya: kelas Failure (1) memiliki median Torque yang jauh lebih tinggi (~52 Nm) dibandingkan kelas Normal (0) (~39 Nm), serta Tool wear yang cenderung lebih besar. Yang menarik, **Rotational speed pada kelas Failure justru lebih rendah** (~1.380 rpm vs ~1.510 rpm), mengindikasikan bahwa mesin beroperasi pada torsi tinggi namun kecepatan rendah kombinasi yang berpotensi menyebabkan Overstrain Failure (OSF) dan Power Failure (PWF). Temuan ini menjadi justifikasi penting pembentukan fitur turunan <mark>Power = RPM × Torque</mark> pada tahap _feature engineering_ . 

## **E. Analisis Korelasi Antar Fitur** 

Analisis korelasi Pearson dilakukan untuk mengidentifikasi hubungan linear antar fitur sensor, mendeteksi potensi multikolinearitas, dan memahami fitur mana yang paling berkorelasi dengan target kegagalan mesin. 

**Tabel 6. Korelasi Fitur terhadap Machine Failure (Top 5)** 

|Fitur|Korelasi dengan Machine Failure|Arah|Interpretasi|
|---|---|---|---|
|Torque [Nm]|+0.19|Positif|Torsi tinggi → risiko failure meningkat|
|Tool wear [min]|+0.11|Positif|Keausan alat tinggi → risiko failure meningkat|
|Air temperature [K]|+0.08|Positif|Suhu udara tinggi → sedikit berpengaruh|
|Process temperature [K]|+0.04|Positif|Suhu proses → lemah secara individual|
|Rotational speed [rpm]|-0.04|Negatif|RPM tinggi → cenderung lebih aman (torsi rendah)|



# Block 5 — EDA: Heatmap Korelasi plt.figure(figsize=(10, 8)) 

corr = df[num_cols + ['Machine failure']].corr() 

mask = np.triu(np.ones_like(corr, dtype=bool)) 

sns.heatmap(corr, annot=True, fmt='.2f', cmap='coolwarm', 

mask=mask, vmin=-1, vmax=1, linewidths=0.5) plt.title('Heatmap Korelasi Fitur Sensor vs Machine Failure') plt.tight_layout() 

plt.savefig('fig4_correlation_heatmap.png', dpi=150) plt.show() 

17 | P a g e 

Heatmap Korelasi Fitur Sensor vs Machine Failure 

1.00 



<!-- Start of picture text -->
Air temperature [K] -<br><!-- End of picture text -->



<!-- Start of picture text -->
0.75<br><!-- End of picture text -->



<!-- Start of picture text -->
Process temperature [K] 0.50<br>- 0.25<br>Rotational speed [rpm] - 0.02 0.02<br>- 0.00<br>Torque [Nm] - 0.01 -0.01 -0.88<br>-—-0.25<br>Tool wear [min] - 0.01 0.01 0.00 -0.00 -—0.50<br>—-0.75<br>Machine failure - 0.08 0.04 -0.04 0.19 0.11<br>\ \ \ \ \ \ —1.00<br>y vy = = 7 v<br>rsfa FiPa =5 —é E— 2oO<br>2 a = ¥ 5 rf<br>s 2 % > o rat<br>ouava a -a = =G<br>2E2= =2 28 =ic<br><ir=<br>2«<br>-5<br><!-- End of picture text -->





<!-- Start of picture text -->
Zona Kegagalan: RPM vs Torque (Power Zone) Zona Kegagalan: Tool Wear vs Torque (Strain Zone)<br>80 80<br>ee «6 Machine failure ° e e Machine failure<br>70 RNes re 70 e e ° Cg SS e - °<br>i v8 a) e ° bd ee eee o* @ « & 1<br>y 3 ka % »e*>VJ  Pe ° ase” e a «2 ‘ ao Ag a. Rs<br>69 604 pgiteae ° Ase.s 7B Giese... osm<br>e ° . e tes i , a4 Or ear ea eens og e re Yeo ~<<br>30 30 reset ee eee skies oe aie cea Oe Le weeneee?<br>oeeee eie Geptleoe cepna eats wepteeu canaR Te © °°%<br>2010 08° ae og 20 AAee9 ) ° Heme’,$5‘ tea neRNS©oS.MoBenmag ton umeeMsgs- 2 ORLSboooe Wsoie:p PerPhewageae |2 * aFoooSaeorootate fg&@_.° “og<br>%, 10 * e e<br>"ea rs e e e<br>1250 1500 1750 2000 2250 2500 2750 () 50 100 150 200 250<br>Rotational speed [rpm] Tool wear [min]<br><!-- End of picture text -->

penanganan imbalanced data → data splitting.[10] 

## **Penghapusan Kolom Tidak Informatif** 

Sebelum preprocessing dimulai, dua kolom yang tidak memiliki nilai prediktif dihapus dari dataset:[11] 

**Tabel 8. Kolom yang Dihapus dan Alasannya** 

|Kolom|Alasan Penghapusan|
|---|---|
|UDI|Hanya indeks urutan (1–10.000), bukan fitur operasional mesin|
|Product ID|Redundan dengan kolomType;hanya kombinasi kode kualitas + serial number|



## **Feature Engineering** 

Berdasarkan domain knowledge mekanika  mesin, tiga fitur turunan dibuat untuk menangkap interaksi antar fitur yang lebih bermakna secara teknis:[7] 

### **Tabel 9. Feature Engineering** 

|**Fitur**<br>**Turunan**|**Formula**|**Satuan**|**Justifikasi Domain Knowledge**|
|---|---|---|---|
|Power|Rotational speed × Torque|Watt|Daya mekanis aktual; mesin gagal saat power di luar rentang<br>aman|
|Strain|Torque × Tool wear|Nm·min|Beban kumulatif pada alat potong; indikator risiko OSF dan<br>TWF|
|Temp_diff|Process temperature − Air<br>temperature|Kelvin|Efisiensi pendinginan; nilai rendah → risiko HDF meningkat|



# Block 7 — Preprocessing: Feature Engineering + Encoding 

# Feature engineering berbasis domain knowledge mesin df['Temp_diff'] = df['Process temperature [K]'] - df['Air temperature [K]'] df['Power']     = df['Rotational speed [rpm]'] * df['Torque [Nm]'] 

df['Strain']    = df['Torque [Nm]'] * df['Tool wear [min]'] 

# Ordinal encoding untuk tipe produk (ada urutan logis: L < M < H) df['Type'] = df['Type'].map({'L': 0, 'M': 1, 'H': 2}) 

# Hapus kolom tidak informatif df.drop(['UDI', 'Product ID'], axis=1, inplace=True, errors='ignore') 

print("Shape setelah preprocessing:", df.shape)  # Output: (10000, 15) print(df.dtypes) 

20 | P a g e 

|Shape setelah preprocessi|ng:<br>(10000,<br>15)|
|---|---|
|Type|int64|
|Air temperature<br>[K]|Float64|
|Process temperature<br>[K]|float64|
|Rotational speed<br>[rpm]|int64|
|Torque<br>[Nm]|Float64|
|Tool wear [min]|int64|
|Machine failure|int64|
|TWF|int64|
|HDF|int64|
|PWF|int64|
|OSF|int64|
|RNF|int64|
|Temp_diff|float64|
|Power|Float64|
|Strain|Float64|
|dtype:<br>object||







<!-- Start of picture text -->
Distribusi Fitur Turunan (Feature Engineering) per Kelas Kegagalan<br>le-5 KDE: Power KDE: Strain KDE: Temp_diff<br>4.0 [23 Normal [3 Normal ] [3 Normal<br>(5 Machine Failure 0.00012 (5 Machine Failure (© Machine Failure<br>35 O4f 00°<br>0.00010<br>3.0<br>25 0.00008 03<br>20 A FS<br>a 4 a 0.00006 8 o2<br>15<br>0.00004<br>10 0.1<br>0.00002<br>0.5<br>0.0 0.00000 0.0<br>0 20000 40000 60000 80000 100000 120000 5000 0 5000 10000 15000 20000 7 8 9 10 n R 13<br>Power Strain Temp_diff<br><!-- End of picture text -->

**Tabel 10. Rencana Penanganan Outlier** 

|**Fitur**|**Outlier Ditemukan**|**Metode**<br>**Penanganan**|**Pertimbangan Domain**|
|---|---|---|---|
|Rotational speed<br>[rpm]|Ya (signifikan, >2.700<br>rpm)|Winsorization 1%|Nilai ekstrem mungkin kondisi abnormal<br>pra-failure|
|Torque [Nm]|Ya (ringan, <10 dan >70<br>Nm)|Winsorization 1%|Torsi ekstrem tinggi = indikator<br>kegagalan|
|Tool wear [min]|Tidak signifikan|Monitor saja|Distribusi near-uniform by design|
|Air/Process<br>temperature|Tidak signifikan|Monitor saja|Distribusi normal by design|



# Block 8 — Preprocessing: Deteksi & Winsorization Outlier from scipy.stats.mstats import winsorize 

all_num = ['Air temperature [K]', 'Process temperature [K]', 'Rotational speed [rpm]', 'Torque [Nm]', 'Tool wear [min]'] 

fig, axes = plt.subplots(2, 5, figsize=(20, 8)) for i, col in enumerate(all_num): df[[col]].boxplot(ax=axes[0, i]) axes[0, i].set_title(f'Sebelum\n{col[:15]}') df[col] = winsorize(df[col], limits=[0.01, 0.01]) df[[col]].boxplot(ax=axes[1, i]) axes[1, i].set_title(f'Sesudah\n{col[:15]}') plt.suptitle('Outlier: Sebelum vs Sesudah Winsorization', fontsize=13) plt.tight_layout() plt.savefig('fig6_outlier_treatment.png', dpi=150) plt.show() 

23 | P a g e 



<!-- Start of picture text -->
Outlier: Sebelum vs Sesudah Winsorization<br>Air Sebelumtemperature ProcessSebelumtempera RotationalSebelumspee TorqueSebelum[Nm] ToolSebelumwear [min]<br>ae 80 250 =><br>304 313 2750 70<br>312 2500 60 200<br>302<br>300 pt} 311310 22502000 50“0 150 1<br>298 309308 1750 | 3020 100 +<br>307 1500 a %°<br>296 306 150 — 10 ° +<br>Air temperature [K] Process temperature [K] Rotational speed [rpm] Torque [Nm] Tool wear [min]<br>Air Sesudahtemperature ProcessSesudahtempera RotationalSesudahspee TorqueSesudah[Nm] ToolSesudahwear [min]<br>304 313 2200 60 200<br>302 a311 2000 50 150<br>300 — 310 1800 40 |} 100<br>298 309 1600 an) 30<br>308 jt} 50<br>296 307 1400 +fT 20 °<br>Air temperature [K] Process temperature [K] Rotational speed [rpm] Torque [Nm] Tool wear [min]<br><!-- End of picture text -->



## **d. Data Standardization** 

Standardisasi fitur numerik diperlukan terutama untuk algoritma yang sensitif terhadap skala seperti Logistic Regression:[8] 

**Tabel 12. Rencana Standardisasi Fitur** 

|**Fitur**|**Di-scale?**|**Metode**|**Catatan**|
|---|---|---|---|
|Air temperature [K]|Ya (untuk LR)|StandardScaler|Rentang 295–304 K|
|Process temperature [K]|Ya (untuk LR)|StandardScaler|Rentang 306–314 K|
|Rotational speed [rpm]|Ya (untuk LR)|StandardScaler|Rentang 1.168–2.886 rpm|
|Torque [Nm]|Ya (untuk LR)|StandardScaler|Rentang 3.8–76.6 Nm|
|Tool wear [min]|Ya (untuk LR)|StandardScaler|Rentang 0–253 menit|
|Power, Strain, Temp_diff|Ya (untuk LR)|StandardScaler|Fitur turunan|
|Random Forest|Tidak perlu|—|Tree-based, invariant terhadap scaling|
|XGBoost|Tidak perlu|—|Tree-based, invariant terhadap scaling|



from sklearn.preprocessing import StandardScaler scaler = StandardScaler() 

X_train_scaled = scaler.fit_transform(X_train)  # fit hanya pada training X_val_scaled   = scaler.transform(X_val)         # transform saja (no fit) X_test_scaled  = scaler.transform(X_test)        # transform saja (no fit) 

## **e. Mengatasi Ketidakseimbangan Data** 

Ketidakseimbangan kelas merupakan tantangan terbesar dataset ini rasio ~96.6%:3.4% (Normal:Failure) setara dengan rasio ~28:1. Tanpa penanganan, model akan cenderung selalu memprediksi "Normal" dan tetap mendapatkan _accuracy_ semu ~96%  namun gagal total mendeteksi kegagalan mesin yang justru menjadi tujuan utama penelitian.[11] 

Tiga strategi dikombinasikan sesuai karakteristik masing-masing model:[13] 

# Block 9 — Preprocessing: Splitting + SMOTE 

X = df.drop(['Machine failure', 'TWF', 'HDF', 'PWF', 'OSF', 'RNF'], axis=1) 

y = df['Machine failure'] 

# Split stratified 

X_temp, X_test, y_temp, y_test = train_test_split( 

25 | P a g e 

X, y, test_size=0.20, random_state=42, stratify=y) 

X_train, X_val, y_train, y_val = train_test_split( 

X_temp, y_temp, test_size=0.125, random_state=42, stratify=y_temp) 

print(f"Train: {X_train.shape}, Val: {X_val.shape}, Test: {X_test.shape}") # Output: Train: (7000, 9), Val: (1000, 9), Test: (2000, 9) 

print(f"Distribusi kelas Train sebelum SMOTE:\n{y_train.value_counts()}") # Output: 0: 6763, 1: 237 

# Terapkan SMOTE hanya pada training set 

smote = SMOTE(random_state=42, k_neighbors=5, sampling_strategy=0.3) X_res, y_res = smote.fit_resample(X_train, y_train) 

print(f"Distribusi kelas Train sesudah SMOTE:\n{pd.Series(y_res).value_counts()}") # Output: 0: 6763, 1: 2028 

# Visualisasi perbandingan fig, axes = plt.subplots(1, 2, figsize=(10, 4)) 

y_train.value_counts().plot(kind='bar', ax=axes, 

color=['steelblue','tomato'], title='Sebelum SMOTE', rot=0) pd.Series(y_res).value_counts().plot(kind='bar', ax=axes[^1], color=['steelblue','salmon'], title='Sesudah SMOTE', rot=0) plt.suptitle('Distribusi Kelas: Sebelum vs Sesudah SMOTE') plt.tight_layout() plt.savefig('fig7_smote_comparison.png', dpi=150) plt.show() 

26 | P a g e 



<!-- Start of picture text -->
ees Train: (7000, 9), Val: (1000, 9), Test: (2000, 9)<br>Distribusi kelas Train sebelum SMOTE:<br>Machine failure<br>8 6763<br>1 237<br>Name: count, dtype: int64<br>Distribusi kelas Train sesudah SMOTE:<br>Machine failure<br>C) 6763|<br>1 2028<br>Name: count, dtype: int64<br>Distribusi Kelas: Sebelum vs Sesudah SMOTE<br>Sebelum SMOTE Sesudah SMOTE<br>7000 7000<br>6000 6000<br>5000 5000<br>4000 4000<br>3000 3000<br>2000 2000<br>1000 1000<br>00<br>01 0 1<br>Machine failure Machine failure<br><!-- End of picture text -->

## **f. Data Splitting (Train/Validasi/Test)** 

Stratified split memastikan proporsi kelas kegagalan yang kecil (~3.4%) terwakili secara proporsional di setiap subset:[2] 

**Tabel 14. Pembagian Dataset Train/Validasi/Test** 

|**Split**|**Proporsi**|**Jumlah Baris**|**Kasus Failure**|**Keterangan**|
|---|---|---|---|---|
|Training Set|70%|7.000 baris|~237 kasus|Untuk melatih model; SMOTE diterapkan di sini|
|Validation Set|10%|1.000 baris|~34 kasus|Untuk hyperparameter tuning|
|Test Set|20%|2.000 baris|~68 kasus|Evaluasi akhir  tidak disentuh selama training|



Selain pembagian hold-out ini, **5-Fold Stratified Cross-Validation** akan diterapkan pada training set untuk memaksimalkan pemanfaatan data dan mendapatkan estimasi performa model yang lebih robust.[15] 

## **2.3 Penentuan Model** 

Gambar 9 berikut menyajikan diagram alur ( _flowchart_ ) keseluruhan pipeline eksperimen yang dirancang untuk studi kasus Predictive Maintenance ini. Pipeline mencakup sembilan tahap berurutan mulai dari pengumpulan data hingga penarikan kesimpulan dan rekomendasi kebijakan maintenance. 

28 | P a g e 



<!-- Start of picture text -->
1. Data Collection<br>AI4I 2020 - 10.000 x 14- CC<br>BY 4.0<br>2. EDA<br>Deskriptif + Distribusi<br>failure - Histogram/KDE<br>Boxplot - Korelasi - Scatter<br>zona gagal<br>3. Pra-Pemrosesan<br>Drop UID & Product ID -<br>Power, Strain, Temp_diff<br>IQR + Winsorization - Type:<br>L/M/H > 0/1/2<br>4, Standardisasi<br>StandardScaler (Z-score)<br>Hanya untuk LR - Tree<br>models tanpa scaling<br>5. Imbalanced Data<br>96.6% Normal - 3.4% Failure<br>SMOTE scale_pos_weight = 28.5 class_weight='balanced'<br>strategy=0.3 - k=5 XGBoost RF &LR<br>6. Split Stratified<br>Train 70% - Val 10% - Test<br>20%<br>SMOTE hanya di Training<br>7. Modeling<br>XGBoost - Random Forest -<br>LR Baseline<br>GridSearchCV 5-Fold<br>Stratified<br>8. Evaluasi<br>Recall - F1 - ROC-AUC<br>Precision - Accuracy - CM -<br>SHAP<br>9. Kesimpulan<br>Model terbaik untuk Early<br>Warning<br>Feature importance —<br>Maintenance Policy<br><!-- End of picture text -->

## **Model 1: XGBoost Classifier (Extreme Gradient Boosting)** 

XGBoost merupakan pilihan terdepan untuk Predictive Maintenance berbasis data tabular sensor, didukung bukti performa paling komprehensif dalam berbagai studi. Pada AI4I 2020 dataset, XGBoost + SMOTE berhasil menjadi model paling optimal dalam menyeimbangkan Recall tinggi dengan Precision yang wajar, serta konsisten mengungguli model lain untuk kelas minoritas.[15][13] 

## **Justifikasi pemilihan XGBoost:** 

- **<mark>scale_pos_weight</mark>** <mark>:</mark> Parameter built-in yang secara langsung menangani class imbalance tanpa memerlukan SMOTE  nilai ~28.5 sesuai rasio kelas 

- **Regularisasi L1/L2 built-in** : Mencegah overfitting pada feature space yang diperkaya oleh feature engineering 

- **SHAP Values** : Sangat penting untuk explainability di lingkungan industri teknisi perlu memahami _mengapa_ mesin diprediksi akan gagal, bukan hanya _kapan_ [7] 

- **Kecepatan tinggi** dengan implementasi paralel efisien untuk iterasi eksperimen 

# Block 10 — Inisialisasi Model 

ratio = y_train.value_counts() / y_train.value_counts()[^1]  # ≈28.5 

# Model 1: XGBoost xgb = XGBClassifier( n_estimators=200, learning_rate=0.05, max_depth=6, scale_pos_weight=ratio,  # Menangani imbalanced eval_metric='logloss', random_state=42 ) 

# Model 2: Random Forest rf = RandomForestClassifier( n_estimators=200, max_depth=None, class_weight='balanced', random_state=42, n_jobs=-1 ) 

# Baseline: Logistic Regression lr = LogisticRegression( class_weight='balanced', 

30 | P a g e 



ses Semua model siap digunakan pada Assignment II XGBoost scale_pos_ weight: 28.54 

## **Tabel 16. Rencana Hyperparameter yang akan Dioptimalkan** 

|**Model**|**Hyperparameter**|**Rentang Nilai**|**Metode Tuning**|
|---|---|---|---|
|XGBoost|n_estimators|100, 200, 500|Grid Search CV|
|XGBoost|learning_rate|0.01, 0.05, 0.1|Grid Search CV|
|XGBoost|max_depth|4, 6, 8|Grid Search CV|
|XGBoost|scale_pos_weight|~28.5 (fixed dari data)|Derived dari rasio kelas|
|Random Forest|n_estimators|100, 200, 500|Grid Search CV|
|Random Forest|max_depth|None, 10, 20|Grid Search CV|
|Random Forest|class_weight|balanced, balanced_subsample|Grid Search CV|
|Semua Model|cv|5-Fold Stratified|StratifiedKFold|



## **Rencana Evaluasi Model (Assignment II)** 

**Tabel 17. Metrik Evaluasi dan Prioritas Konteks Manufaktur** 

|**Metrik**|**Formula**|**Prioritas**|**Justifikasi Konteks Manufaktur**|
|---|---|---|---|
|**Recall**|TP/(TP+FN)|⭐⭐⭐<br>Tertinggi|False Negative = kegagalan mesin tidak terdeteksi = downtime total + biaya<br>darurat sangat besar|
|**F1-Score**|2×(P×R)/(P+R)|⭐⭐⭐|Keseimbangan mendeteksi kegagalan vs meminimalkan false alarm|
|**ROC-**<br>**AUC**|Area under<br>ROC|⭐⭐|Kemampuan diskriminasi model secara keseluruhan|
|**Precision**|TP/(TP+FP)|⭐⭐|False Positive = false alarm = inspeksi tidak perlu, membuang jam produksi|
|**Accuracy**|(TP+TN)/Total|⭐|Tidak representatif karena imbalanced ekstrem (~96% normal)|



**Mengapa Recall diutamakan?** Dalam konteks manufaktur, melewatkan satu prediksi kegagalan mesin ( _false negative_ ) dapat berarti mesin beroperasi menuju kerusakan total yang membutuhkan penggantian komponen besar dan menghentikan seluruh lini produksi selama berhari-hari. Biaya _false negative_ di industri manufaktur jauh melampaui biaya _false positive_ berupa inspeksi yang ternyata tidak diperlukan.[2] 

32 | P a g e 

## **Tabel 18. Ringkasan Pipeline Eksperimen Lengkap** 

|**Tahap**|**Aktivitas**|**Library/Tools**|**Output**|
|---|---|---|---|
|1. Data Collection|Download AI4I 2020 dari Kaggle|kaggle API,pandas|DataFrame 10.000 × 14|
|2. EDA|Statistik deskriptif, distribusi,<br>heatmap, scatter|pandas,seaborn, matplotlib|5 gambar EDA|
|3. Preprocessing|Hapus kolom, feature engineering,<br>encoding|pandas,numpy|DataFrame 10.000 × 15|
|4. Outlier Treatment|IQR detection + Winsorization|scipy.stats.mstats|DataFrame tanpa outlier<br>ekstrem|
|5. Standardisasi|StandardScaler (untuk LR baseline)|sklearn.preprocessing|X_train_scaled,<br>X_val_scaled, X_test_scaled|
|6. Imbalanced<br>Handling|SMOTE + class_weight +<br>scale_pos_weight|imblearn.over_sampling|X_res (7.000→8.791), y_res|
|7. Data Splitting|Stratified 70/10/20|sklearn.model_selection|Train/Val/Test sets|
|8. Modeling (Asgmt II)|XGBoost, Random Forest, LR<br>Baseline|xgboost, sklearn|Trained models|
|9. Evaluasi (Asgmt II)|Recall, F1, ROC-AUC, CM|sklearn.metrics, shap|Laporan perbandingan model|



33 | P a g e 

## **BAB 3** 

## **3.1 Hasil Hyperparameter Tuning** 

Proses tuning dilakukan menggunakan **GridSearchCV dengan 5-Fold Stratified CrossValidation** , menguji 54 kombinasi hyperparameter untuk XGBoost dan Random Forest (270 fits masing-masing), serta 8 kombinasi untuk Logistic Regression, dengan metrik scoring F1-Score. 

## **Rencana Tuning per Model** 

**Tabel 3.1. Rencana Hyperparameter Tuning** 

|**Model**|**Hyperparameter**|**Rentang Nilai yang Diuji**|**Metode**|
|---|---|---|---|
|**XGBoost**|n_estimators|100, 200, 300, 500|GridSearchCV|
||learning_rate|0.01, 0.05, 0.1, 0.2|GridSearchCV|
||max_depth|3, 4, 6, 8|GridSearchCV|
||subsample|0.7, 0.8, 1.0|GridSearchCV|
||scale_pos_weight|1, 10, 28.5 (rasio aktual)|GridSearchCV|
|**Random Forest**|n_estimators|100, 200, 300, 500|GridSearchCV|
||max_depth|None, 10, 20, 30|GridSearchCV|
||min_samples_split|2, 5, 10|GridSearchCV|
||class_weight|balanced,<br>balanced_subsample|GridSearchCV|
|**Logistic Regression**<br>**(Baseline)**|C|0.01, 0.1, 1, 10|GridSearchCV|
||penalty|l1, l2|GridSearchCV|
||class_weight|balanced|Fixed|



34 | P a g e 

Fitting 5 folds for each of 54 candidates, totalling 27@ fits Best XGBoost params: {‘learning_ rate’: 0.1, ‘max_depth': 6, ‘n_estimators': 300, ‘subsample’: 0.8} Best CV Fi1-Score: 9.9663747869260876 Fitting 5 folds for each of 54 candidates, totalling 27@ fits Best Random Forest params: {'class_weight': ‘balanced’, ‘max_depth': None, 'min_samples_split': 2, ‘n_estimators': 200} Best CV Fi1-Score: @.9622239612615772 Best LR params: {'C': 1, ‘penalty': '12'} 



<!-- Start of picture text -->
Learning Curve: XGBoost Learning Curve: Random Forest Learning Curve: Logistic Regression<br>1004 © —E ° ° 1.00 4 ——————1—_—_@— 025<br>0.98 4 0.24<br>0.98 PNA »<br>0.96 + — ~ __ an [ / nN ~ 4y, ~o<br>g 0.96 Pp = ~ ¥ 0.944 pail g é / \ 7<br>Fea& 3a© o924 §a* 0.22 oY\ \ ef/J e a °<br>0.94 \/<br>021 "§<br>0.904 °<br>0.92 « 0.88 4 0.20<br>—@ Training F1 —® Training F1 —® Training F1<br>—® ValidationF1 0.86 4 —®- ValidationFl 0.19 —®- ValidationF1<br>5600 5800 6000 6200 6400 6600 6800 7000 5600 5800 6000 6200 6400 6600 6800 7000 1000 2000 3000 4000 5000<br>jumlah Data Training Jumlah Data Training Jumiah Data Training<br>XGBoost — Train Fl: @.9998 | Val F1: @.7229<br>Random Forest — Train F1: 1.0000 | Val F1: @.8955<br>Logistic Regression — Train F1: @.2356 | Val F1: @.2333<br><!-- End of picture text -->

Tabel 3.2. Perbandingan F1-Score: Training vs Validation 

|**Model**|**Train F1**|**Validation F1**|**Gap**|**Diagnosis**|
|---|---|---|---|---|
|**XGBoost**|0.9998|0.7229|**0.2769 (sangat**<br>**besar)**|**Overfitting parah**|
|**Random Forest**|1.0000|0.8955|**0.1045 (besar)**|**Overfitting sedang-**<br>**berat**|
|**Logistic**<br>**Regression**|0.2356|0.2333|0.0023 (kecil)|**Underfitting**|



Grafik learning curve pada Gambar di atas mengkonfirmasi tiga pola yang sangat berbeda pada ketiga model: 

**XGBoost** menunjukkan pola overfitting klasik  kurva Training F1 (biru) menempel datar di angka mendekati 1.0 sejak awal, sementara kurva Validation F1 (merah) berada jauh di bawah pada kisaran 0.92–0.96 dan baru mulai naik seiring bertambahnya data. Gap sebesar 0.28 antara Train F1 (0.9998) dan Val F1 (0.7229) pada evaluasi langsung menegaskan bahwa model terlalu hafal pola spesifik pada data training hasil SMOTE, termasuk kemungkinan menghafal pola sintetis yang dibuat oleh SMOTE itu sendiri — fenomena yang dikenal sebagai _SMOTE overfitting_ . 

**Random Forest** memperlihatkan pola serupa namun lebih ringan  Training F1 juga mencapai 1.0000 (wajar karena karakteristik pohon keputusan yang dapat tumbuh hingga node murni), namun Validation F1 (0.8955) jauh lebih baik dibanding XGBoost pada evaluasi yang sama. Ini menunjukkan Random Forest sedikit lebih robust terhadap overfitting berkat mekanisme _bagging_ dan _feature randomness_ yang built-in. 

**Logistic Regression** justru menunjukkan pola sebaliknya **underfitting** . Baik Training F1 (0.2356) maupun Validation F1 (0.2333) sama-sama sangat rendah dan saling berdekatan, dengan kurva pada grafik ketiga yang berfluktuasi liar di kisaran 0.19–0.24 tanpa tren peningkatan yang jelas. Ini mengindikasikan model linear sederhana ini **gagal total** menangkap kompleksitas hubungan nonlinear antar fitur sensor (misalnya interaksi Torque-RPM yang berkorelasi -0.88, atau ambang batas fisik Power dan Strain yang bersifat non-linear). 

36 | P a g e 

**Upaya Mitigasi yang Direkomendasikan** 

**Tabel 3.3. Rekomendasi Perbaikan Berdasarkan Diagnosis Aktual** 

|**Model**|**Masalah Terdeteksi**|**Rekomendasi Perbaikan**|
|---|---|---|
|**XGBoost**|Overfitting<br>parah<br>(gap 0.28)|Turunkan max_depth ke 3-4, tambahkan<br>reg_alpha/reg_lambda, terapkan early_stopping_rounds,<br>kurangi rasio SMOTE dari 0.3|
|**Random**|Overfitting<br>sedang|Batasi max_depth (jangan None), naikkan|
|**Forest**|(gap 0.10)|min_samples_leaf menjadi 5-10, kurangi n_estimators|
|**Logistic**|Underfitting parah|Tambahkan fitur polynomial/interaksi, gunakan kernel non-|
|**Regression**||linear (ganti ke SVM-RBF), atau terima sebagai baseline<br>pembanding saja|



## **3.3 Hasil Evaluasi Model pada Test Set (Hold-out)** 

Evaluasi akhir menggunakan test set 2.000 baris yang **tidak pernah disentuh** selama proses training maupun tuning. 

**Tabel 3.4. Hasil Evaluasi Model pada Test Set** 

|**Model**|**Accuracy**|**Precision**|**Recall**|**F1-Score**|**ROC-AUC**|
|---|---|---|---|---|---|
|**XGBoost**|0.976|0.604|**0.853**|0.707|0.982|
|**Random Forest**|**0.988**|**0.844**|0.794|**0.818**|**0.985**|
|**Logistic Regression**|0.817|0.137|0.824|0.234|0.906|



37 | P a g e 



<!-- Start of picture text -->
Confusion Matrix: XGBoost Confusion Matrix: Random Forest Confusion Matrix: Logistic Regression<br>1750 1750 1400<br>Normal 1894 1500 Normal 1922 1500 Normal 1578 p00<br>1250 1250 1000<br>3 1000 3 1000 * 800<br>" ° .<br>750 750 600<br>Failure — Failure soo Failure 400<br>250 250 200<br>Normal Failure Normal Failure Normal Failure<br>Predicted label Predicted label Predicted label<br>Model Accuracy Precision Recall F1-Score ROC-AUC<br>) XGBoost @.976 @.604167 @.852941 ©.707317 @.982364<br>1 Random Forest 0.988 @.84375@ @.794118 ©@.818182 6.984746<br>2 Logistic Regression @.817 0.136585 ©.823529 ©.23431@ @.9@5896<br><!-- End of picture text -->

Model CV F1 (meantstd) CV Recall (meantstd) CV ROC-AUC (mean+std) | 0) XGBoost 0.964 + 0.005 0.981 + 0.007 0.999 + 0.000 1 Random Forest 0.963 + 0.005 0.950 + 0.012 0.998 + 0.001 2 Logistic Regression 0.233 + 0.013 0.818 + 0.050 0.887 + 0.020 



<!-- Start of picture text -->
Perbandingan Performa Model (F1-Score, Recall, Precision)<br>1.0 mmm F1-Score<br>> © Mm Recall<br>i t 3 S lm Precision<br>x 8 a 3 3 3<br>Soo 2 s<br>g 5 & 8<br>oe S 3 3<br>0.6 cs g<br>2 8 a 5. Fy<br>&5 es = a=5 a = 4S 23<br>0.4 Fa3a5]<br>~4<br>3<br>0.2<br>0.0<br>S© Ss s Se KoS RZoo KoS A Ss<br>RS SsSs se xS ¥s &e .&<br>& cog s<br>Model<br><!-- End of picture text -->

|**7**|CatBoost|0.478|0.868|0.330|Boosting|
|---|---|---|---|---|---|
|**8**|SVM|0.451|0.882|0.303|Kernel-based|
|**9**|KNN|0.374|0.250|0.739|Instance-based|



Temuan paling menarik dari eksperimen lanjutan ini adalah **Gradient Boosting (implementasi sklearn) justru mengungguli seluruh model lain** , termasuk XGBoost dan Random Forest yang sudah melalui hyperparameter tuning intensif — meskipun Gradient Boosting di sini masih menggunakan parameter default tanpa tuning sama sekali. Hal ini mengindikasikan bahwa parameter default sklearn untuk Gradient Boosting kebetulan sudah cukup mendekati konfigurasi optimal untuk karakteristik dataset AI4I 2020, atau bahwa XGBoost dan Random Forest versi tuned mengalami overfitting terhadap data SMOTE sehingga performanya justru menurun saat diuji pada test set dengan distribusi asli. 

Pola yang sangat konsisten muncul dari LightGBM, CatBoost, dan SVM: ketiganya mencatat **Recall tinggi (0.87–0.88) namun Precision sangat rendah (0.30–0.55)** . Ini menunjukkan ketiga algoritma tersebut, tanpa tuning tambahan, cenderung terlalu agresif memprediksi kelas Failure  menghasilkan banyak false alarm. Sebaliknya, **KNN menunjukkan pola berlawanan** dengan Recall sangat rendah (0.250) model ini gagal mendeteksi sebagian besar kasus Failure yang sesungguhnya, kemungkinan besar karena _curse of dimensionality_ pada data dengan banyak fitur turunan hasil feature engineering. 

## **Analisis Trade-off untuk Konteks Manufaktur** 

Dalam konteks predictive maintenance, **Recall lebih diprioritaskan** dibanding Precision karena biaya _false negative_ (kegagalan mesin tidak terdeteksi) jauh lebih besar daripada biaya _false positive_ (inspeksi yang ternyata tidak diperlukan). Berdasarkan kriteria ini, urutan prioritas model berubah signifikan: 

**Tabel 3.7. Re-ranking Model Berdasarkan Prioritas Recall (Konteks Manufaktur)** 

|**Peringkat (by**<br>**Recall)**|**Model**|**Recall**|**Precision**||**Catatan Trade-off**|
|---|---|---|---|---|---|
|**1**|SVM|0.882|0.303|Recall<br>terendah|tertinggi,<br>tapi<br>Precision<br>kedua|



40 | P a g e 

|**2**|CatBoost|0.868|0.330|Recall sangat tinggi, Precision sangat<br>rendah|
|---|---|---|---|---|
|**2**|LightGBM|0.868|0.551|Recall tinggi, Precision sedang|
|**4**|XGBoost (tuned)|0.853|0.604|**Keseimbangan lebih baik**|
|**5**|Decision Tree|0.838|0.553|Cepat tapi Precision rendah|
|**6**|Gradient Boosting|0.824|0.812|**Trade-off paling seimbang secara**<br>**keseluruhan**|
|**7**|Logistic<br>Regression|0.824|0.137|Recall tinggi tapi Precision sangat<br>buruk (underfitting)|
|**8**|AdaBoost|0.735|0.602|Sedang di semua metrik|
|**9**|Random<br>Forest<br>(tuned)|0.794|0.844|Precision terbaik, tapi Recall bukan<br>prioritas|



Tabel di atas menunjukkan bahwa memilih model "terbaik" untuk deployment tidak bisa hanya bergantung pada satu metrik. Jika prioritas mutlak adalah meminimalkan kegagalan yang terlewat tanpa mempedulikan jumlah false alarm, SVM atau CatBoost menjadi kandidat terbaik meski akan membebani tim maintenance dengan banyak inspeksi tidak perlu. Namun jika perusahaan menginginkan keseimbangan operasional yang realistis antara mendeteksi kegagalan dan menjaga efisiensi sumber daya inspeksi, **Gradient Boosting (default) dan XGBoost (tuned)** menjadi pilihan paling rasional karena keduanya mencatat kombinasi Recall tinggi dan Precision yang masih dapat diterima. 

41 | P a g e 

## **3.5 Kesimpulan Bab 3** 

Tiga temuan utama dapat disimpulkan dari keseluruhan eksperimen tuning, diagnosis overfitting/underfitting, dan evaluasi sembilan algoritma pada studi kasus predictive maintenance AI4I 2020: 

**Pertama** , proses hyperparameter tuning berhasil menemukan konfigurasi optimal secara matematis pada training set (CV F1-Score XGBoost 0.966, Random Forest 0.962), namun skor tinggi ini **tidak serta-merta mencerminkan performa nyata di lapangan** terbukti dari penurunan tajam F1-Score saat diuji pada test set dengan distribusi kelas asli (XGBoost turun ke 0.707, meski Random Forest relatif lebih stabil di 0.818). Temuan ini menegaskan pentingnya evaluasi hold-out test set yang independen dari proses SMOTE dan tuning, bukan hanya mengandalkan skor cross-validation. 

**Kedua** , dari sisi generalisasi model, **Random Forest terbukti paling robust** di antara tiga model utama, dengan gap Train-Validation F1 paling kecil (0.10) dibanding XGBoost (0.28), serta mencatat kombinasi Accuracy, Precision, dan ROC-AUC tertinggi pada test set. Sebaliknya, **Logistic Regression terbukti tidak layak** digunakan sebagai model produksi untuk kasus ini karena underfitting parah  model linear sederhana ini gagal menangkap kompleksitas hubungan non-linear antar fitur sensor mesin. 

**Ketiga** , eksplorasi sembilan algoritma tambahan mengungkap temuan tak terduga bahwa **Gradient Boosting versi default (tanpa tuning)** justru mencatat F1-Score tertinggi (0.818) dan trade-off Recall-Precision paling seimbang di antara seluruh model yang diuji, mengungguli XGBoost dan Random Forest yang sudah melalui tuning intensif. Hal ini menjadi pelajaran penting bahwa hyperparameter tuning yang terlalu agresif pada data hasil SMOTE berisiko menyebabkan overfitting terhadap pola sintetis, sehingga pemilihan model akhir sebaiknya selalu divalidasi ulang pada test set dengan distribusi data asli, bukan hanya berdasarkan skor cross-validation semata. 

42 | P a g e 

**3.6 Kelemahan dan Keterbatasan Penelitian** 

## **Keterbatasan Metodologis:** 

- **Overfitting belum sepenuhnya diatasi** : Penelitian ini baru sampai pada tahap _observasi_ dan _identifikasi_ overfitting pada XGBoost dan Random Forest, namun belum melakukan iterasi ulang tuning dengan parameter regularisasi yang lebih ketat sebagai tindak lanjut konkret. Rekomendasi mitigasi pada Tabel 3.3 masih bersifat rencana, belum diuji ulang hasilnya. 

- **SMOTE hanya diterapkan pada satu rasio (0.3)** : Tidak dilakukan eksperimen sensitivitas terhadap rasio SMOTE lain (misalnya 0.5, 0.7, atau 1.0) yang berpotensi mengurangi tingkat overfitting yang teramati, khususnya pada XGBoost. 

- **Model tambahan (LightGBM, CatBoost, SVM, dst.) tidak di-tuning** : Sembilan algoritma pada eksplorasi tambahan seluruhnya menggunakan parameter default, sehingga perbandingan dengan XGBoost dan Random Forest (yang sudah di-tuning) menjadi tidak sepenuhnya adil ( _apple-to-apple_ ). Ada kemungkinan performa LightGBM atau CatBoost dapat meningkat signifikan jika diberi perlakuan tuning yang setara. 

## **Keterbatasan Data:** 

- **Dataset bersifat sintetis** : AI4I 2020 adalah data simulasi, bukan data sensor riil dari pabrik. Meski dirancang menyerupai kondisi nyata, pola statistiknya mungkin tidak sepenuhnya menangkap kompleksitas dan noise yang ada pada mesin industri sesungguhnya. 

- **Jumlah kasus Failure sangat terbatas (339 dari 10.000)** : Bahkan setelah SMOTE, keterbatasan data asli pada kelas minoritas membuat model rentan mempelajari pola dari sampel sintetis yang mungkin tidak sepenuhnya representatif terhadap variasi kegagalan mesin di dunia nyata. 

- **Test set kecil untuk kelas Failure (~68 kasus)** : Dengan hanya 68 kasus Failure pada test set, setiap kesalahan klasifikasi tunggal memiliki dampak signifikan terhadap metrik Recall dan Precision, membuat estimasi performa lebih rentan terhadap varians statistik dibanding jika jumlah kasus lebih besar. 

## **Keterbatasan Perbandingan Antar Studi:** 

- Perbandingan dengan penelitian literatur (Al Mamlook et al., Sakmar et al., Cioch et al.) perlu dilakukan dengan hati-hati karena masing-masing menggunakan **dataset, jumlah fitur, dan strategi resampling yang berbeda** , sehingga perbedaan angka performa tidak selalu 

43 | P a g e 

murni mencerminkan keunggulan algoritma, melainkan juga karakteristik data yang digunakan. 

## **3.7 Tabel Referensi Algoritma dengan Konteks Penelitian Lengkap** 

## **Tabel 3.8. Algoritma Tambahan  & Konteks Dataset dan Studi Rujukan** 

|**Algoritma**|**Kategori**|**Potensi**|**Metrik Kunci**|**Sumber**|**Dataset**|
|---|---|---|---|---|---|
|**LightGBM**|<sup>Gradient</sup><br>Boosting|Sangat<br>Baik|Acc 0.980,<br>Recall 0.730,<br>AUC 0.968|Al Mamlook<br>et al.,<br>INTCEC<br>2024|10.000 entri, 7 fitur<br>sensor, SMOTE<br>(339→9.661)|
|**CatBoost**|Gradient<br>Boosting|Sangat<br>Baik|Recall 0.795<br>(tertinggi), AUC<br>0.971, Precision<br>0.593|Al Mamlook<br>et al.,<br>INTCEC<br>2024|10.000 entri, 7 fitur<br>sensor, SMOTE<br>(339→9.661)|
|**CatBoost**<br>**(validasi)**|Gradient<br>Boosting|Baik<br>(Recall<br>0.79–<br>0.99)|Konfirmasi<br>efektivitas<br>SMOTE;<br>XGBoost paling<br>optimal trade-off|Sakmar et<br>al., Jurnal<br>SINTA 2025|AI4I 2020 asli (UCI),<br>10.000 baris, tanpa<br>modifikasi|
|**SVM**|Kernel-based|Baik,<br>lambat di<br>data<br>besar|Acc 97.6–98.2%,<br>AUC >0.95,<br>speed 10.818<br>obs/detik|Cioch et al.,<br>ASTRJ 2025|100.000 baris, 3 fitur<br>sensor, imbalanced<br>80.3:19.7|
|**Decision**<br>**Tree**|Tree<br>sederhana|Cukup<br>Baik,<br>tercepat|Acc 98.24%,<br>speed >421.000<br>obs/detik, size<br>4.7KB|Cioch et al.,<br>ASTRJ 2025|100.000 baris, 3 fitur<br>sensor, imbalanced<br>80.3:19.7|



44 | P a g e 

|**KNN**|Instance-<br>based|Kurang<br>Optimal|Acc 97.67%, 233<br>error (177 FN +<br>56 FP)|Cioch et al.,<br>ASTRJ 2025|100.000 baris, 3 fitur<br>sensor, imbalanced<br>80.3:19.7|
|---|---|---|---|---|---|
|**Naive**<br>**Bayes**|Probabilistic|Kurang<br>Optimal|Acc 96.34%<br>(terendah kedua),<br>366 FN|Cioch et al.,<br>ASTRJ 2025|100.000 baris, 3 fitur<br>sensor, imbalanced<br>80.3:19.7|
|**AdaBoost**|Boosting<br>klasik|Sedang|AUC 0.940<br>(terendah dari 8<br>model), Recall<br>0.425|Al Mamlook<br>et al.,<br>INTCEC<br>2024|10.000 entri, 7 fitur<br>sensor, SMOTE<br>(339→9.661)|
|**ANN**<br>**(MLP)**|Deep<br>Learning|Baik|Precision 0.803,<br>Acc 0.980,<br>Recall sedang<br>0.558|Al Mamlook<br>et al.,<br>INTCEC<br>2024|10.000 entri, 7 fitur<br>sensor, SMOTE<br>(339→9.661)|
|**Gradient**<br>**Boosting**|Boosting|Sangat<br>Baik<br>(Terbaik)|Acc 0.982 dan<br>Precision 0.828<br>tertinggi dari 8<br>model|Al Mamlook<br>et al.,<br>INTCEC<br>2024|10.000 entri, 7 fitur<br>sensor, SMOTE<br>(339→9.661)|



45 | P a g e 

### **Future Works.** 

### **1. Penyempurnaan Mitigasi Overfitting** 

Penelitian saat ini baru sampai pada tahap _diagnosis_ overfitting pada XGBoost (gap 0.28) dan Random Forest (gap 0.10), namun rekomendasi mitigasi pada Tabel 3.3 belum diuji ulang. Pengembangan lanjutan perlu mengimplementasikan dan memvalidasi konfigurasi regularisasi baru (max_depth diturunkan, reg_alpha/reg_lambda ditambahkan, early_stopping_rounds diterapkan) lalu mengukur ulang gap TrainValidation F1 hingga mencapai target di bawah 0.05. 

### **2. Eksperimen Sensitivitas Rasio SMOTE** 

Penelitian ini hanya menguji satu rasio SMOTE (0.3). Pekerjaan lanjutan perlu melakukan grid search terhadap rasio 0.2, 0.5, 0.7, dan 1.0, serta membandingkan dengan teknik resampling alternatif seperti SMOTETomek atau ADASYN, untuk menentukan konfigurasi yang paling meminimalkan _SMOTE overfitting_ sekaligus mempertahankan Recall tinggi. 

### **3. Tuning Setara untuk Seluruh Algoritma Kandidat** 

Sembilan algoritma pada eksplorasi lanjutan (LightGBM, CatBoost, SVM, Decision Tree, KNN, Naive Bayes, AdaBoost, ANN, Gradient Boosting) seluruhnya masih menggunakan parameter default, sementara XGBoost dan Random Forest sudah di-tuning — perbandingan ini tidak _apple-to-apple_ . Penelitian lanjutan wajib menerapkan hyperparameter tuning setara pada semua kandidat, khususnya Gradient Boosting yang justru menjadi model terbaik meski masih default, untuk memastikan superioritasnya bukan kebetulan. 

### **4. Validasi Statistik Signifikansi Antar Model** 

Perbedaan F1-Score antar sembilan model belum diuji signifikansinya secara statistik. Penelitian lanjutan perlu menerapkan McNemar's test atau paired t-test pada hasil k-fold untuk memastikan superioritas Gradient Boosting atas Random Forest dan XGBoost benar-benar signifikan secara statistik, bukan variasi acak. 

### **5. Optimasi Threshold Keputusan dan Kalibrasi Probabilitas** 

Seluruh evaluasi saat ini menggunakan threshold default 0.5. Mengingat konteks manufaktur memprioritaskan Recall, penelitian lanjutan perlu menggunakan Precision-Recall curve untuk mencari threshold optimal per model, serta menerapkan CalibratedClassifierCV khususnya pada SVM dan Logistic Regression yang menunjukkan Precision sangat rendah. 

### **6. Ekspansi ke Multi-Class Failure Mode Classification** 

Ruang lingkup penelitian sudah mencantumkan target sekunder opsional berupa klasifikasi lima failure modes (TWF, HDF, PWF, OSF, RNF), namun belum diimplementasikan. Tahap lanjutan penting untuk mengembangkan model multi-class guna mengidentifikasi _jenis_ kegagalan spesifik, bukan hanya biner gagal/tidak — ini jauh lebih actionable bagi tim maintenance dalam menentukan tindakan perbaikan yang tepat. 

### **7. Perbandingan Head-to-Head dengan Studi Rujukan** 

Untuk memperkuat validitas eksternal, penelitian lanjutan perlu mereplikasi skema eksperimen studi rujukan (Al Mamlook et al. 2024, Sakmar et al. 2025) — menggunakan rasio SMOTE dan split data yang 

46 | P a g e 

identik — agar hasil dapat dibandingkan secara head-to-head, bukan hanya dibandingkan secara kualitatif seperti pada Tabel 3.8 saat ini. 

### **8. Pengembangan Sistem Deployment End-to-End** 

Sebagai kelanjutan menuju Final Project (AOL), penelitian perlu diarahkan pada pengembangan sistem _end-to-end_ — mulai dari API inferensi real-time, integrasi dengan dashboard monitoring sensor, hingga mekanisme _alerting_ otomatis bagi tim maintenance sesuai fokus penilaian AOL yang menekankan pengembangan sistem machine learning end-to-end beserta saran pengembangan ke depan. 

47 | P a g e 

### **Referensi:** 

[1] S.Nangia, S. Makkar, and R.Hassan, "IoT based predictive maintenance in manufacturing sector," SSRN Electronic Journal, 2020. [Online]. Available: 

https://papers.ssrn.com/sol3/Delivery.cfm/SSRN_ID3563559_code3635775.pdf?abstractid=3563559&mi rid=1 

[2] H.Rafi, "Predictive maintenance berbasis machine learning dalam sektor manufaktur," JUTECH: Jurnal Teknologi dan Komputer, vol. 1, no. 1, 2024. [Online]. Available: https://ojs.itbad.ac.id/index.php/JUTECH/article/view/3333 

[3] Label Your Data, "How to work with predictive maintenance data and why?," LabelYourData.com, 2023. [Online]. Available: https://labelyourdata.com/articles/predictive-maintenance-datasets 

[4] S. Matzka, "AI4I 2020 predictive maintenance dataset," UCI Machine Learning Repository, 2020. [Online]. Available: http://archive.ics.uci.edu/ml/datasets/AI4I+2020+Predictive+Maintenance+Dataset 

[5] S. Matzka, "Predictive maintenance dataset," Mendeley Data, vol. 1, 2020. doi: 10.17632/5ww3zv87y7.1. [Online]. Available: https://data.mendeley.com/datasets/5ww3zv87y7 

[6] S. Matzka, "Machine predictive maintenance classification," Kaggle, 2021. [Online]. Available: https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification 

[7] R.Dogan and M.Basunaid, "Machine failure prediction and interpretation for operator decision support," B.S. thesis, School of Informatics, University of Skövde, Skövde, Sweden, 2025. [Online]. Available: https://his.diva-portal.org/smash/get/diva2:2083757/FULLTEXT01.pdf 

[8] E. Sestri1, A.Satyo B.Karno, W.Hastomo, "Benchmarking five machine learning models for accurate defect detection in steel plates," Cogito Smart Journal, vol. 10, no. 2, 2024. [Online]. Available: https://cogito.unklab.ac.id/index.php/cogito/article/view/753 

[9] Arkondata, "Data preprocessing in machine learning: Steps, techniques, and importance in AI and ML," Arkondata Blog, 2023. [Online]. Available: https://www.arkondata.com/en/post/data-preprocessingin-machine-learning 

[10] Couchbase, "The importance of data preprocessing in machine learning," Couchbase Blog, 2023. [Online]. Available: https://www.couchbase.com/blog/data-preprocessing-in-machine-learning/ 

[11] A.Muhidin, M.Danny, & N.Surojudin, "Prediksi kegagalan perangkat industri menggunakan machine learning pada dataset AI4I 2020," Bulletin of Computer Science Research, vol. 4, no. 2, 2024. [Online]. Available: https://hostjournals.com/bulletincsr/article/view/745 

[12] A.Muhidin, M.Danny, & N.Surojudin, "Prediksi kegagalan perangkat industri menggunakan machine learning pada dataset AI4I 2020," Bulletin of Computer Science Research, vol. 4, no. 2, 2024. [Online]. Available: http://www.hostjournals.com/bulletincsr/article/view/745 

[13] M.Sakmar, N.Kadir, P.Shofo, A.Darmawan, "Efektivitas XGBoost, LightGBM, dan CatBoost pada dataset tidak seimbang dengan teknik SMOTE," Jurnal SINTA, vol. 2, no. 1, 2024. [Online]. Available: 

48 | P a g e 

https://jurnalsinta.id/index.php/sinta/article/view/145 

[14] W.Rahayu1, D.Jollyta2, A. Hajjah, Johan, Gusrianty, Gustientiedina, Y.Marlim, Y.Desnelita, "Synthetic minority oversampling technique (SMOTE) for imbalanced classification," Journal of Artificial Intelligence and Engineering Applications (JAIEA), vol. 3, no. 1, 2023. [Online]. Available: https://ioinformatic.org/index.php/JAIEA/article/view/469 

[15] S. S. Kale, "Predictive maintenance of equipment using machine learning," M.S. thesis, National College of Ireland, Dublin, Ireland, 2024. [Online]. Available: https://norma.ncirl.ie/8576/1/sakshisanjaykale.pdf 

[16] M.Alnahhal  ,MosabI.Tabash, Samir K. Safi ,and Z.Mamadiyarov, Mujeeb S.M. Absy, "A comparative study of imbalance-handling methods in predictive maintenance using the AI4I 2020 dataset," MDPI Computation, vol. 14, no. 4, p. 88, 2026. doi: 10.3390/computation14040088. [Online]. Available: https://www.mdpi.com/2079-3197/14/4/88 

[17] A.Kareem, "Comparative analysis of XGBoost and random forest for predictive maintenance," Annals of the Faculty of Engineering Hunedoara, vol. 22, no. 4, pp. 113–120, 2024. [Online]. Available: https://annals.fih.upt.ro/pdf-full/2024/ANNALS-2024-4-18.pdf 

[18] Scribd / Anonymous, "Anomaly detection in predictive maintenance," Scribd Document, 2024. [Online]. Available: https://www.scribd.com/document/869753188/Anomaly-Detection-and-PredictiveMaintenance 

49 | P a g e 

