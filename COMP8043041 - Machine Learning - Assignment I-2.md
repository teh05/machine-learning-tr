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
|Gambar 10|Pipeline Anti-Overfit (SMOTE 0.2, val-asli scoring)|Bab 3.0–3.1|
|Gambar 11|Learning Curves setelah Regularisasi|Bab 3.2|
|Gambar 12|Confusion Matrices Model Utama vs GB|Bab 3.3|
|Gambar 16|Perbandingan Multi-Model (Main / Extended / All)|Bab 3.5|
|Gambar 22|SHAP Summary & Bar — Random Forest|Bab 3.7|



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

Strategi final (setelah mitigasi overfitting): **SMOTE hanya pada training** dengan `sampling_strategy=0.2` (bukan 0.3). Untuk model tree (RF/XGB/GB) **tidak** digabung dengan `class_weight`/`scale_pos_weight` agresif agar menghindari _double-balancing_ yang menurunkan Precision. Logistic Regression tetap memakai `class_weight='balanced'` (+ polynomial features) karena dilatih pada data asli tanpa SMOTE.[13] 

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

smote = SMOTE(random_state=42, k_neighbors=5, sampling_strategy=0.2) X_res, y_res = smote.fit_resample(X_train, y_train) 

print(f"Distribusi kelas Train sesudah SMOTE:\n{pd.Series(y_res).value_counts()}") # Output: 0: 6763, 1: 1352
# Alasan 0.2 (bukan 0.3/1.0): rasio lebih tinggi menambah sampel sintetis → Precision turun (false alarm naik). Sensitivitas RF membuktikan F1 terbaik di 0.2. 

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
1. Data Collection<br>AI4I 2020 - 10.000 x 14- CC<br>BY 4.0<br>2. EDA<br>Deskriptif + Distribusi<br>failure - Histogram/KDE<br>Boxplot - Korelasi - Scatter<br>zona gagal<br>3. Pra-Pemrosesan<br>Drop UID & Product ID -<br>Power, Strain, Temp_diff<br>IQR + Winsorization - Type:<br>L/M/H > 0/1/2<br>4, Standardisasi<br>StandardScaler (Z-score)<br>Hanya untuk LR - Tree<br>models tanpa scaling<br>5. Imbalanced Data<br>96.6% Normal - 3.4% Failure<br>SMOTE 0.2 (no double-balance); LR class_weight='balanced'<br>strategy=0.2 - k=5 XGBoost RF &LR<br>6. Split Stratified<br>Train 70% - Val 10% - Test<br>20%<br>SMOTE hanya di Training<br>7. Modeling<br>XGBoost - Random Forest -<br>LR Baseline<br>GridSearchCV 5-Fold<br>Stratified<br>8. Evaluasi<br>Recall - F1 - ROC-AUC<br>Precision - Accuracy - CM -<br>SHAP<br>9. Kesimpulan<br>Model terbaik untuk Early<br>Warning<br>Feature importance —<br>Maintenance Policy<br><!-- End of picture text -->

## **Model 1: XGBoost Classifier (Extreme Gradient Boosting)** 

XGBoost merupakan pilihan terdepan untuk Predictive Maintenance berbasis data tabular sensor, didukung bukti performa paling komprehensif dalam berbagai studi. Pada AI4I 2020 dataset, XGBoost + SMOTE berhasil menjadi model paling optimal dalam menyeimbangkan Recall tinggi dengan Precision yang wajar, serta konsisten mengungguli model lain untuk kelas minoritas.[15][13] 

## **Justifikasi pemilihan XGBoost:** 

- **<mark>scale_pos_weight</mark>** <mark>:</mark> tersedia untuk imbalance, namun pada pipeline final **diset 1.0** saat data sudah di-SMOTE agar menghindari double-balancing (penyebab Precision anjlok di eksperimen awal) 

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
|6. Imbalanced<br>Handling|SMOTE 0.2 (tree tanpa double-balance); LR class_weight|imblearn.over_sampling|X_res (~8115 baris), y_res|
|7. Data Splitting|Stratified 70/10/20|sklearn.model_selection|Train/Val/Test sets|
|8. Modeling (Asgmt II)|XGBoost, Random Forest, LR<br>Baseline|xgboost, sklearn|Trained models|
|9. Evaluasi (Asgmt II)|Recall, F1, ROC-AUC, CM|sklearn.metrics, shap|Laporan perbandingan model|



33 | P a g e 

## **BAB 3 — Hasil Eksperimen, Analisis Alasan Metrik, dan Pembahasan**

Bab ini menyajikan hasil Assignment II setelah mitigasi overfitting/underfitting. Evaluasi dipisah menjadi **(A) Model Utama** sesuai ruang lingkup penelitian (XGBoost, Random Forest, Logistic Regression + Gradient Boosting sebagai pembanding) dan **(B) Extended Models** sebagai penguat eksperimen. Setiap angka dilengkapi **alasan metodologis** mengapa nilai terbentuk demikian.

### **3.0 Ringkasan Perubahan Metodologi (sebelum → sesudah mitigasi)**

| Aspek | Sebelum (diagnosis awal) | Sesudah (pipeline final) | Alasan diubah |
|-------|--------------------------|---------------------------|---------------|
| SMOTE | `strategy=0.3` (failure train 237→2028) | **`strategy=0.2`** (237→1352) | Rasio tinggi menambah noise sintetis → Precision turun |
| Balancing tree | SMOTE + `scale_pos_weight≈28` / `class_weight=balanced` | **SMOTE saja** (`scale_pos_weight=1`, RF tanpa class_weight) | Double-balancing membuat model terlalu agresif ke Failure (P turun, F1 jelek) |
| Scoring tuning | CV di data SMOTE | **`PredefinedSplit` skor di validation asli** | Mencegah memilih model yang hanya hafal sampel SMOTE |
| XGBoost | depth tinggi, tanpa early stopping | depth 3–4, early stopping, regularisasi | Menurunkan gap Train–Val |
| LR | linear murni | **Polynomial degree=2 + StandardScaler** | Menambah kapasitas non-linear (tetap underfit relatif tree) |

---

## **3.1 Hasil Hyperparameter Tuning (Model Utama)**

Tuning dilakukan dengan **GridSearchCV + PredefinedSplit**: train = data SMOTE, skor F1 diukur pada **validation set berdistribusi asli**. Ini berbeda dari CV murni di SMOTE yang sebelumnya menghasilkan F1 CV sangat tinggi (~0.96) tetapi drop tajam di test.

**Mengapa skor val-asli lebih rendah dari CV-SMOTE lama?**  
Validation asli hanya ~3.4% failure (~34 kasus). Model yang “terlalu cocok” ke SMOTE akan dihukum di val asli → grid search memilih konfigurasi yang lebih generalizable ke distribusi lapangan.

**Tabel 3.1. Arah Hyperparameter Final (inti)**

| Model | Fokus parameter | Alasan |
|-------|-----------------|--------|
| XGBoost | `max_depth` 3–4, `learning_rate` 0.05–0.1, `scale_pos_weight=1`, early stopping | Meniru perilaku sklearn GB yang stabil; hindari overfit SMOTE |
| Random Forest | tanpa `class_weight`, `min_samples_leaf/split` terkontrol | Bagging + SMOTE 0.2 cukup; class_weight menambah bias Failure |
| LR-Poly | Pipeline Poly(2) + `C`, `penalty` l1/l2, `class_weight=balanced` | Linear murni underfit; poly menambah interaksi Torque–RPM, dll. |

Gambar terkait: `fig10_pipeline_flowchart.png` (pipeline anti-overfit).

---

## **3.2 Diagnosa Overfitting / Underfitting (setelah mitigasi)**

**Tabel 3.2. Gap Train vs Validation F1 (Block 12)**

| Model | Train F1 | Val F1 | Gap | Diagnosis | Alasan nilai seperti itu |
|-------|----------|--------|-----|-----------|---------------------------|
| **XGBoost (reg)** | 0.9244 | 0.9062 | **0.0182** | Sehat | Depth rendah + early stopping + tanpa double-balance → kurva train/val saling dekat (dulu gap 0.28) |
| **Random Forest (reg)** | 1.0000 | 1.0000* | 0.0000 | Dicek lewat **test** | RF mudah mencapai Train F1=1 pada SMOTE (pohon bisa murni). Val F1=1.0 pada ~34 failure **terlalu sempurna** → kemungkinan varians val kecil, **bukan** bukti sempurna di lapangan |
| **LR-Poly** | 0.4198 | 0.4314 | −0.0116 | Underfit | Kapasitas tetap terbatas vs interaksi fisik kompleks; poly membantu (naik dari F1~0.23) tetapi Precision tetap rendah |

\*Interpretasi hati-hati: keputusan final selalu dari **test hold-out** (~68 failure), bukan Val F1=1.0.

Gambar: `fig11_learning_curves.png`.

---

## **3.3 Evaluasi Test Set — Model Utama (Hold-out)**

Test set: 2.000 baris, distribusi asli (~68 failure). Metrik utama untuk kesimpulan Assignment: **F1@0.5**, dilengkapi Recall, Precision, ROC-AUC.

**Tabel 3.3. Hasil Test Model Utama (F1@0.5)**

| Rank | Model | Accuracy | Precision | Recall | **F1@0.5** | ROC-AUC |
|------|-------|----------|-----------|--------|------------|---------|
| 1 | **Random Forest (reg)** | 0.991 | **0.903** | **0.824** | **0.862** | **0.988** |
| 2 | Gradient Boosting (default) | 0.991 | 0.889 | 0.824 | 0.855 | 0.985 |
| 3 | XGBoost (reg) | 0.990 | 0.887 | 0.809 | 0.846 | 0.983 |
| 4 | LR-Poly (reg) | 0.910 | 0.260 | 0.897 | 0.403 | 0.968 |

### **Alasan mengapa nilai terbentuk seperti itu**

1. **Mengapa Accuracy semua tree ~0.99?**  
   Kelas Normal mendominasi (~96.6%). Accuracy tinggi **tidak** berarti model bagus untuk PdM; yang relevan adalah deteksi Failure (Recall/Precision/F1).

2. **Mengapa Random Forest F1 & AUC tertinggi di Main?**  
   - Bagging mengurangi varians dibanding boosting yang terlalu agresif pada SMOTE.  
   - Tanpa double-balancing, Precision tetap tinggi (0.903) sambil mempertahankan Recall 0.824.  
   - AUC 0.988 menunjukkan ranking probabilitas Failure paling baik di antara model utama.

3. **Mengapa Recall RF = Recall GB (0.824)?**  
   Keduanya menangkap jumlah Failure yang sama di threshold 0.5 pada test ini. Perbedaan kualitas ada di **Precision/F1/AUC**: RF lebih sedikit false alarm relatif terhadap keseimbangan F1, dan ranking skornya lebih baik (AUC).

4. **Mengapa Gradient Boosting tetap sangat dekat (F1 0.855)?**  
   Default sklearn GB (`depth` rendah, learning rate moderat) secara alami mirip konfigurasi “jinak”. Itu sebabnya di eksperimen awal GB terlihat unggul saat XGB/RF masih overfit SMOTE. Setelah mitigasi, RF menyusul/mengungguli tipis.

5. **Mengapa XGBoost F1 0.846 (bukan 0.707 lagi)?**  
   Mitigasi berhasil: tidak lagi hafal SMOTE. F1 naik dari ~0.71 → ~0.85 karena Precision pulih (dulu ~0.60 akibat terlalu banyak prediksi Failure).

6. **Mengapa LR-Poly Recall tinggi (0.90) tetapi F1 hanya 0.40?**  
   `class_weight=balanced` + batas keputusan linear/poly membuat model sering memprediksi Failure → banyak **false positive** → Precision anjlok (0.26). Cocok sebagai baseline, tidak untuk produksi.

7. **Threshold dari validation (kolom Threshold di eksperimen)**  
   Optimasi threshold di val (~34 failure) tidak stabil; untuk RF, F1@0.5 (0.862) justru sedikit lebih baik dari F1 di thr val 0.575 (0.857). Karena itu kesimpulan produksi memakai **F1@0.5**.

Gambar: `fig12_confusion_matrices.png`, `main_models_vs_gb.csv`.

---

## **3.4 Repeated Stratified K-Fold (Stabilitas)**

**Tabel 3.4. CV (5×3) — mean ± std**

| Model | CV F1 | CV Recall | CV Precision | CV ROC-AUC |
|-------|-------|-----------|--------------|------------|
| Random Forest (reg) | **0.949 ± 0.012** | 0.921 ± 0.021 | 0.978 ± 0.008 | 0.996 ± 0.002 |
| Gradient Boosting | 0.915 ± 0.013 | 0.867 ± 0.019 | 0.969 ± 0.011 | 0.990 ± 0.002 |
| XGBoost (reg) | 0.906 ± 0.011 | 0.847 ± 0.018 | 0.974 ± 0.013 | 0.991 ± 0.002 |
| LR-Poly | 0.402 ± 0.018 | 0.880 ± 0.042 | 0.261 ± 0.015 | 0.959 ± 0.014 |

**Alasan CV F1 tree (~0.90–0.95) lebih tinggi dari test F1 (~0.85):**  
CV untuk tree dijalankan pada **X_res (SMOTE)** sehingga distribusi train/fold lebih “seimbang” daripada test asli. Ini **bukan** kontradiksi; melainkan mengingatkan bahwa skor CV-SMOTE bersifat optimistis. Pola peringkat tetap konsisten: **RF > GB > XGB >> LR**.

---

## **3.5 Eksperimen Extended Models (Penguat) — Ranking Berlapis**

### **A) Ranking Model Utama (skema Assignment)**

Pemenang: **Random Forest (reg)** — lihat Tabel 3.3.

### **B) Ranking Extended (default, belum tuning setara)**

| Rank | Model | F1 | Recall | Precision | ROC-AUC | Alasan singkat pola metrik |
|------|-------|------|--------|-----------|---------|----------------------------|
| 1 | **LightGBM** | **0.877** | 0.838 | 0.919 | 0.984 | Boosting leaf-wise + default cocok tabular AI4I; belum dijinakkan seperti RF tuned |
| 2 | CatBoost | 0.806 | 0.794 | 0.818 | 0.978 | Kuat, sedikit di bawah LightGBM pada seed/setup ini |
| 3 | ANN (MLP) | 0.683 | 0.632 | 0.741 | 0.976 | Butuh scaling; kapasitas terbatas tanpa tuning arsitektur |
| 4 | Decision Tree | 0.559 | 0.838 | 0.419 | 0.911 | Recall tinggi tapi banyak FP (Precision rendah) |
| 5 | AdaBoost | 0.541 | 0.485 | 0.611 | 0.965 | Kurang agresif pada minority |
| 6 | Naive Bayes | 0.493 | 0.529 | 0.462 | 0.932 | Asumsi independensi fitur dilanggar (korelasi RPM–Torque kuat) |
| 7 | SVM | 0.451 | **0.882** | 0.303 | 0.972 | `class_weight=balanced` → Recall tinggi, Precision hancur (banyak false alarm) |
| 8 | KNN | 0.374 | 0.250 | 0.739 | 0.864 | Jarak di ruang fitur + imbalance → banyak Failure terlewat |

**Mengapa LightGBM bisa “menang F1 global” tetapi tidak menggantikan kesimpulan Assignment?**

1. LightGBM masuk kelompok **Extended (default)**; RF adalah **Main (tuned anti-overfit)**. Perbandingan belum apple-to-apple.  
2. Selisih F1 LightGBM vs RF hanya ~0.015 pada **~68 failure** → sensitif 1–2 kesalahan prediksi.  
3. RF tetap unggul **AUC (0.988 vs 0.984)** dan merupakan jawaban hipotesis utama (XGB vs RF vs LR).  
4. Best practice laporan: LightGBM = **temuan future work** (wajib di-tune setara sebelum diklaim superior).

Gambar: `fig16_main_models.png`, `fig16_extended_models.png`, `fig16_all_models_comparison.png`.

---

## **3.6 Sensitivitas Rasio SMOTE (pada Random Forest)**

**Tabel 3.6. Pengaruh SMOTE Ratio terhadap Test RF**

| SMOTE Ratio | Test F1 | Recall | Precision | ROC-AUC | Alasan |
|-------------|---------|--------|-----------|---------|--------|
| **0.2** | **0.853** | 0.809 | **0.902** | 0.988 | Sedikit sintetis → Precision terjaga |
| 0.5 | 0.778 | 0.824 | 0.737 | 0.988 | Lebih banyak Failure sintetis → FP naik |
| 0.7 | 0.752 | 0.824 | 0.691 | 0.984 | Pola sama: Recall flat, Precision terus turun |
| 1.0 | 0.742 | 0.824 | 0.675 | 0.983 | Over-sampling penuh memperburuk false alarm |

**Kesimpulan metodologi:** memilih SMOTE 0.2 bukan sembarang; empiris F1 terbaik untuk RF. Rasio lebih besar **tidak** menaikkan Recall secara bermakna, tetapi merusak Precision.

---

## **3.7 Uji McNemar dan SHAP (Evidence Statistik + Explainability)**

### **McNemar (prediksi test)**

| Perbandingan | p-value | Interpretasi | Alasan |
|--------------|---------|--------------|--------|
| RF vs Gradient Boosting | ≈ 1.00 | Tidak signifikan | Hanya beda 2–3 prediksi; performa praktis setara |
| RF vs XGBoost | ≈ 0.73 | Tidak signifikan | Demikian pula |

**Mengapa tetap merekomendasikan RF meski McNemar tidak signifikan?**  
McNemar menguji perbedaan **kesalahan prediksi**, bukan secara langsung “F1 lebih tinggi”. Karena prediksi hampir sama, p besar. Pemilihan RF tetap sah berdasarkan **F1@0.5 + AUC + konteks operasional** (lebih baik atau setara, dengan ranking skor terbaik).

### **SHAP — Random Forest (model rekomendasi)**

| Fitur (mean \|SHAP\|) | Peran domain |
|------------------------|--------------|
| Rotational speed (rpm) | Zona gagal power/kecepatan |
| Strain (Torque×Tool wear) | Fitur turunan keausan + beban |
| Power (RPM×Torque) | Daya potong / overload |
| Temp_diff | Gradien suhu proses–udara |
| Tool wear | Keausan pahat |
| Torque | Beban torsi langsung |

**Alasan urutan ini masuk akal:** EDA menunjukkan zona kegagalan kuat di ruang RPM–Torque dan Tool wear–Torque; feature engineering Power/Strain/Temp_diff memang didesain menangkap mekanisme fisik tersebut — SHAP mengonfirmasi bahwa model RF memakai sinyal yang sama, bukan artefak acak.

Gambar: `fig22_shap_summary_rf.png`, `fig22_shap_bar_rf.png`.

---

## **3.8 Kesimpulan Bab 3 (untuk Sistem Predictive Maintenance)**

1. **Model produksi dalam skema penelitian ini: Random Forest (reg).**  
   Alasan: F1@0.5 tertinggi di model utama (0.862), ROC-AUC tertinggi (0.988), Precision tinggi (0.903) dengan Recall 0.824 — seimbang untuk early warning tanpa false alarm berlebihan.

2. **Gradient Boosting** adalah kompetitor terdekat (F1 0.855; Recall sama). McNemar tidak signifikan → setara statistik; RF dipilih karena F1@0.5 & AUC sedikit lebih baik.

3. **XGBoost (reg)** sudah keluar dari overfit parah (gap Train–Val 0.018; F1 test 0.846) dan layak sebagai alternatif.

4. **LR-Poly** tetap underfit untuk produksi (F1 0.40) meski Recall tinggi — Precision terlalu rendah.

5. **LightGBM (default)** mencatat F1 tertinggi di extended (0.877). Ini **bukan** mengganti kesimpulan Assignment, melainkan peluang **future work** dengan tuning setara.

6. **SMOTE 0.2** terbukti pilihan terbaik untuk RF pada sensitivitas rasio.

7. **Kebijakan maintenance:** prioritas monitoring sensor/fitur SHAP top (RPM, Strain, Power, Temp_diff, Tool wear).

---

## **3.9 Kelemahan dan Keterbatasan (diperbarui)**

### **Keterbatasan yang masih berlaku**
- Dataset AI4I bersifat **sintetis**.  
- Failure di test hanya ~**68** kasus → metrik F1 sensitif.  
- Extended models (termasuk LightGBM) **belum** di-tune setara Main.  
- Val set kecil (~34 failure) membuat threshold-from-val kurang stabil.

### **Keterbatasan lama yang sudah dijawab oleh eksperimen ini**
- ~~Mitigasi overfit belum diuji~~ → **sudah** (gap XGB 0.28 → 0.018; F1 XGB 0.71 → 0.85).  
- ~~SMOTE hanya satu rasio~~ → **sudah** diuji 0.2/0.5/0.7/1.0 pada RF.  
- ~~Belum ada McNemar~~ → **sudah** (RF vs GB / XGB).  
- ~~Belum ada threshold experiment~~ → **sudah** di Block 13 (kesimpulan tetap F1@0.5).

---

## **3.10 Future Works (revisi prioritas)**

1. **Tuning setara LightGBM/CatBoost** lalu bandingkan head-to-head dengan RF (termasuk McNemar).  
2. Kalibrasi probabilitas + kebijakan threshold berbasis biaya FN vs FP di pabrik.  
3. Multi-class failure modes (TWF/HDF/PWF/OSF/RNF).  
4. Validasi pada data sensor riil / shift domain.  
5. Deployment end-to-end (API inferensi, dashboard, alerting) untuk Final Project (AOL).

---

## **3.11 Tabel Referensi Algoritma (literatur — tetap relevan)**

Tabel referensi studi sebelumnya (Al Mamlook, Sakmar, Cioch, dll.) tetap dapat digunakan sebagai konteks literatur. Yang berubah adalah **klaim hasil empiris studi ini**: pemenang Main = **Random Forest (reg)**; temuan Extended menonjol = **LightGBM (default)**.

---


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

