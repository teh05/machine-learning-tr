BINUS UNIVERSITY GRADUATE PROGRAM 

5 ¥ 4z ea 

People Innovation Excellence 

a if BINUS UNIVERSITY GRADUATE PROGRAM 

td<sup>»</sup> a3 > y aw a, 

People Innovation Excellence 



<!-- Start of picture text -->
4<br>@eeJ<br>BINUS<br>UNIVERSITY<br>GRADUATE<br>PROGRAM<br><!-- End of picture text -->

| Innovation Excellence 



BINUS UNIVERSITY GRADUATE PROGRAM 

**Daftar Isi** 

# **Daftar Gambar** 

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
|Gambar 10|Kurva pembelajaran Train vs Validation (XGB, RF, LR-Poly)|Bab 3.3 Diagnosa kesesuaian|
|Gambar 11|Kurva ROC model utama pada test set|Bab 3.4 Evaluasi|
|Gambar 12|Sensitivitas rasio SMOTE pada Random Forest|Bab 3.4 Evaluasi|
|Gambar 13|SHAP summary dan ranking fitur Random Forest|Bab 3.4 Evaluasi|



# **Daftar Tabel** 

|No.|Judul Tabel|Halaman/Bagian|
|---|---|---|
|Tabel 1|Ringkasan Penelitian Terdahulu|Bab 1|
|Tabel 2|Informasi Dataset AI4I 2020|Bab 2|
|Tabel 3|Deskripsi Lengkap 14 Fitur Dataset|Bab 2.1|
|Tabel 4|Ringkasan Kualitas Data|Bab 2.1|
|Tabel 5|Ringkasan Kualitas Data|Bab 2.1|
|Tabel 6|Korelasi Fitur terhadap Machine Failure|Bab 2.1|
|Tabel 7|Ringkasan Kualitas Data|Bab 2.1|
|Tabel 8|Kolom yang Dihapus dan Alasannya|Bab 2.2|
|Tabel 9|Rencana Feature Engineering|Bab 2.2|
|Tabel 10|Rencana Penanganan Outlier|Bab 2.2|
|Tabel 11|Rencana Encoding Fitur Kategorikal|Bab 2.2|
|Tabel 12|Rencana Standardisasi Fitur|Bab 2.2|
|Tabel 13|Distribusi Kelas Sebelum dan Sesudah SMOTE|Bab 2.2|
|Tabel 14|Pembagian Dataset Train/Validasi/Test|Bab 2.2|



COMP8043041 – Machine Learning 

|Tabel 15|Perbandingan Karakteristik Model|Bab 2.3|
|---|---|---|
|Tabel 16|Rencana Hyperparameter yang Dioptimalkan|Bab 2.3|
|Tabel 17|Metrik Evaluasi dan Prioritas Konteks Manufaktur|Bab 2.3|
|Tabel 18|Ringkasan Pipeline Eksperimen|Bab 2.3|
|Tabel 23|Hasil Test Model Utama (F1@0,5)|Bab 3.4|
|Tabel 24|Ranking Model Extended|Bab 3.4|
|Tabel 25|Sensitivitas Rasio SMOTE pada RF|Bab 3.4|
|Tabel 26|Uji McNemar RF vs GB / XGB|Bab 3.4|



# Source Code : 

Kode terbaru Github : https://github.com/teh05/machine-learning-tr.git Kode old code Google Collab : = <u>https://colab.research.google.com/drive/1wfPW8hYMrGNpVUHbgSH9Xdmy2vqF4TN6?usp sharing</u> Video :  https://youtu.be/PRQM3csHQBM 

Link dataset : https://www.kaggle.com/datasets/stephanmatzka/predictive-maintenance-dataset-ai4i-2020 

COMP8043041 – Machine Learning 

# **Bab 1. Pendahuluan** 

# **1.1 Latar Belakang Masalah** 

Keberlanjutan operasional mesin produksi merupakan isu strategis dalam konteks Industri 4.0. Kegagalan mesin yang tidak terjadwal (unplanned downtime) dapat menimbulkan kerugian operasional yang meliputi biaya perbaikan darurat, penghentian lini produksi, serta gangguan rantai pasok. Pendekatan perawatan konvensional, yaitu reactive maintenance dan preventive maintenance, memiliki keterbatasan: pendekatan reaktif menanggung konsekuensi kerusakan yang telah terjadi, sedangkan pendekatan preventif berisiko melakukan intervensi pada komponen yang masih layak operasi (Çınar et al., 2020; Abidi et al., 2022). 

Predictive maintenance (PdM) berbasis machine learning dikembangkan untuk memperkirakan risiko kegagalan berdasarkan data sensor operasional sehingga intervensi perawatan dapat dijadwalkan secara lebih tepat (Taoufyq et al., 2025; Serradilla et al., 2022). Dalam praktik industri, data kegagalan umumnya bersifat jarang sehingga membentuk permasalahan klasifikasi tidak seimbang. Kondisi tersebut dapat menghasilkan accuracy paradox, yaitu akurasi tinggi tanpa kemampuan deteksi kelas kegagalan yang memadai (Yang & Iqbal, 2025; Alnahhal et al., 2026). 

Penelitian ini menempatkan prediksi kegagalan mesin sebagai masalah klasifikasi biner pada dataset AI4I 2020 Predictive Maintenance (Matzka, 2020). Dataset tersebut menyediakan label Machine failure beserta moda kegagalan terkait dan banyak digunakan sebagai benchmark akademik pada kajian PdM tabular. Fokus penelitian diarahkan pada Random Forest sebagai model usulan untuk dasar sistem peringatan dini (early warning), dengan penekanan pada keseimbangan Recall–Precision serta interpretabilitas fitur (Brito et al., 2024; Kareem, 2024). 

# **1.2 Rumusan Masalah**

Berdasarkan latar belakang tersebut, penelitian ini merumuskan masalah sebagai berikut:

1. Parameter sensor dan fitur turunan manakah yang paling berkontribusi terhadap prediksi `Machine failure` pada dataset AI4I 2020?
2. Bagaimana membangun model klasifikasi biner yang andal untuk prediksi kegagalan mesin pada data yang sangat tidak seimbang?
3. Bagaimana perbandingan kinerja Random Forest sebagai model usulan terhadap XGBoost, Logistic Regression–Polynomial, Gradient Boosting, serta model extended (termasuk LightGBM) pada protokol evaluasi yang sama?
4. Failure mode manakah yang paling sering terjadi, dan apa implikasinya bagi kebijakan *predictive maintenance*?

# **1.3 Tujuan dan Ruang Lingkup** 

# **Tujuan Penelitian:** 

- a) Mengidentifikasi parameter sensor mesin (suhu, torsi, kecepatan, keausan alat) yang paling berkontribusi terhadap kegagalan mesin 

- b) Membangun model prediksi klasifikasi biner: apakah mesin akan mengalami kegagalan atau beroperasi normal 

- c) Membandingkan performa lebih dari satu algoritma machine learning dalam menangani data imbalanced (kegagalan mesin jauh lebih jarang dari kondisi normal) 

- d) Mengidentifikasi jenis moda kegagalan (failure modes) yang paling sering terjadi sebagai dasar kebijakan maintenance berbasis risiko 

COMP8043041 – Machine Learning 

**Ruang Lingkup:** 

1. **Dataset** : AI4I 2020 Predictive Maintenance Dataset (UCI Machine Learning Repository / Kaggle) 

2. **Target variabel primer** : <mark>Machine failure</mark> (biner: 1 = Gagal, 0 = Normal) 

3. **Target variabel sekunder (opsional)** : Multi-class failure modes (TWF, HDF, PWF, OSF, RNF) 

4. **Jenis masalah** : Binary Classification (utama) + Multi-class Classification (lanjutan) 

5. **Model yang dibandingkan** : Random Forest (usulan); XGBoost (pembanding utama); Logistic Regression–Polynomial (baseline); Gradient Boosting dan model extended (termasuk LightGBM) sebagai pembanding tambahan. Dan model lainnya yang digunakan untuk percobaan. 

6. **Evaluasi** : Accuracy, Precision, Recall, F1-Score, ROC-AUC 

# **1.4 Tinjauan Penelitian Terdahulu dan Research Gap** 

Tabel 1 Ringkasan Penelitian Terdahulu 

|**No**|**Judul penelitian (ringkas)**|**Peneliti &**<br>**tahun**|**Tujuan**|**Model / teknologi /**<br>**dataset**|**Kelebihan**|**Kekurangan**|
|---|---|---|---|---|---|---|
|1|Machine learning in predictive<br>maintenance towards<br>sustainable smart manufacturing<br>in Industry 4.0. Sustainability|Çınar et al.<br>(2020)|Memetakan<br>penerapan ML<br>pada PdM|ML: ANN, SVM, D<br>T, RF, LR,<br>XGBoost, GBM,<br>dll. Dataset: real &<br>synthetic; Bosch,<br>SECOM, NASA<br>Turbofan/CMAPSS.|Landasan luas<br>tren PdM–ML|penggunaan satu<br>metode saja kurang<br>optimal; beberapa<br>studi belum<br>melakukan parameter<br>tuning dan cross-<br>validation dapat<br>terkendala resource.|
|2|Perbandingan XGBoost vs<br>Random Forest untuk PdM|Kareem<br>(2024)|Membandingkan<br>XGB dan RF|XGBoost, Random<br>Forest; konteks<br>PdM|Perbandingan<br>head-to-head<br>ensemble|Belum menekankan<br>pipeline anti-overfit +<br>SMOTE terkendali +<br>XAI pada AI4I|
|3|Prediksi kegagalan perangkat<br>industri (AI4I 2020)|Muhidin et<br>al. (2024)|Prediksi failure<br>pada AI4I|ML pada AI4I 2020|Fokus langsung<br>dataset AI4I|Analisis imbalance/F1<br>dan usulan RF belum<br>sedalam studi ini|
|4|Metode penanganan imbalance<br>pada PdM multiclass|Alnahhal et<br>al. (2026)|Membandingkan<br>strategi<br>imbalance|RF, XGB, SVM, k-<br>NN, MLR; AI4I<br>2020|Evaluasi<br>sistematis<br>imbalance &<br>multi-moda|Fokus multiclass;<br>belum mengusulkan<br>RF biner + SHAP<br>sebagai early warning|
|5|Baseline robust & kalibrasi<br>probabilitas PdM|Dale Luche<br>et al. (2026)|Baseline failure<br>detection +<br>kalibrasi|RF, MLP; AI4I<br>2020|Menekankan<br>validasi ketat &<br>kalibrasi|Belum memosisikan<br>RF sebagai model<br>usulan vs XGB/LR<br>secara berlapis|
|6|Cost-optimised model<br>comparison untuk PdM|Yang &<br>Iqbal (2025)|Membandingkan<br>model berbasis<br>biaya|Berbagai ML; data<br>imbalanced PdM|Menyoroti<br>batas<br>Accuracy/F1 vs<br>biaya|Belum spesifik<br>pipeline anti-overfit<br>RF pada AI4I biner|
|7|Explainable PdM<br>(LIME/SHAP/PDP/ICE)|Brito et al.<br>(2024)|Meningkatkan<br>interpretabilitas<br>prediksi PdM|XAI pada model<br>ML PdM|Menekankan<br>explainability<br>operasional|Tidak berfokus<br>justifikasi RF sebagai<br>model utama pada<br>AI4I imbalanced|



COMP8043041 – Machine Learning 

Research gap. Penelitian terdahulu telah membahas PdM berbasis ML, perbandingan RF–XGBoost, penanganan ketidakseimbangan pada AI4I, serta explainability. Namun, masih terdapat celah pada integrasi: (1) prediksi biner Machine failure pada AI4I 2020 dengan penanganan imbalance terkendali; (2) mitigasi overfitting melalui evaluasi pada validation berdistribusi asli; (3) penetapan Random Forest sebagai model usulan yang dibandingkan secara sistematis terhadap XGBoost dan Logistic Regression sebagai baseline; serta (4) penguatan interpretabilitas melalui SHAP pada model usulan. Penelitian ini diarahkan untuk mengisi gap tersebut sesuai judul: Prediksi Kegagalan Mesin Industri Menggunakan Random Forest pada Dataset Tidak Seimbang AI4I 2020. 

# **Bab 2. Pemahaman Data dan Pra-Pemrosesan Data** 

# **2.1 Deskripsi dan Eksplorasi Data** 

# **Sumber Data** 

Dataset yang digunakan adalah AI4I 2020 Predictive Maintenance Dataset yang dikembangkan untuk merepresentasikan kondisi operasional mesin milling secara realistis dan tersedia secara publik (Matzka, 2020). Penggunaan dataset publik dipilih karena data PdM industri riil seringkali terbatas akibat kerahasiaan operasional dan kendala akses (Serradilla et al., 2022). 

**Tabel 2 Informasi Dataset AI4I 2020** 

|**Atribut**|**Keterangan**|
|---|---|
|Nama dataset|AI4I 2020 Predictive Maintenance Classification Dataset|
|Pengembang|Stephan Matzka, HTW Berlin|
|Sumber primer|UCI Machine Learning Repository (Dataset ID: 601)|
|Lisensi|CC BY 4.0|
|Konteks industri|Mesin milling pada lingkungan manufaktur|
|Dimensi|10.000 observasi×14 kolom|



# **Jenis Data dan Karakteristiknya** 

Dataset bersifat tabular dengan kombinasi fitur numerik dan kategorikal. Target primer adalah Machine failure, sementara lima indikator moda kegagalan tersedia sebagai label sekunder (Matzka, 2020). 

|**Parameter**|**Nilai**|
|---|---|
|Jumlah observasi|10.000|
|Jumlah kolom awal|14|
|Missing values|Tidak ada|
|Target primer|Machine failure (0/1)|
|Target sekunder|TWF, HDF, PWF, OSF, RNF|
|Rasiokelas primer|sekitar96,6% Normal: 3,4%Failure|



COMP8043041 – Machine Learning 

|UDI<br>Product<br>ID<br>Type<br>Air temperature<br>[K]<br>Process temperature<br>[K]|Rotational speed<br>[rpm]|Torque|[Nm]<br>Tool wear<br>[min]|Machine failure<br>TWF<br>HDF<br>PWF<br>OSF<br>RNF|
|---|---|---|---|---|
|°<br>1<br>M14860<br>M<br>298.1<br>308.6|1551||428<br>ie}|ie}<br>ie}<br>ie)<br>fe)<br>ie}<br>ie}|
|1<br>2<br>L47181<br>L<br>298.2<br>308.7|1408||46.3<br>3|ie}<br>ie}<br>ie}<br>te}<br>ie}<br>ie}|
|a<br>3<br>L47182<br>L<br>298.1<br>308.5|1498||49.4<br>5|0<br>ie)<br>fe)<br>ie)<br>fe)<br>fe)|
|3<br>4<br>L47183<br>E<br>298.2<br>308.6|1433||39.5<br>7|ie}<br>ie}<br>ie}<br>ie}<br>ie}<br>ie}|
|4<br>5<br>L47184<br>L<br>298.2<br>308.7|1408||40.0<br>9|ie)<br>ie)<br>ie)<br>ie}<br>ie)<br>ie)|









# **Ulasan Kualitas Data** 

# **Kekuatan dataset:** 

Kekuatan. Dataset tidak mengandung nilai hilang, memiliki ukuran yang memadai untuk eksperimen terkontrol, dan menyediakan label moda kegagalan untuk analisis lanjutan. Karakteristik tersebut mendukung reproduktifitas eksperimen akademik (Matzka, 2020). 

Keterbatasan. Ketidakseimbangan kelas bersifat ekstrem (rasio sekitar 28:1), sehingga Accuracy tidak dapat dijadikan kriteria keputusan utama (Yang & Iqbal, 2025; Alnahhal et al., 2026). Selain itu, dataset bersifat sintetis sehingga pola noise dan drift pada data sensor riil belum sepenuhnya terwakili (Azari et al., 2023). Beberapa moda kegagalan sangat jarang (misalnya RNF), sehingga pemodelan multi-kelas memerlukan strategi khusus (Alnahhal et al., 2026). 

# **Tabel .4 Ringkasan Kualitas Data** 

|**Aspek**|**Status**|**Keterangan**|
|---|---|---|
|Missing Values|Tidak ada|df.isnull().sum()menghasilkan 0 untuk semua kolom|
|Tipe Data|Konsisten|Float64, Int64, dan Object (sesuai karakteristik fitur)|
|Imbalanced Class|Sangat Ekstrem|Rasio Normal:Failure ≈ 96.6% : 3.4%|
|Kolom Tidak Informatif|Ada 2 kolom|UDI (hanya index) dan Product ID (redundan dengan Type)|
|Outlier|Ada|Terutama pada Rotational speed [rpm]|
|Dataset Sintetis|Perlu dicatat|Bukan data sensor fisik nyata, namun statistik realistis|



# **Tantangan/Keterbatasan:** 

- **Ketidakseimbangan kelas ekstrem** merupakan salah satu tantangan utama pada dataset ini. Hanya sekitar 3,4% observasi yang termasuk dalam kelas _machine failure_ , sehingga rasio kelas _Normal_ terhadap _Failure_ mencapai sekitar 28:1. Kondisi tersebut menunjukkan adanya _class imbalance_ yang signifikan dan perlu ditangani sebelum proses pelatihan model dilakukan (Arkon Data, 2025). 

- Dataset bersifat sintetis (bukan data sensor nyata dari mesin fisik), sehingga pola kegagalannya lebih "bersih" dari data industri sesungguhnya. (Matzka, 2020). 

COMP8043041 – Machine Learning 

- Beberapa failure modes sangat jarang terjadi: RNF hanya 0.1% dari total data hampir tidak bisa dimodelkan secara terpisah. 

# **Eksplorasi Data (Exploratory Data Analysis)** 

# **A. Statistik Deskriptif Fitur Numerik** 

**Tabel 5. Statistik Deskriptif Fitur Sensor Numerik** 

|**Fitur**|**Mean**|**Min**|**Max**|**Std Dev**|**Distribusi**|
|---|---|---|---|---|---|
|Air temperature [K]|~300.0|295.3|304.5|~2.0|Near normal|
|Process temperature [K]|~310.0|305.7|313.8|~1.5|Near normal|
|Rotational speed [rpm]|~1539|1168|2886|~179.3|Right-skewed|
|Torque [Nm]|~39.99|3.8|76.6|~9.97|Near normal|
|Tool wear [min]|~107.9|0|253|~63.7|Near uniform|



# **B. Distribusi Kelas Target (Machine Failure)** 

**Tabel 6. Distribusi Kelas Target Machine Failure** 

|**Kelas**|**Jumlah**|**Persentase**|
|---|---|---|
|0 – Normal|~9.661|~96.6%|
|1 – Machine Failure|~339|~3.4%|



Rasio imbalanced yang ekstrem ini merupakan tantangan utama yang harus ditangani secara serius sebelum training model. Tanpa penanganan, model akan cenderung selalu memprediksi "Normal" dan tetap mendapatkan accuracy semu ~96% namun gagal total dalam mendeteksi kegagalan mesin. (Sakmar et al., 2025). 

# **C. Distribusi Failure Modes (Multi-label)** 

**Tabel.7 Frekuensi dan Persentase per Failure Mode** 

|**Failure Mode**|**Kode**|**Deskripsi**|**Jumlah Kasus**|**Persentase**|
|---|---|---|---|---|
|Heat Dissipation Failure|HDF|Kegagalan sistem pendinginan|~115|~1.15%|
|Overstrain Failure|OSF|Beban mekanis berlebih|~98|~0.98%|
|Power Failure|PWF|Daya di luar rentang aman|~95|~0.95%|



COMP8043041 – Machine Learning 



<!-- Start of picture text -->
Distribusi Kelas Target: Machine Failure Frekuensi per Failure Mode<br>10000<br>HDF 115<br>8000<br>OSF 98<br>6000<br>€<br>38 PWF 95<br>4000<br>TWF 46<br>2000<br>RNF 19<br>0 t) 1 () 20 40 60 80 100 120<br>Machine failure<br><!-- End of picture text -->



<!-- Start of picture text -->
Distribusi Fitur Sensor per Kelas Kegagalan<br>Distribusi: Air temperature [K] Distribusi: Process temperature [K] Distribusi: Rotational speed [rpm]<br>3 fFailure=0 ©) failure=0 3 failure=0<br>(3 Failure=1 ©) failure=1 0.0030 (3 failure=1<br>0.20 0.30<br>025 0.0025<br>0.15<br>a8>coro a8>i0.20os a&>c0.00200.0015<br>0.10 0.0010<br>0.05<br>0.05 0.0005<br>0.00 294-296 «= 298 = 300. 302-304 306 0.00 306 308 310 312 314 0.0000 1000 1500 2000 2500 3000<br>Air temperature [K] Process temperature [K] Rotational speed [rpm]<br>0.040 Distribusi: Torque [Nm] [= failure=0 0.007: Distribusi: Too! wear [min]= failure=o Lo<br>[5 Failure=1 5 failure=1<br>0.035<br>0.006 0.8<br>0.030<br>0.005<br>0.025 0.6<br>2 2 0.004<br>a§ 0.020 &5<br>0.003 0.4<br>0.015<br>0.002<br>0.010<br>0.2<br>0.005 0.001<br>0.000 0.000 0.0<br>() 20 40 60 80 -50 0 50 100 150 200 250 300 0.0 0.2 0.4 0.6 08 10<br>Torque [Nm] Tool wear [min]<br><!-- End of picture text -->



<!-- Start of picture text -->
Distribusi Fitur Sensor: Normal vs Failure<br>Boxplot: Air temperature [K] Boxplot: Process temperature [K] Boxplot: Rotational speed [rpm]<br>304 314 g<br>313 2750 g :<br>312 2500 8<br>o*x Zg 311 EE 2250 °°<br>rd @ 310 Q<br>g 300 = 2 2000 °<br>A 309 5 8<br>raz 3g a& 1750<br>298 & 308 «<br>307 1500<br>296 306 8 1250<br>0) 1 0) 1 0) 1<br>Machine failure Machine failure Machine failure<br>80 Boxplot: Torque [Nm] Boxplot: Tool wear [min] 10.<br>250<br>70<br>08<br>60 200<br>= 50 =c 0.6<br>g E 150<br>vo5<br>e30 3 100 04<br>20 8 5° 0.2<br>10 i<br>8 0<br>() 1 0 1 0.0 0.0 0.2 0.4 0.6 08 1.0<br>Machine failure Machine failure<br><!-- End of picture text -->



<!-- Start of picture text -->
Heatmap Korelasi Fitur Sensor vs Machine Failure 1.00<br>Air temperature [K] -<br>0.75<br>Process temperature [K] 0.50<br>- 0.25<br>Rotational speed [rpm] - 0.02 0.02<br>- 0.00<br>Torque [Nm] - 0.01 -0.01 -0.88<br>-—-0.25<br>Tool wear [min] - 0.01 0.01 0.00 -0.00 -—0.50<br>—-0.75<br>Machine failure - 0.08 0.04 -0.04 0.19 0.11<br>\ \ \ \ \ \ —1.00<br>¥ — E = Ss<br>¥ ¥ c = E ia<br>ZF3F33<br>a<br>v & g o o g<br>a v a S = =<br>Ee a a - = G<br>2 2== =22 222 =GG<br>5 4 B<br>eS-5-5 Z<br><!-- End of picture text -->

Process temperature [K] 0.50 - 0.25 Rotational speed [rpm] - 0.02 0.02 - 0.00 Torque [Nm] - 0.01 -0.01 -0.88 -—-0.25 Tool wear [min] - 0.01 0.01 0.00 -0.00 -—0.50 —-0.75 Machine failure - 0.08 0.04 -0.04 0.19 0.11 \ \ \ \ \ \ —1.00 ¥ — E = Ss ¥ ¥ c = E ia ZF3F33 a v & g o o g a v a S = = Ee a a - = G 2 2== =22 222 =GG 5 4 B eS-5-5 Z 



<!-- Start of picture text -->
Zona Kegagalan: RPM vs Torque (Power Zone) Zona Kegagalan: Tool Wear vs Torque (Strain Zone)<br>80 80<br>*. Machine failure e ‘ e e ‘ Machine failure<br>70 ete’ . e (0 10 2 « . 7 ,e? * 0<br>60 aar eae e1 ©hadgore‘4 «awe7%, be¢ater’,ioe ) eee¢ ph.* Aasate* 9 ©ise Po Fas—<«el<br>ee 60 % ts Pate & not oaks on ?é<br>ay ieee... ene)Ob Wate a {FaleSESE na atuonn te St hn Sh 1 See oe2 lee, ae W o®<br>‘@ 40 SSS ‘@ 40 BS so sas? Diekentisacaestnecenticcns oS<br>30 Masdis te, 30] EPS rncunalseer Ue Sawa Senne: Wecomam nes, 3.<br>20 a 20 eee Ff i  o ate 2 ’ + a<br>: ‘ , ss te Cg eo ogete ‘octet 2 @° = ~ PY<br>10 5 OOP ee ge Soeec8,%° eGte,2 CoasewieSe gSHe? « 8.5 cook '@ oé<br>%, 10 *¥ e @ e<br>a ‘ ‘4 e e<br>1250 1500 1750 2000 2250 2500 2750 () 50 100 150 200 250<br>Rotational speed [rpm] Tool wear [min]<br><!-- End of picture text -->

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
|Temp_diff|Float64|
|Power|float64|
|Strain|Float64|
|dtype:<br>object||





<!-- Start of picture text -->
Distribusi Fitur Turunan (Feature Engineering) per Kelas Kegagalan<br>le-5 KDE: Power KDE: Strain KDE: Temp_diff<br>4.0 [23 Normal [3 Normal ] [3 Normal<br>(5 Machine Failure 0.00012 (5 Machine Failure (© Machine Failure<br>35 O4f 00°<br>0.00010<br>3.0<br>25 0.00008 03<br>ga20 &a0.00006 8a0.2<br>15<br>0.00004<br>1.0 o1<br>0.00002<br>os<br>0.0 0.00000 0.0<br>0 20000 40000 60000 80000 100000 120000 5000 0 5000 10000 15000 20000 7 8 9 10 n R 13<br>Power Strain Temp_diff<br><!-- End of picture text -->



<!-- Start of picture text -->
Outlier: Sebelum vs Sesudah Winsorization<br>Air Sebelumtemperature ProcessSebelumtempera RotationalSebelumspee TorqueSebelum[Nm] ToolSebelumwear [min]<br>314 80 250 7<br>8 313 2750 70<br>312 2500 60 200<br>302<br>300 pt} 311310 22502000 5040 ‘| 150 4<br>L 309 1750 t 0 100<br>298 308 re 20<br>307 1500 ct 50<br>296 306 150 —| 10 ° +<br>Air temperature [K] Process temperature [K] Rotational speed [rpm] Torque [Nm] ‘Tool wear [min]<br>Air Sesudahtemperature ProcessSesudahtempera RotationalSesudahspee TorqueSesudah[Nm] ToolSesudahwear [min]<br>304 313 2200 6 200<br>302 aaul 2000 50 150<br>300 — 310 1800 t 40 |} 100<br>298 309 1600 an) 30<br>308 ne ad<br>296 307 1400 —F+ 20 0<br>Air temperature [k] Process temperature [K] Rotational speed [rpm] Torque [Nm] Tool wear [min]<br><!-- End of picture text -->

**Tabel 11. Rencana Encoding Fitur Kategorikal** 

|**Fitur**|**Nilai Asli**|**Metode Encoding**|**Hasil**|**Justifikasi**|
|---|---|---|---|---|
|Type|L, M, H|Ordinal Encoding|L=0, M=1, H=2|Ada urutan kualitas logis: Low < Medium < High|
|UDI|1–10.000|Dihapus|—|Hanya identifier, bukan fitur|
|Product ID|String|Dihapus|—|Redundan denganType|
|Semua fitur lain|Numerik|Tidak perlu encoding|—|Sudah dalam format numerik|



# **d. Data Standardization** 

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



# **e. Mengatasi Ketidakseimbangan Data** 

Ketidakseimbangan kelas merupakan tantangan terbesar dataset ini rasio ~96.6%:3.4% (Normal:Failure) setara dengan rasio ~28:1. Tanpa penanganan, model akan cenderung selalu memprediksi "Normal" dan tetap mendapatkan _accuracy_ semu ~96%  namun gagal total mendeteksi kegagalan mesin yang justru menjadi tujuan utama penelitian. 

Tiga strategi dikombinasikan sesuai karakteristik masing-masing model: 

COMP8043041 – Machine Learning 



<!-- Start of picture text -->
ees Train: (7000, 9), Val: (1000, 9), Test: (2000, 9)<br>Distribusi kelas Train sebelum SMOTE:<br>Machine failure<br>8 6763<br>al 237<br>Name: count, dtype: int64<br>Distribusi kelas Train sesudah SMOTE:<br>Machine failure<br>() 6763|<br>1 2028<br>Name: count, dtype: int64<br>Distribusi Kelas: Sebelum vs Sesudah SMOTE<br>Sebelum SMOTE Sesudah SMOTE<br>7000 7000<br>6000 6000<br>5000 5000<br>4000 4000<br>3000 3000<br>2000 2000<br>1000 1000<br>0 fe)<br>0 1 0 1<br>Machine failure Machine failure<br><!-- End of picture text -->

Test (asli) ~1.932 (96.6%) ~68 (3.4%) 28.5 : 1 

# **f. Data Splitting (Train/Validasi/Test)** 

Stratified split memastikan proporsi kelas kegagalan yang kecil (~3.4%) terwakili secara proporsional di setiap subset:[2] 

**Tabel 14. Pembagian Dataset Train/Validasi/Test** 

|**Split**|**Proporsi**|**Jumlah Baris**|**Kasus Failure**|**Keterangan**|
|---|---|---|---|---|
|Training Set|70%|7.000 baris|~237 kasus|Untuk melatih model; SMOTE diterapkan di sini|
|Validation Set|10%|1.000 baris|~34 kasus|Untuk hyperparameter tuning|
|Test Set|20%|2.000 baris|~68 kasus|Evaluasi akhir  tidak disentuh selama training|



Selain pembagian hold-out ini, **5-Fold Stratified Cross-Validation** akan diterapkan pada training set untuk memaksimalkan pemanfaatan data dan mendapatkan estimasi performa model yang lebih robust. 

# **2.3 Penentuan Model** 

Gambar 9 berikut menyajikan diagram alur ( _flowchart_ ) keseluruhan pipeline eksperimen yang dirancang untuk studi kasus Predictive Maintenance ini. Pipeline mencakup sembilan tahap berurutan mulai dari pengumpulan data hingga penarikan kesimpulan dan rekomendasi kebijakan maintenance. 

COMP8043041 – Machine Learning 



<!-- Start of picture text -->
1. Data Collection<br>AI4I 2020 - 10.000 x 14- CC<br>BY 4.0<br>2. EDA<br>Deskriptif + Distribusi<br>failure - Histogram/KDE<br>Boxplot - Korelasi - Scatter<br>zona gagal<br>3. Pra-Pemrosesan<br>Drop UID & Product ID -<br>Power, Strain, Temp_diff<br>IQR + Winsorization - Type:<br>L/M/H > 0/1/2<br>4, Standardisasi<br>StandardScaler (Z-score)<br>Hanya untuk LR - Tree<br>models tanpa scaling<br>5. Imbalanced Data<br>96.6% Normal - 3.4% Failure<br>SMOTE scale_pos_weight = 28.5 class_weight='balanced'<br>strategy=0.3 - k=5 XGBoost RF &LR<br>6. Split Stratified<br>Train 70% - Val 10% - Test<br>20%<br>SMOTE hanya di Training<br>7. Modeling<br>XGBoost - Random Forest -<br>LR Baseline<br>GridSearchCV 5-Fold<br>Stratified<br>8. Evaluasi<br>Recall - F1 - ROC-AUC<br>Precision - Accuracy - CM -<br>SHAP<br>9. Kesimpulan<br>Model terbaik untuk Early<br>Warning<br>Feature importance —<br>Maintenance Policy<br><!-- End of picture text -->

Pemilihan model pada penelitian ini disusun dalam tiga peran: Random Forest sebagai model usulan (main), XGBoost sebagai pembanding utama, dan Logistic Regression sebagai baseline. Pembagian peran tersebut mengikuti judul penelitian serta tujuan perbandingan pada data tidak seimbang. 

# **Random Forest sebagai model usulan (main)** 

Random Forest merupakan metode ensemble berbasis bagging yang membentuk banyak pohon keputusan dan mengagregasi prediksi untuk menurunkan varians. Pada konteks PdM tabular, Random Forest banyak digunakan karena relatif robust terhadap skala fitur, mampu menangkap interaksi non-linear antar sensor, serta mendukung analisis kepentingan fitur dan explainability (Çınar et al., 2020; Brito et al., 2024). Studi perbandingan pada ranah PdM menempatkan Random Forest sebagai kompetitor utama XGBoost (Kareem, 2024), sementara eksperimen pada AI4I menunjukkan Random Forest relevan dalam skenario ketidakseimbangan kelas (Alnahhal et al., 2026; Dale Luche et al., 2026). 

Dalam penelitian ini, Random Forest ditetapkan sebagai model usulan karena: (1) sesuai karakteristik data sensor tabular AI4I; (2) mendukung tujuan identifikasi parameter penting melalui SHAP pada estimator pohon; dan (3) selaras dengan judul yang secara eksplisit menempatkan Random Forest sebagai fokus prediksi kegagalan mesin pada data tidak seimbang. 

# **XGBoost sebagai pembanding utama** 

XGBoost merupakan algoritma gradient boosting yang banyak diterapkan pada masalah klasifikasi tabular, termasuk PdM. Kekuatan utamanya terletak pada kemampuan memodelkan hubungan kompleks serta opsi regularisasi untuk mengendalikan overfitting (Kareem, 2024; Serradilla et al., 2022). Pada dataset AI4I, XGBoost juga sering menjadi salah satu model terbaik dalam konfigurasi tertentu (Alnahhal et al., 2026). 

Oleh karena itu, XGBoost digunakan sebagai pembanding utama terhadap Random Forest agar tujuan perbandingan antaralgoritma terpenuhi secara sistematis. Peran XGBoost pada studi ini adalah challenger, bukan model judul. 

# **Logistic Regression sebagai baseline** 

Logistic Regression berfungsi sebagai acuan kinerja linear (baseline). Model ini transparan dan sering dipakai sebagai batas bawah performa sebelum mengevaluasi metode non-linear/ensemble. Pada data PdM yang imbalanced dan mengandung interaksi fitur, kinerja model linear umumnya terbatas, sehingga perbandingan terhadap ensemble memperjelas kontribusi metode yang lebih kompleks (Alnahhal et al., 2026; Yang & Iqbal, 2025). 

Pada penelitian ini, Logistic Regression dilengkapi Polynomial Features derajat 2 dan class_weight='balanced' agar baseline tidak terlalu naif terhadap ketidakseimbangan kelas, namun tetap mempertahankan peran sebagai acuan linear. Posisi tersebut selaras dengan tujuan penelitian yang menetapkan Logistic Regression sebagai baseline. 

COMP8043041 – Machine Learning 

Tabel 5. Justifikasi Pemilihan Model 

|**Model**|**Peran**|**Alasan teoretis singkat**|**Rujukan**|
|---|---|---|---|
|Random Forest|Model usulan (main)|Ensemble bagging; cocok<br>tabular/non-linear; mendukung<br>SHAP; fokus judul|Kareem (2024); Brito et al.<br>(2024); Dale Luche et al.<br>(2026)|
|XGBoost|Pembanding utama|Boosting kuat pada tabular<br>PdM/AI4I; pembanding adil<br>terhadapRF|Kareem (2024); Alnahhal et al.<br>(2026)|
|Logistic Regression–Poly|Baseline|Acuan kinerja linear;<br>memperjelas nilai tambah<br>ensemble pada data<br>imbalanced|Alnahhal et al. (2026); Yang<br>& Iqbal (2025)|



Dengan demikian, arsitektur perbandingan model pada Bab 3 disusun untuk menguji Random Forest sebagai model usulan terhadap XGBoost dan Logistic Regression pada dataset tidak seimbang AI4I 2020, sesuai judul dan tujuan penelitian. 

**Tabel 15. Perbandingan Karakteristik Model** 

|Aspek|XGBoost|Random Forest|Logistic Regression|
|---|---|---|---|
|Paradigma|Boosting (sequential)|Bagging (parallel)|Linear Model|
|Interpretability|Tinggi (SHAP)|Sedang-Tinggi (feat. importance)|Tinggi (koefisien)|
|Handling Imbalanced|scale_pos_weight|class_weight|class_weight|
|Butuh Feature Scaling|Tidak|Tidak|Ya (wajib)|
|Kecepatan Training|Tinggi|Sedang|Sangat Tinggi|
|Overfitting Risk|Rendah (regularisasi)|Rendah (bagging)|Sedang|
|Benchmark Accuracy AI4I|~98%[^13]|97-98%[^2]|Referensi baseline|



**Tabel 16. Rencana Hyperparameter yang akan Dioptimalkan** 

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



COMP8043041 – Machine Learning 

**Tabel 17. Metrik Evaluasi yang Digunakan.** 

|**Metrik**|**Prioritas**|**Landasan penggunaan**|
|---|---|---|
|F1-score|Utama|Menyeimbangkan Precision dan Recall pada data imbalanced (Alnahhal et al.,<br>2026)|
|Recall|Tinggi|Mengurangi risikokegagalanterlewat (Çınaret al.,2020;Abidiet al.,2022)|
|Precision|Tinggi|Mengendalikan false alarm|
|ROC-AUC|Pendukung|Menilai kualitas ranking skor risiko (Serradilla et al., 2022; Dale Luche et al.,<br>2026)|
|Accuracy|Pelengkap|Tidakdigunakansebagai kriteriakeputusanutama (Yang &Iqbal,2025)|



**Mengapa Recall diutamakan?** Dalam konteks manufaktur, melewatkan satu prediksi kegagalan mesin ( _false negative_ ) dapat berarti mesin beroperasi menuju kerusakan total yang membutuhkan penggantian komponen besar dan menghentikan seluruh lini produksi selama berhari-hari. Biaya _false negative_ di industri manufaktur jauh melampaui biaya _false positive_ berupa inspeksi yang ternyata tidak diperlukan. 

**Tabel 18. Ringkasan Pipeline Eksperimen Lengkap** 

|**Tahap**|**Aktivitas**|**Library/Tools**|**Output**|
|---|---|---|---|
|1. Data Collection|Download AI4I 2020 dari Kaggle|kaggle API, pandas|DataFrame 10.000 × 14|
|2. EDA|Statistik deskriptif, distribusi,<br>heatmap, scatter|pandas, seaborn,<br>matplotlib|5 gambar EDA|
|3. Preprocessing|Hapus kolom, feature engineering,<br>encoding|pandas, numpy|DataFrame 10.000 × 15|
|4. Outlier Treatment|IQR detection + Winsorization|scipy.stats.mstats|DataFrame tanpa outlier<br>ekstrem|
|5. Standardisasi|StandardScaler (untuk LR baseline)|sklearn.preprocessing|X_train_scaled,<br>X_val_scaled, X_test_scaled|
|6. Imbalanced Handling|SMOTE + class_weight +<br>scale_pos_weight|imblearn.over_sampling|X_res (7.000→8.791), y_res|
|7. Data Splitting|Stratified 70/10/20|sklearn.model_selection|Train/Val/Test sets|
|8. Modeling|XGBoost, Random Forest, LR<br>Baseline|xgboost, sklearn|Trained models|
|9. Evaluasi|Recall, F1, ROC-AUC, CM|sklearn.metrics, shap|Laporan perbandingan model|



COMP8043041 – Machine Learning 

**BAB 3 Pengembangan Model dan Evaluasi** 

Bab ini menyajikan pengembangan model setelah mitigasi overfitting, mencakup arsitektur, pelatihan, penyetelan hiperparameter, hasil evaluasi, serta analisis temuan. Angka kinerja merujuk pada eksperimen hold-out yang telah dilakukan. 

# **3.1 Proses Pelatihan Model**

Pelatihan mengikuti protokol anti-*leakage* dan anti-*overfit* sebagai berikut.

1. **Pembagian data.** Split stratified 70/10/20 menghasilkan training 7.000 baris (Failure ≈ 237), validation 1.000 baris (Failure ≈ 34), dan test 2.000 baris (Failure ≈ 68). Validation dan test **tidak** di-oversample agar mencerminkan distribusi operasional.
2. **SMOTE hanya pada training.** `sampling_strategy=0.2` menaikkan kelas Failure training dari 237 menjadi sekitar 1.352 (rasio 1:5), tanpa *double-balancing* pada model pohon (`scale_pos_weight=1`; RF tanpa `class_weight`).
3. **Peran data per model.** XGBoost, Random Forest, dan Gradient Boosting dilatih pada `X_res` (hasil SMOTE). Logistic Regression–Polynomial dilatih pada `X_train` asli dengan `class_weight='balanced'` dan `StandardScaler`.
4. **Seleksi kandidat Random Forest.** Tiga kandidat dibandingkan pada F1 validation: (i) pemenang GridSearch, (ii) RF subsample (`max_samples=0.7`, 800 pohon), dan (iii) soft-vote RF+GB+ExtraTrees (bobot 2-1-1). Kandidat dengan F1 validation tertinggi ditetapkan sebagai `rf_best`.
5. **Metrik keputusan.** F1@0,5 pada test menjadi kriteria ranking utama; threshold optimal dari validation dicatat tetapi tidak menggantikan F1@0,5 karena validation berukuran kecil.

Ringkasan protokol:

| Aspek | Protokol final |
|-------|----------------|
| Split | Stratified 70 / 10 / 20; `random_state=42` |
| SMOTE | `strategy=0.2`, `k_neighbors=5`, hanya training |
| Balancing pohon | Tanpa *double-balancing* |
| LR-Poly | Data asli + `class_weight='balanced'` |
| Seleksi RF | Val F1 tertinggi di antara grid / subsample / soft-vote |

# **3.2 Hyperparameter Tuning** 

Penyetelan dilakukan dengan GridSearchCV dan PredefinedSplit, yaitu pelatihan pada data SMOTE serta penilaian F1 pada validation berdistribusi asli. Pendekatan ini dipilih untuk mengurangi seleksi model yang hanya optimal pada sampel sintetis. 

# **Tuning per Model** 

**Tabel 19. Rencana Hyperparameter Tuning** 

|**Model**|**Fokus parameter**|
|---|---|
|XGBoost|n_estimators, learning_rate, max_depth (3–4),<br>min_child_weight, subsample, reg_lambda;<br>scale_pos_weight=1|
|Random Forest|n_estimators, max_depth, min_samples_split,<br>min_samples_leaf, max_features; tanpa<br>class_weight|
|LR-Poly|C danpenalty (l1/l2) pada classifier|



# **Hasil Tuning** 

**Tabel 20. Hasil Hyperparameter** 

|**Model**|**Best Parameters**|**Best Val-asli F1**|
|---|---|---|
|XGBoost|learning_rate=0.05,<br>max_depth=3,<br>min_child_weight=1,<br>n_estimators=200,<br>reg_lambda=1,<br>subsample=1.0;<br>scale_pos_weight=1.0|0.9063|
|Random Forest<br>(grid)|class_weight=None, max_depth=None, max_features=sqrt,<br>min_samples_leaf=1, min_samples_split=2, n_estimators=200|0.9231|
|Logistic<br>Regression–Poly|C=10, penalty=l1, class_weight=balanced, poly degree=2|0.4177|



COMP8043041 – Machine Learning 



<!-- Start of picture text -->
Learning Curve: XGBoost (reg) Learning Curve: Random Forest (reg) Learning Curve: LR-Poly<br>0.924 —@ Training F1 —® Training Fl —® Training F1<br>6 cvFl 0.984 -@ CVF —e CVF<br>0.50<br>0.90 0.96<br>0.45<br>82S0.88 &v50.94 &25<br>am ose" in 0.92 a 0.40<br>0.84 0.90<br>0.35<br>0.82 0.88<br>5600 5800 6000 6200 6400 5600 5800 6000 6200 6400 1000 2000 3000 4000 5000<br>Jumiah Data Training Jumlah Data Training Jumiah Data Training<br><!-- End of picture text -->

dll.) bekerja: tidak “menghafal” berlebihan. 

# **Random Forest (reg)** 

Train sangat tinggi (0.989), Val tetap kuat (0.937), tapi gap 0.052 sedikit di atas ambang 0.05. Artinya RF hampir sempurna di data latih (kapasitas ensemble pohon tinggi), sementara di validation ada penurunan kecil indikasi mild overfitting, bukan gagal total. Val F1 tetap yang tertinggi di antara ketiga model, jadi trade-off-nya: performa val bagus, tapi sedikit lebih “longgar” di train dibanding XGBoost. 

# **LR-Poly** 

Train dan Val sama-sama rendah (~0.42), gap hampir nol / sedikit negatif. Bukan overfit; model underfit  bahkan di training tidak menangkap pola kegagalan dengan baik. Cocok hanya sebagai baseline linear, bukan kandidat utama. 

# **3.3 Uji Stabilitas Model (Repeated Stratified K-Fold, 5×3)** 

Skor tunggal dari satu partisi data belum cukup untuk mendukung klaim pemilihan model. Karena itu dilakukan validasi silang berulang (5 lipatan, 3 pengulangan) pada data sesuai protokol masing masing model, untuk menilai apakah peringkat model konsisten dan seberapa besar variansinya. 

**Tabel 22. Stabilitas Kinerja (Repeated Stratified K-Fold)** 

|**Model**|**CV F1**|**CV Recall**|**CV Precision**|**CV ROC-AUC**|
|---|---|---|---|---|
|**Random Forest (reg)**|**0.941 ± 0.010**|**0.904 ± 0.018**|**0.982 ± 0.007**|**0.996 ± 0.001**|
|**Gradient Boosting (default)**|0.915 ± 0.013|0.867 ± 0.019|0.969 ± 0.011|0.990 ± 0.002|
|**XGBoost (reg)**|0.906 ± 0.011|0.847 ± 0.018|0.974 ± 0.013|0.991 ± 0.002|
|**LR-Poly (reg)**|0.402 ± 0.018|0.880 ± 0.042|0.261 ± 0.015|0.959 ± 0.014|



Interpretasi: Random Forest menempati peringkat teratas pada F1 (0,941) dan Precision (0,978) dengan simpangan baku terkecil, menandakan kinerja yang tinggi sekaligus stabil. Perlu dicatat secara metodologis bahwa skor validasi silang pada data hasil SMOTE cenderung lebih optimistis dibanding evaluasi pada data uji berdistribusi asli. Meski demikian, pola peringkat relatif tetap konsisten: RF > GB > XGB ≫ LR. Konsistensi inilah yang menjadi dasar untuk memusatkan 

COMP8043041 – Machine Learning 

analisis lanjutan pada Random Forest sebagai model usulan. 

# **3.4 Perbandingan Multi-Algoritma (Eksplorasi)** 

Untuk memastikan pilihan tidak sempit, dilakukan eksplorasi terhadap dua kelompok model. Kelompok utama mencakup model yang disetel/direncanakan (Random Forest, Gradient Boosting, XGBoost, dan Logistic Regression–Polynomial). Kelompok extended mencakup delapan algoritma tambahan dengan konfigurasi bawaan (LightGBM, CatBoost, ANN/MLP, Decision Tree, AdaBoost, Naive Bayes, SVM, dan KNN) sebagai pembanding eksploratif. 

# **3.4.1 Hasil Evaluasi Model pada Test Set (Hold-out)** 

Evaluasi utama dilakukan pada test set (2.000 baris; Failure ≈ 68) dengan F1-score pada threshold 0,5 sebagai metrik keputusan. 

**Tabel 23. Hasil Test Model Utama (F1@0,5)** 

|**Rank**|**Model**|**Accuracy**|**Precision**|**Recall**|**F1@0,5**|**ROC-AUC**|
|---|---|---|---|---|---|---|
|1|Random Forest (reg)|0,993|0,965|0,809|0,880|0,988|
|2|Gradient Boosting<br>(default)|0,991|0,889|0,824|0,855|0,985|
|3|XGBoost (reg)|0,990|0,887|0,809|0,846|0,983|
|4|LR-Poly (reg)|0,910|0,260|0,897|0,403|0,968|



**Tabel 24. Ranking Model Extended (konfigurasi bawaan)** 

|**Rank**|**Model**|**F1-Score**|**Recall**|**Precision**|**ROC-AUC**|
|---|---|---|---|---|---|
|1|**LightGBM**|**0,877**|**0,838**|**0,919**|**0,984**|
|2|**CatBoost**|0,806|0,794|0,818|0,978|
|3|**ANN (MLP)**|0,683|0,632|0,741|0,976|
|4|**Decision Tree**|0,559|0,838|0,419|0,911|
|5|**AdaBoost**|0,541|0,485|0,611|0,965|
|6|**Naive Bayes**|0,493|0,529|0,462|0,932|
|7|**SVM**|0,451|**0,882**|0,303|0,972|
|8|**KNN**|0,374|0,250|0,739|0,864|

Evaluasi dilengkapi *classification report* per model utama (Precision/Recall/F1 per kelas pada test) dan **kurva ROC** (ig20_roc_main_models.png) untuk menilai kualitas ranking skor risiko.

**Tabel 25. Sensitivitas Rasio SMOTE pada Random Forest (komponen pohon)**

| SMOTE Ratio | Test F1 | Recall | Precision | ROC-AUC |
|-------------|---------|--------|-----------|---------|
| **0,2** | **0,875** | 0,824 | **0,933** | 0,988 |
| 0,5 | 0,767 | 0,824 | 0,718 | 0,988 |
| 0,7 | 0,752 | 0,824 | 0,691 | 0,985 |
| 1,0 | 0,728 | 0,809 | 0,663 | 0,984 |

Interpretasi: menaikkan rasio SMOTE dari 0,2 ke 1,0 tidak meningkatkan F1; F1 turun dari 0,875 menjadi 0,728. Recall relatif stagnan (sekitar 0,824) lalu sedikit turun pada rasio 1,0 (0,809), sementara Precision menurun tajam dari 0,933 menjadi 0,663. Oversampling agresif menambah *false positive* tanpa menambah kemampuan deteksi. Gambar ig18_smote_sensitivity_rf.png memperlihatkan pola tersebut.

**Tabel 26. Uji McNemar (prediksi test)**

| Perbandingan | n01 | n10 | p-value | Kesimpulan |
|--------------|-----|-----|---------|------------|
| RF vs Gradient Boosting | 5 | 1 | 0,219 | Tidak signifikan |
| RF vs XGBoost | 5 | 0 | 0,063 | Tidak signifikan |

Keunggulan Random Forest pada studi ini bersifat **praktis** (F1, Precision, ROC-AUC), bukan klaim perbedaan prediksi yang signifikan secara statistik.




COMP8043041 – Machine Learning 



<!-- Start of picture text -->
A) Model Utama Assignment — RF sebagai pemenang Main<br>Random Forest (reg)<br>1.0 wo Mimmm Fl-ScoreRecall<br>Ed in a in EA ME Precision<br>a = 3<br>0.8 = --<br>uw<br>5 0.6<br>A<br>t<br>0.4 a<br>0.2<br>0.0<br>, ec) \ 3)<br>goge a 5 se<br>go ah eo” ar?<br>ee eo™ +<br>_e*<br>of<br><!-- End of picture text -->



<!-- Start of picture text -->
B) Extended Models (default) — LightGBM = temuan eksplorasi<br>LightGBM<br>Mm Fl-Score<br>1.0 Mam Recall<br>a Gl Precision<br>3 7 ca<br>e Si<br>=I me<br>CsS qdce<br>£ 0.6 a= s = a<br>a si w<br>i=] = pie wo<br>= =<br>Si = + EA<br>0.4 = rya<br>eom wsAY<br>0.2<br>0.0<br>x >) ez 5<br>yas ca? ws Q “oo poe we?<br>ia oe 2<br><!-- End of picture text -->



<!-- Start of picture text -->
C) Semua model — RF (vote) vs LightGBM<br>Random Forest (reg)<br>1.0 g mmm F1-Score<br>. S By o . mmm Recall<br>08 8 z= S 8. 8: 7= z zé jm Precisionz<br>gos . g<br>0.4 2, =<br>& 8|<br>0.2<br>0.0<br>a<9) woroo oeRS) osey sooo wswt) ngg& ee?ot weeye? a ssey as<br>owo yr a or" oe pn 3 oo po yor” er<br>go’ mad<br>we<br>oe<br><!-- End of picture text -->



<!-- Start of picture text -->
Sensitivitas Rasio SMOTE pada Random Forest (komponen pohon)<br>00<br>—@ Test Fl<br>0.95 —™— Precision<br>“a= Recall<br>Rasio terpilih (0.2)<br>0.90 1G ~<br> ~ ~<br>~“<br>0.85 are<br>2 80 eeSS aa weed SOC POECCETCCCESCEOOS VOCE CEECEECECEOCEOCCOCCCOOLES ¥<br>QO “<br>Wn “ x<br>0.75 SAaSS<br>0.70 a<br>Si<br>0.65<br>0.60<br>0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9 1.0<br>SMOTE sampling_strategy<br><!-- End of picture text -->



<!-- Start of picture text -->
XGBoost (reg) Random Forest (reg) LR-Poly (reg) Gradient Boosting (default)<br>thr=0.85 thr=0.60 thr=0.88 thr=0.86<br>Normal 1932 Normal 2 Normal 1891 Normal 0<br>ry&2ry&2gé2g&2<br>Failure Failure + 15 53 Failure Failure 7 51<br>Normal Predicted label Failure Normal Predicted label Failure Normal Predicted label Failure Normal Predicted label Failure<br><!-- End of picture text -->

. High 

5Sc) © > w v8 



<!-- Start of picture text -->
SHAP Summary — Random Forest (reg)<br><!-- End of picture text -->



<!-- Start of picture text -->
Rotational_speed_rpm oo come ¢<br>Strain ee e cocoa eucee<br>Temp_diff G@mEmece © © © apa<br>Power ) e e eamece<br>Tool_wear_min °<br>Torque_Nm Ocleeent @e<br>Air_temperature_K<br>Type @ecee ecco<br>Process temperature _K °<br>Low<br>—0.2 0.0 0.2 0.4 0.6<br>SHAP value (impact on model output)<br><!-- End of picture text -->



<!-- Start of picture text -->
Top 10 Fitur — Random Forest (mean |SHAP])<br>Rotational_speed_rpm<br>Strain<br>Temp_diff<br>Power<br>Tool_wear_min<br>Torque_Nm<br>Air_temperature_K<br>Type<br>Process_temperature_K<br>0.000 0.005 0.010 0.015 0.020 0.025 0.030 0.035 0.040<br>mean |SHAP|<br><!-- End of picture text -->

1. Kinerja tertinggi pada metrik keputusan. Pada data uji, RF memperoleh F1@0,5 tertinggi (**0,880**) dan ROC-AUC tertinggi (**0,988**) di antara model utama, sekaligus Precision terbaik (**0,965**)—kritis untuk PdM agar alarm palsu ditekan.

2. Paling stabil lintas partisi. Pada validasi silang berulang, RF memimpin F1 (**0,941 ± 0,010**) dan Precision (**0,982 ± 0,007**) dengan simpangan baku kecil, menandakan kinerjanya tidak bergantung pada satu pembagian data tertentu.

3. Generalisasi terkendali. Meskipun kesenjangan Train–Validation sedikit di atas ambang (**0,0524**), Validation F1-nya justru tertinggi. Ini menunjukkan *mild overfitting* yang tidak mengorbankan kemampuan generalisasi.

4. Kokoh terhadap pilihan desain imbalance. Analisis sensitivitas menunjukkan RF mencapai puncak kinerja pada rasio SMOTE konservatif (**0,2**): Test F1 **0,875** dan Precision **0,933**. Menaikkan rasio ke 1,0 menurunkan F1 menjadi **0,728** dan Precision menjadi **0,663**, sementara Recall relatif stagnan (≈ 0,824 lalu 0,809).

5. Keunggulan yang jujur secara statistik. Uji McNemar menegaskan bahwa RF tidak berbeda signifikan dari GB (**p = 0,219**) maupun XGB (**p = 0,063**) pada ambang 0,05; keunggulannya bersifat praktis dan konsisten, bukan artefak satu evaluasi. Ini justru memperkuat keandalan pilihan karena tidak **over-claiming**.

6. Dapat diinterpretasikan. SHAP menghasilkan penjelasan fitur yang selaras dengan pengetahuan domain (rpm, Strain, Temp_diff, Power, Tool wear, Torque), sehingga model layak dipercaya untuk pengambilan keputusan pemeliharaan.

7. Unggul dibanding eksplorasi extended pada kondisi setara. LightGBM memang mencatat F1 default sedikit kompetitif (**0,877**), tetapi belum melalui penyetelan setara. Dalam skema perbandingan yang adil, Random Forest tetap menjadi pilihan yang paling seimbang antara kinerja, stabilitas, kehati-hatian statistik, dan interpretabilitas. 

**Kesimpulan.** Berdasarkan keseluruhan rantai bukti diagnosa kesesuaian, stabilitas, perbandingan multialgoritma, sensitivitas SMOTE, uji signifikansi, dan interpretabilitas **Random Forest (reg) ditetapkan sebagai model rekomendasi** untuk prediksi kegagalan mesin pada dataset AI4I 2020, didukung penanganan ketidakseimbangan terkendali (SMOTE 0,2), pemantauan ambang, dan penjelasan berbasis SHAP. 

# **3.5 Analisis** 

# **Pembahasan hasil** 

Hasil eksperimen menunjukkan bahwa kinerja prediksi Machine failure pada AI4I 2020 dipengaruhi secara material oleh strategi penanganan ketidakseimbangan dan pengendalian overfitting. Pembatasan SMOTE pada rasio 0,2 tanpa double-balancing menurunkan kesenjangan Train–Validation pada XGBoost dan memperbaiki Precision model pohon. Temuan tersebut selaras dengan literatur yang menekankan sensitivitas metode imbalance serta pentingnya evaluasi multi-metrik pada PdM (Alnahhal et al., 2026; Yang & Iqbal, 2025). 

Pada model utama, Random Forest memperoleh F1-score tertinggi (0,880) dan ROC-AUC tertinggi (0,988). 

COMP8043041 – Machine Learning 

Soft-vote RF-dominated meningkatkan Precision (0,965) dengan sedikit penurunan Recall relatif terhadap Gradient Boosting. LightGBM dengan konfigurasi bawaan kompetitif (F1 0,877), namun belum disetel pada skema yang setara dengan model utama sehingga perbandingan perlu ditafsirkan secara hati-hati (Kareem, 2024). 

Analisis sensitivitas SMOTE menunjukkan bahwa peningkatan rasio oversampling tidak meningkatkan Recall secara bermakna, tetapi menurunkan Precision. Oleh karena itu, pemilihan rasio 0,2 memiliki dasar empiris pada protokol eksperimen ini. Interpretasi SHAP pada komponen pohon Random Forest menempatkan rotational speed, Strain, Power, Temp_diff, Tool wear, dan Torque sebagai fitur berpengaruh, konsisten dengan pola EDA dan kebutuhan explainability pada PdM (Brito et al., 2024; Matzka, 2020). 

# **Temuan utama** 

- F1-score lebih tepat dijadikan metrik keputusan dibanding Accuracy pada data AI4I yang imbalanced. 

- Random Forest (reg) unggul pada model utama dan pada perbandingan keseluruhan dalam eksperimen ini. 

- Mitigasi overfitting pada XGBoost berhasil menurunkan gap Train –Validation. 

- Logistic Regression–Polynomial tetap underfit untuk tujuan deteksi yang seimbang. 

- Perbedaan prediksi RF terhadap GB/XGB tidak signifikan menurut McNemar; pemilihan model tetap merujuk F1, Precision, dan ROC-AUC. 

# **Model yang diusulkan** 

Model yang diusulkan pada penelitian ini adalah Random Forest (reg) dengan pipeline sebagai berikut: feature engineering domain (Power, Strain, Temp_diff), Winsorization, stratified split, SMOTE 0,2 hanya pada training, penyetelan/seleksi kandidat berdasarkan F1 validation, serta konfigurasi final berupa soft-vote RF-dominated apabila terpilih pada tahap validasi. Interpretasi fitur dilakukan melalui SHAP pada estimator pohon Random Forest. Model ini diposisikan sebagai dasar sistem peringatan dini pada kerangka eksperimen AI4I 2020, dengan catatan bahwa penerapan operasional memerlukan validasi pada data riil dan kajian biaya kesalahan prediksi (Abidi et al., 2022; Dale Luche et al., 2026). 

# **Keterbatasan** 

- Dataset bersifat sintetis (Matzka, 2020). 

- Jumlah kasus Failure pada test relatif kecil sehingga metrik sensitif terhadap sedikit kesalahan prediksi (Alnahhal et al., 2026). 

- Model extended belum disetel setara dengan model utama. 

- Validation set kecil membuat optimasi threshold kurang stabil (Dale Luche et al., 2026). 

# **Arah penelitian lanjutan (Future Works)** 

- Penyetelan LightGBM/CatBoost pada skema evaluasi setara, dilengkapi uji statistik perbandingan, untuk menjawab rumusan masalah perbandingan algoritma secara lebih adil (Alnahhal et al., 2026; Kareem, 2024). LightGBM default kompetitif (F1 0,877) sehingga menjadi prioritas *future work*, bukan pengganti rekomendasi saat ini. 

COMP8043041 – Machine Learning 

- Perbandingan strategi imbalance tambahan secara sistematis dan anti-leakage (Alnahhal et al., 2026). 

- Perluasan ke klasifikasi moda kegagalan multi-kelas/multi-label (Matzka, 2020). 

- Validasi eksternal atau transfer learning menuju data sensor riil (Azari et al., 2023; Serradilla et al., 2022). 

- Kalibrasi probabilitas dan penentuan threshold berbasis biaya FN–FP (Dale Luche et al., 2026; Yang & Iqbal, 2025). 

- Penerjemahan keluaran SHAP menjadi prosedur keputusan perawatan (Brito et al., 2024; Taoufyq et al., 2025). 

- Pengembangan sistem end-to-end (inferensi, pemantauan, dan umpan balik operasional) (Çınar et al., 2020; Taoufyq et al., 2025). 

COMP8043041 – Machine Learning 

## **Referensi:** 

Arkon Data. (2025, August 14). _Data preprocessing: Steps, techniques, and importance in AI and ML_ . <u>https://www.arkondata.com/en/post/data-preprocessing-in-machine-learning</u> 

Matzka, S. (2020). _AI4I 2020 predictive maintenance dataset_ [Data set]. UCI Machine Learning Repository. https://doi.org/10.24432/C5HS5C 

Muhidin, A., Muhtajuddin Danny, & Surojudin, N. (2025). Prediksi kegagalan perangkat industri menggunakan random forest dan SMOTE untuk pemeliharaan preventif. _Bulletin of Computer Science Research, 5_ (5), 1089–1094. https://doi.org/10.47065/bulletincsr.v5i5.745 

Sakmar, M., Kadir, N. T., Shofo, P. A., & Darmawan, A. (2025). Evektivitas XGBoost LightGBM dan CatBoost pada dataset imbalanced predictive maintenance. _Jurnal SINTA: Sistem Informasi dan Teknologi Komputasi, 3_ (1), 36–44. https://doi.org/10.61124/sinta.v3i1.145 

Sestri, E., Karno, A. S. B., & Hastomo, W. (2025). Benchmarking five machine learning models for accurate steel plate defect detection. _CogITo Smart Journal, 11_ (2), 382–401. <u>https://doi.org/10.31154/cogito.v11i2.753.382-401</u> 

Abidi, M. H., Mohammed, M. K., & Alkhalefah, H. (2022). Predictive maintenance planning for Industry 4.0 using machine learning for sustainable manufacturing. Sustainability, 14(6), Article 3387. <u>https://doi.org/10.3390/su14063387</u> Alnahhal, M., Tabash, M. I., Safi, S. K., Absy, M. S. M., & Mamadiyarov, Z. (2026). A comparative study of imbalance-handling methods in multiclass predictive maintenance. Computation, 14(4), Article 88. <u>https://doi.org/10.3390/computation14040088</u> 

Azari, M. S., Flammini, F., Santini, S., & Caporuscio, M. (2023). A systematic literature review on transfer learning for predictive maintenance in Industry 4.0. IEEE Access, 11, 12887–12910. <u>https://doi.org/10.1109/ACCESS.2023.3239784</u> Brito, L. C., Susto, G. A., Brito, J. N., & Duarte, M. A. V. (2024). Explainable predictive maintenance of rotating machines using LIME, SHAP, PDP, ICE. IEEE Access, 12, 28525–28548. <u>https://doi.org/10.1109/ACCESS.2024.3367110</u> 

Çınar, Z. M., Abdussalam Nuhu, A., Zeeshan, Q., Korhan, O., Asmael, M., & Safaei, B. (2020). Machine learning in predictive maintenance towards sustainable smart manufacturing in Industry 4.0. Sustainability, 12(19), Article 8211. https://doi.org/10.3390/su12198211 

Dale Luche, J. R., Goussain, B. G. C. dos S., & de Freitas, C. R. (2026). Robust baselines and probability calibration for TPM-oriented predictive maintenance. International Journal of Prognostics and Health Management, 17(1). https://doi.org/10.36001/ijphm.2026.v17i1.4659 

Kareem, A. (2024). Comparative analysis of XGBoost and random forest for predictive maintenance. Annals of the Faculty of Engineering Hunedoara, 22(4), 113–120. 

Muhidin, A., Danny, M., & Surojudin, N. (2024). Prediksi kegagalan perangkat industri menggunakan machine learning pada dataset AI4I 2020. Bulletin of Computer Science Research, 4(2). <u>https://hostjournals.com/bulletincsr/article/view/745</u> 

Serradilla, O., Zugasti, E., Rodriguez, J., & Zurutuza, U. (2022). Deep learning models for predictive maintenance: A survey, comparison, challenges and prospects. Applied Intelligence, 52(10), 10934–10964. <u>https://doi.org/10.1007/s10489-021-03004-y</u> 

COMP8043041 – Machine Learning 

Taoufyq, H., El Guemmat, K., Mansouri, K., & Akef, F. (2025). Predictive maintenance approaches: A systematic literature review. Journal of Industrial Engineering and Management, 18(3), 427–458. <u>https://doi.org/10.3926/jiem.8537</u> 

Yang, Y., & Iqbal, M. Z. (2025). Cost-optimised machine learning model comparison for predictive maintenance. Electronics, 14(12), Article 2497. https://doi.org/10.3390/electronics14122497 

COMP8043041 – Machine Learning 

