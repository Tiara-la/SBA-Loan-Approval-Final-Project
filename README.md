<h1 align="center">
  <br>
  <img height="300" src="https://i.ibb.co.com/m5hwhf2/HDC-Anca.png"> <br>
    Loan Risk Assesment - Heptad Data Colletor
<br>
</h1>

<p align="center">
<a href="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/fork" target="blank">
<img src="https://img.shields.io/github/forks/heptaddc/SBA-Loan-Approval-Final-Project?style=for-the-badge" alt="HDC forks"/>
</a>
<a href="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/stargazers" target="blank">
<img src="https://img.shields.io/github/stars/heptaddc/SBA-Loan-Approval-Final-Project?style=for-the-badge" alt="HDC stars"/>
</a>
<a href="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/pulls" target="blank">
<img src="https://img.shields.io/github/issues-pr/heptaddc/SBA-Loan-Approval-Final-Project?style=for-the-badge" alt="HDC pull-requests"/>
</a>
<a href='https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/releases'>
<img src='https://img.shields.io/github/release/heptaddc/SBA-Loan-Approval-Final-Project?&label=Latest&style=for-the-badge'>
</a>
<a href='https://jupyter.org/try'>
<img src='https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter'>
</a>
<a href='https://jupyter.org/try'>
<img src='https://img.shields.io/badge/Using-Python-blue?style=for-the-badge&logo=Python'>
</a>
</p>

The **Small Business Administration (SBA)** is a United States government agency established to support and promote small businesses and entrepreneurs. Created in 1953 through the Small Business Act, the SBA's mission is to maintain and strengthen the nation’s economy by enabling the establishment and viability of small businesses and by assisting in the economic recovery of communities after disasters.

![screen](https://i.ibb.co.com/nzxDKmR/sba-banner-1.webp)

## **Members of Heptad Data Collector**

1. Farah Fitria Sari
2. Aditya Fajri Melinianto
3. Apri Ansyah
4. Oktafina Pingkan Purwanto
5. Pancaran Ratna Mustika
6. Ryan Fajar
7. Tiara Lailatul Nikmah

## The Data Set (from Kaggle.com)

The original data set is from the U.S.SBA loan database, which includes historical data from 1987 through 2014 (899,164 observations) with 27 variables. The data set includes information on whether the loan was paid off in full or if the SMA had to charge off any amount and how much that amount was. The data set used is a subset of the original set. It contains loans about the Real Estate and Rental and Leasing industry in California. This file has 2,102 observations and 35 variables. The column Default is an integer of 1 or zero, and I had to change this column to a factor.

| Description                            | Link                                                                                                                                                                                                                                                                |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Load the dataset                       | <a href="https://www.kaggle.com/datasets/mirbektoktogaraev/should-this-loan-be-approved-or-denied/data" target="_parent">Should This Loan be Approved or Denied?</a>                               |
| Dataset guide by Journal of Statistics | <a href="https://www.kaggle.com/datasets/mirbektoktogaraev/should-this-loan-be-approved-or-denied?select=Should+This+Loan+be+Approved+or+Denied+A+Large+Dataset+with+Class+Assignment+Guidelines.pdf" target="_parent">Dataset with Class Assignment Guidelines</a> |
| License                                | <a href="https://creativecommons.org/licenses/by-sa/4.0/" target="_parent">CC BY-SA 4.0</a>                                                                                                                                                                         |

<br>

##  1. Business Understanding

### A. Latar Belakang
U.S. Small Business Administration (SBA) didirikan pada tahun 1953, dengan tujuan untuk mendukung usaha kecil di pasar kredit Amerika dalam mengurangi pengangguran dan menciptakan lapangan kerja. Salah satu cara SBA membantu usaha kecil adalah melalui program jaminan pinjaman untuk mendorong bank memberikan kredit kepada usaha kecil. Jika peminjam gagal bayar, maka SBA akan menanggung sebagian dari pinjaman. Meskipun SBA bertindak untuk mengurangi resiko bank dengan cara membayar sebagian jumlah kerugian bank sesuai dengan yang telah dijaminkan diawal, kejadian gagal bayar (loan default) menimbulkan pertanyaan tentang efektivitas inisiatif tersebut dan dampaknya terhadap stabilitas keuangan bank dan ekonomi.

### B. Problem Statement

SBA sebagai lembaga penjamin untuk bank bagi para UMKM ingin menurunkan loan default rate dari usaha-usaha yang mereka loloskan / jaminkan.

### C. Goal

Mengembangkan data driven decision making system yang robust, memanfaatkan data demografis perusahaan untuk menilai kelayakan pinjaman UMKM dengan akurat.

### D. Objectives
- Data preprocessing & cleansing
- Identifikasi potensi resiko dengan EDA, dengan visualisasi
- Membuat model machine learning
- Menentukan metrics evaluation yang tepat
- Monitoring & reporting (mentranslate hasil pemodelan dan evaluasi ke dalam ranah bisnis).

### E. Business Metrics

<img src="https://i.ibb.co.com/pXXGy6X/2024-05-16-18-23-14-Stage-0-PT-Heptad-Data-Collector-Kelompok-4-DS-Batch-43-pptx-Google-Slide.png">

##  2. Data Preprocessing - 1st Section

### A. Handling Missing Values

- Kolom ChargeOffDate, Missing Value 80% maka
kolom dihapus.
- Kolom: MIS_Status memiliki xx% NaN dan akan
dihapus terlebih dulu. Setelah itu, untuk kolom lain
yang memiliki NaN seperti kolom Name, City, State,
Bank, BankState, NewExist, RevLineCr, LowDoc,
DisbursementDate, Missing Value hanya dibawah
0,5%, maka hanya dihapus baris yang mengandung
NaN.

### B. Handle Duplicate Data

Tidak ditemukan adanya duplikasi data pada dataset ini, sehingga bisa melanjutkan proses preprocessing selanjutnya

### C. Feature Transformation

- Mengubah kolom object ke numerik (DisbursementGross, BalanceGross, GrAppv, SBA_Appv) diganti ke float
- Menghilangkan nilai 0 pada: NAICS (memasukan ke kategori 81), Term & NoEmp (diganti dengan nilai median), NewExist & UrbanRural (diganti dengan nilai modus)
- Menghilangkan nilai bukan Y atau N pada kolom LowDoc dan RevLineCr (diganti dengan nilai modus (N))
- Menghilangkan 3 karakter terakhir pada kolom NAICS
- Mengganti 0 dan 1 pada kolom FranchiseCode menjadi 'Not-Franchise' dan selain itu menjadi 'Franchise'
- Nilai 1976A pada kolom ApprovalFY diganti menjadi 1976
- NoEmp, CreateJob, RetainedJob dilakukan robust-scaler, untuk mempermudah dalam melakukan analisis statistik
- Untuk Bank dengan count < 1500 akan dimasukkan ke kategori ‘Others’

## 3. Feature Engineering

### A. Feature Selection
Feature yang dihapus:
- ApprovalDate
- DisbursementDate
- ChgOffDate 
- Zip
- City
- LoanNr_ChkDgt
- Name
- SBA_Appv
- GrAppv
- ChgOffPrinGr
- DisbursementGross
- BalanceGros
- ApprovalFY

Feature yang stay:
- Term
- NoEmp
- CreateJob
- RetainedJob
- NewExist
- UrbanRural
- NAICS
- FranchiseCode
- LowDoc
- RevLineCr
- MIS_Status
- Bank
- State
- BankState

### B. Feature Extraction

Feature yang ditambah:
- BankIsIn -> BankState = State, maka 1, jika tidak 0
- CompanyType -> Jika NewExist dan UrbanRural = 1, maka 1. Jika NewExist = 1 tapi UrbanRural = 2, maka 2. Jika NewExist = 2 tapi UrbanRural = 1, maka 3. Jika NewExist dan UrbanRural = 2, maka 4.
- Prod -> CreatedJob > RetainedJob maka 1, jika tidak 0
- Membuat kolom baru Recession = tahun terjadinya resesi di USA

## 4. Insight and Visualization

### A. Univariate Analysis - Categorical
<img width="857" alt="Stage 2 - Univ_NE_FC" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/3647248b-f549-476f-bd28-cc57b86f23b1">

##### NewExist
Jumlah bisnis yang menerima pinjaman dalam dataset didominasi oleh bisnis yang sudah existing (label 1) dibandingkan dengan bisnis baru (label 2). Bisnis existing umumnya memiliki laporan keuangan yang lebih stabil dan menguntungkan, serta menunjukkan kemampuan mereka untuk melunasi pinjaman dibandingkan dengan bisnis baru yang mungkin belum memiliki riwayat kredit (credit score) yang memadai, dan belum memiliki laporan keuangan yang stabil sehingga lebih sulit mendapat pinjaman.

##### FranchiseCode
Sebagian besar bisnis yang menerima pinjaman adalah bisnis independen atau bukan bagian dari franchise. Bisnis independen cenderung memiliki akses terbatas terhadap modal dibandingkan dengan bisnis franchise. Bisnis independen sering kali tidak memiliki dukungan finansial yang kuat karena dimiliki oleh individual dan jaringan terbatas, sehingga mereka lebih bergantung pada pinjaman eksternal untuk mendanai operasional dan ekspansi bisnis.

<img width="863" alt="Stage 2 - Univ_UR_RLC" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/4cc08569-2c03-4335-bbae-13afaf67b563">

##### UrbanRural
Data menunjukkan bahwa sebagian besar pinjaman diberikan kepada bisnis di daerah perkotaan. Ini mungkin disebabkan oleh beberapa faktor:
1. Konsentrasi bisnis yang lebih tinggi di daerah perkotaan, .
2. Akses yang lebih mudah ke layanan perbankan dan keuangan di daerah perkotaan.
3. Potensi pasar yang lebih besar di daerah perkotaan, karena mobilisasi penduduk yang tinggi dan populasi penduduk yang lebih padat.
Meskipun jumlahnya lebih sedikit, ada sejumlah signifikan pinjaman yang diberikan di daerah pedesaan. Ini menunjukkan bahwa ada kebutuhan akan dukungan finansial di daerah pedesaan, meskipun aksesnya mungkin lebih terbatas dibandingkan dengan daerah perkotaan.

##### RevLineCr
Data menunjukkan bahwa sebagian besar pinjaman diberikan tanpa revolving line of credit, karena banyak bisnis yang lebih memilih pinjaman yang memiliki jadwal pembayaran dengan nominal yang jelas/ tetap dan bunga yang pasti. Pinjaman dengan struktur ini memberikan kepastian bagi bisnis dalam perencanaan keuangan mereka, karena mereka tahu persis berapa yang harus dibayar setiap bulan dan kapan pinjaman tersebut akan lunas. Tidak seperti kartu kredit yang fleksibel dan dapat dibayar sebagian atau seluruh pinjaman sebelum jatuh tempo perbulan.

<img width="863" alt="Stage 2 - Univ_LD_BII" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/9ff67de2-d3a0-4814-addc-673719fc6e95">

##### LowDoc
Grafik menunjukkan bahwa sebagian besar pinjaman diberikan tanpa menggunakan program LowDoc. Namun, ada juga kebutuhan signifikan akan jenis pinjaman ini, meskipun dalam jumlah yang lebih kecil.

##### BankIsIn
Jumlah pinjaman, dimana bisnisnya berada pada state yang sama dengan Bank pemberi pinjamanannya terlihat tidak berbeda signifikan.

<img width="860" alt="Stage 2 - Univ_CT_P" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/4a18dca0-ef51-4936-8fb4-e8031606e916">

##### CompanyType
Jumlah bisnis yang sudah ada dan berada di perkotaan paling tinggi, diikuti oleh bisnis baru dan ada di perkotaan. Sisanya adalah bisnis yang ada di pedesaan, baik yang sudah ada maupun baru.

##### Prod
Sebagian besar data menunjukkan bahwa jumlah pekerjaan yang diciptakan (CreateJob) lebih besar daripada pekerjaan yang dipertahankan (RetainedJob), karena banyak bisnis yang sedang dalam fase ekspansi dan pertumbuhan. Ketika bisnis berkembang, mereka sering kali perlu menambah tenaga kerja baru untuk mendukung peningkatan produksi, layanan, atau operasional lainnya. Hal ini menyebabkan penciptaan lapangan kerja baru yang signifikan. Sebaliknya, pekerjaan yang dipertahankan biasanya mencerminkan upaya untuk menjaga stabilitas operasional yang sudah ada, dan tidak selalu menunjukkan penambahan tenaga kerja baru. Oleh karena itu, dalam periode pertumbuhan ekonomi atau bisnis yang aktif mengembangkan diri, penciptaan lapangan kerja baru cenderung lebih tinggi dibandingkan dengan upaya mempertahankan pekerjaan yang sudah ada.

<img width="559" alt="Stage 2 - Univ_R_T_MS" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/0e4b13f3-8aa8-41a8-b0f9-0dac882f5736">

##### Recession
Pada fitur ini lebih banyak pinjaman terdapat pada tahun-tahun tidak resesi dibanding tahun-tahun resesi.

##### Term
Term dikelompokkan menjadi 4 bagian (0-60 bulan, 60-120 bulan, 120-Upper IQR, dan > Upper IQR)

##### MIS_Status
Term dikelompokkan menjadi 4 bagian (0-60 bulan, 60-120 bulan, 120-Upper IQR, dan > Upper IQR). Terlihat bahwa banyak pinjaman pada term antara 5 sampai 10 tahun.

<img width="371" alt="Stage 2 - Univ_Bank" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/557dda74-21e0-41a3-9f2c-1bb87a2a69f8">

##### Bank
Kategori di kolom ini yang paling banyak kuantitasnya adalah Others. Ini karena bank yang hanya muncul < 1500 dimasukkan ke dalam kategori ini dan bank dengan karakteristik seperti ini ternyata banyak. Bank yang paling dipakai untuk meminjam ke SBA adalah Bank of America, Wells Fargo, JP Morgan, US Bank National of Association, dan Citizens Bank National Association.

<img width="370" alt="Stage 2 - Univ_State" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/9a2a14f7-0484-4220-a6f2-86105b43a525">

##### State
Dari total 50 state di USA, peminjam paling banyak ada pada state California, Texas, New York, Florida, dan Philadelphia. Untuk fokus implementasi program improvement kepada customer, SBA bisa fokus kepada customer di 5 state ini.

<img width="370" alt="Stage 2 - Univ_BS" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/d6f6c401-ae6e-4f2c-88c6-9b8b1fa13148">

##### BankState
Dari total 50 state di USA, bank peminjam paling banyak ada pada state California, North Carolina, Illinois, Ohio, dan Rhode Island. Untuk fokus implementasi program improvement kepada bank, SBA bisa fokus kepada bank ke 5 state ini.

<img width="368" alt="Stage 2 - Univ_Industri" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/7f6ef65f-1628-473f-ba5f-22b97fef019e">

##### Industri
Frekuensi distribusi industri tertinggi di bidang Other Services karena banyak yang nilai awalnya 0 dimasukkan ke kategori ini. Nilai awal 0 menandakan perusahaan tidak diberikan label NAICS, yaitu tipikal pinjaman sebelum NAICS berdiri tahun 1997. Setelah itu, 3 sektor teratas adalah Retail, Manufacturing dan Accomodation & Food Services, mencerminkan pentingnya ketiga industri ini dalam perekonomian. Selanjutnya, sektor construction, healthcare dan social assistance juga menunjukan aktivitas yang signifikan dalam memperoleh pinjaman. Sektor lainnya: Wholesale Trade, Administrative Support, Transportation & Warehousing, dan sektor lainnya menunjukkan aktivitas yang lebih rendah tetapi tetap signifikan.

### B. Univariate Analysis - Numerical

<img width="445" alt="Stage 2 - Univ_NE_CJ_RJ" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/439c0c3f-e596-413c-b079-8edcb679e692">

##### NoEmp
Setelah ditransform dengan robust scaler karena distribusi awal kolom ini positive skew dan di-handle outlier dengan metode Z-score, kolom ini masih memiliki distribusi yang kurang lebih positive skew. Hanya saja ada perubahan limit maksimumnya yang menjadi hanya 29. 

##### CreateJob
Setelah ditransform dengan robust scaler karena distribusi awal kolom ini positive skew dan di-handle outlier dengan metode Z-score, kolom ini masih memiliki distribusi yang kurang lebih positive skew. Hanya saja ada perubahan limit maksimumnya yang menjadi hanya 600.

##### RetainedJob
Setelah ditransform dengan robust scaler karena distribusi awal kolom ini positive skew dan di-handle outlier dengan metode Z-score, kolom ini masih memiliki distribusi yang kurang lebih positive skew. Hanya saja ada perubahan limit maksimumnya yang menjadi hanya 150.

### C. Multivariate Analysis - Categorical

<img width="604" alt="Stage 2 - Multi_NE_FC" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/b7f465a5-d46c-4259-b0ee-ec3daebfa62d">
<img width="288" alt="Stage 2 - Multi_UR" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/426b17cc-abc1-47d4-bbfd-8df3d181a946"><img width="286" alt="Stage 2 - Multi_CT" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/303dbaea-2b66-4c6f-a95a-40f25d12819e">
<img width="288" alt="Stage 2 - Multi_P" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/590454dd-60d5-4317-8f9c-9643a40064b0">


##### NewExist, FranchiseCode, UrbanRural, CompanyType, Prod
Tidak ada perbedaan rasio antara peminjam gagal bayar dengan tidak gagal bayar pada kolom NewExist, FranchiseCode, UrbanRural, CompanyType, dan Prod. Dari bar chart terlihat bahwa fitur-fitur ini tidak terlalu signifikan perbedaannya terhadap fitur target MIS_Status, namun masih harus dicek ulang dengan chi-square test apakah secara statistik observasi ini valid.

<img width="289" alt="Stage 2 - Multi_RLC" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/df187d10-af8d-4572-bf19-74e27f0d8e12"> <img width="286" alt="Stage 2 - Multi_BII" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/9fbd1783-856f-485f-a348-0f8a001b5aea">
<img width="607" alt="Stage 2 - Multi_R_T" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/69de4501-2359-47da-bc9d-3e26228cffc0">

##### RevLineCr, BankIsIn, Recession, Term
Pada bar chart terlihat perbedaan rasio antara peminjam gagal bayar dengan tidak gagal bayar pada kolom RevLineCr, LowDoc, BankIsIn, Recession, dan Term. Dari bar chart terlihat bahwa fitur-fitur ini lumayan signifikan perbedaannya terhadap fitur target MIS_Status, namun masih harus dicek ulang dengan chi-square test apakah secara statistik observasi ini valid.

#### Chi-Square Test

<img width="305" alt="Stage 2 - Multi_Chi_Sqr" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/678f324e-71aa-4ff5-9228-0108f7c34ba3">

Karena p-value semua fitur terhadap fitur MIS_Status adalah 0 (kurang dari nilai alpha = 0.05), maka bisa dibilang semua fitur kategorikal yang kami pilih memiliki pengaruh statistik yang signifikan terhadap fitur target MIS_Status

### D. Multivariate Analysis - Numerical

##### Heatmap

<img width="423" alt="Stage 2 - Multi_HM" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/e720fe46-6bf8-4a5c-a35d-59e3c3cdb672">

Pada matriks korelasi dapat dilihat bahwa urutan korelasi absolut paling besar dari 13 kolom lain yang bisa dikorelasi jika diurutkan adalah:
Recession (0.21)
BankIsIn (0.20)
NAICS (0.11)
RevLineCr (0.11)
LowDoc (0.08)
ind_code (0.08)
NoEmp (0.03)
FranchiseCode (0.02)
NewExist (0.02)
CreateJob (0.01)
RetainedJob (0.01)
UrbanRural (0.01)
Prod (0.01)
Dengan ini dapat dilihat bahwa 5 faktor teratas yang sangat berkaitan dengan MIS_Status sebelum dilakukan handle outlier dan class imbalance adalah: Recession, BankIsIn, NAICS, RevLineCr, dan LowDoc. Urutan list ini akan berubah jika dilakukan handle outlier dan class imbalance. Pada beberapa kolom numerikal yang akan selanjutnya dilakukan handle outlier seperti NoEmp, CreateJob, dan RetainedJob, akan dilakukan t-test untuk melihat lebih dalam lagi signifikansi perbedaan rata-rata tiap kolom terhadap fitur target MIS_Status. Untuk beberapa kolom yang juga merupakan kategorikal seperti Recession, BankIsIn, NAICS, RevLineCr, LowDoc, FranchiseCode, NewExist, UrbanRural, perbedaan statistik juga sudah sebelumnya dilihat berdasarkan chi-square test.

##### Boxplot

<img width="665" alt="Stage 2 - Multi_BP" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/0fddb95a-21d1-4098-88ad-1f4475990d71">

Pada boxplot di atas dapat dilihat bahwa rata-rata semua distribusi PIF dan CHGOFF pada kolom numerikal NoEmp, CreateJob, dan RetainedJob memiliki skewness yang positif, yakni banyak frekuensi pada jumlah rendah. Outliers pada PIF terlihat lebih banyak dibandingkan outliers pada CHGOFF. Untuk melihat apakah perbedaan distribusi MIS_Status pada ketiga fitur ini signifikan, akan dilakukan uji statistik t-test.

#### T-Test

<img width="255" alt="Stage 2 - Multi_TT" src="https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/79759839/95459758-2376-4c4b-8425-3a839a483cb3">

P-value pada t-test antara fitur MIS_Status dengan fitur-fitur numerik menandakan adanya perbedaan signifikan. Ini berarti rata-rata jumlah karyawan NoEmp, jumlah terbentuknya pekerjaan baru CreateJob, dan jumlah pekerjaan tetap RetainedJob memiliki perbedaan signifikan antara kategori yang kreditnya dibayar lunas P I F dengan kredit yang tidak dibayar lunas CHGOFF. Maka dari itu ke depannya SBA bisa melihat ke fitur-fitur ini untuk membedakan klien yang baik untuk diberikan pinjaman atau tidak.


## 5. Pre-Processing - 2nd Section

### D. Feature Encoding

- Pengkategorian Term, dibuat kolom baru RealEstate dengan nilai >= 240 =1, dibawah 240=0
- NAICS diubah menjadi nama-nama industri setiap kategori -> dilabelin jadi angka numerik
- MIS_status dilabelin chargeoff = 1, PIF=0
- Encoding 60 bank dengan count terbanyak

### E. Handle Outlier

Pada kolom numerikal outliers di-handle dengan cara sebagai berikut:
- Fitur yang sudah di-robust scaler akan menggunakan metode Z Score
- Term menggunakan metode IQR

### F. Class Imbalance

Class Imbalance pada MIS_Status di-handle dengan oversampling dengan menggunakan metode SMOTE. Setelah itu dilakukan pengecekan terhadap duplikat dan missing values

## 6. Modeling

### A. Melakukan Oversampling pada Training Set

Sebelumnya kami telah melakukan percobaan tanpa oversampling namun hasilnya kurang memuaskan jika dibandingkan dengan yang sudah dilakukan oversampling.
1. Pertama-tama kita perlu untuk memisahkan antara feature dan target terlebih dahulu
2. Setelah itu, kita akan melakukan oversampling untuk menyeimbangkan target MIS_Status menggunakan metode SMOTE supaya tidak terjadi bias.
3. Pada kasus kali ini kita akan membagi dataset menjadi training sebanyak 80 persen dan testing sebanyak 20 persen

Berikut ini merupakan hasil akhir setelah dilakukan oversampling:<br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/60963438-0b05-44ca-840d-4c74ef1e0638)


### B. Melakukan Transformasi Training Set dengan menggunakan Robust Scaler

Setelah data dilakukan splitting dan resampling selanjutnya kita akan mentransformasi dengan menggunakan robust scaler.
1. Perlu diingat bahwa kita hanya akan melakukan fit hanya pada dataset train saja, kita tidak perlu untuk melakukannya pada data test, Hal ini dilakukan untuk mencegah terjadinya data leakage.
2. Setelah melakukan fit pada data train, kita akan mentransform data test agar bentuknya sama seperti train data. Hal ini dilakukan supaya mesin jadi lebih mudah untuk mengenali pola dari transformasi robust scaler yang telah kita lakukan. <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/650e954b-e1e6-4102-ac4a-df1a399deae0)


### C. Melakukan Modeling menggunakan Algoritma Logistic Regression

1. Menginisialisasi variabel logistic regression dan melakukan fit terhadap training data <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/de05f658-cc15-41e3-a795-fb048b0019af)
3. Mengujinya menggunakan metrics akurasi dan recall <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/80199837-0613-47a2-8db4-d6d291c31974)

Kesimpulan / Hasil Evaluasi : 
Berdasarkan hasil evaluasi tersebut kami menggunakan recall sebagai metrics utama, sedangkan metrics yang lain hanya sebagai pembanding. Terutama untuk akurasi hanya kami gunakan untuk melakukan pengecekan apakah model cenderung overfit atau tidak. Setelah mendapatkan hasil tersebut kami mengetahui bahwa jarak antara akurasi training dan test tidak terlalu jauh sehingga kecil kemungkinan untuk terjadi overfit.

### D. Hyperparameter Tuning Logistic Regression

1. Hyperparameter Tuning pada model Logistic Regression <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/d6cbc2ba-8c71-40e9-bba3-50bcf8e666c9)
2. Menetapkan Parameter terbaik pada model Logistic Regression <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/a5f1a171-6d37-452e-92af-52048b42b21b)

Kesimpulan / Hasil Evaluasi : 
Setelah melakukan hyperparameter tuning, terdapat penurunan spesifik pada recall, maka kami memutuskan untuk menggunakan model awal (parameter default) karena memiliki nilai recall yang tinggi.

### E. Melakukan Modeling menggunakan Algoritma Decision Tree

Selanjutnya kami akan mencoba melakukan pemodelan menggunakan DecisionTree, karena algoritma ini cukup umum dan populer digunakan pada bidang masalah klasifikasi.

1. Menginisialisasi variabel Decision Tree dan melakukan fit terhadap training data <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/53109bad-6a2f-432f-94e1-b3531c66749f)
2. Mengujinya menggunakan metrics akurasi dan recall <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/da9f62e5-7507-4a0f-96b6-b33c089f20b3)

Kesimpulan / Hasil Evaluasi : 
Model tersebut memiliki kecenderungan yang besar untuk overfit sehingga kami memutuskan untuk tidak menggunakan model Decision Tree tersebut. Hal ini dikarenakan algoritma Decision tree memiliki sifat untuk melakukan partitioning ruang fitur secara rekursif sehingga lebih mudah untuk overfit.

### F. Melakukan Modeling menggunakan Algoritma Random Forest

Terakhir, kami akan mencoba untuk menggunakan algoritma Random Forest, karena model ini dikenal sebagai model yang sangat fleksibel dan memiliki performa yang bagus khususnya pada studi kasus klasifikasi seperti yang sedang kami lakukan.

1. Menginisialisasi variabel Random Forest dan melakukan fit terhadap training data. <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/19b6dd63-2368-47ff-a61a-5c81eeae9316)
2. Mengujinya menggunakan metrics akurasi dan recall. <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/cdeb4f6f-2d3c-401e-a943-b0566d71623b)

Kesimpulan / Hasil Evaluasi : 
Model tersebut memiliki kecenderungan yang besar untuk overfit sehingga kami akan melakukan treatment dengan memasukkan parameter tambahan seperti kedalaman tree, dan min sample split untuk melihat hasil apakah model masih mengalami overfit atau tidak.

### G. Hyperparameter Tuning Random Forest 

1. Mengatasi overfit RandomForest tersebut dengan memasukkan parameter tertentu untuk mengatur agar model bisa memberikan performa yang lebih baik. <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/fd35442e-1a26-4aea-b672-5986e483704f)
3. Setelah sebelumnya model random forest terjadi overfit, kali ini kami akan memasukkan max depth = 6, dan min sample split = 100 untuk menurunkan kecenderungan overfitting. <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/612a523e-5093-4ab4-9296-dfecd19b2c23)

Kesimpulan / Hasil Evaluasi : Setelah dilakukan treatment, model terbaru menghasilkan akurasi yang tak jauh berbeda antara training dengan testing. yang mana kecenderungan untuk overfitting sangat kecil untuk terjadi. akan tetapi model ini memiliki nilai recall yang rendah, sehingga besar kemungkinan akan dipilih model yang memiliki jumlah recall lebih besar.

### H. Komparasi Antar Model

1. Model terbaik jatuh kepada Logistic Regression, karena memiliki nilai recall tertinggi dibandingkan dengan yang lain, dan yang paling penting tidak terjadi overfit pada model tersebut.
2. Model kedua terbaik jatuh kepada Random Forest, karena memiliki nilai recall kedua dibandingkan dengan Decision Tree, meskipun model ini memiliki nilai akurasi yang tinggi jika dibandingkan dengan Logistic Regression kami tetap memilih Logistic Regression karena memiliki nilai recall yang jauh lebih tinggi.
3. Model Decision Tree menempati peringkat terakhir, karena memiliki kecenderungan overfit yang tinggi berdasarkan sifat model itu sendiri. <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/f21bf3a1-fb5c-41f3-9658-b5c49e0b8bce)

### I. Meningkatkan Nilai Recall Model Logistic Regression

1. Jika kita ingin meningkatkan lebih jauh lagi recall score, kita bisa menetapkan thresholds dengan nilai tertentu untuk menaikannya. Dengan menurunkan thresholds, maka akan menaikkan Recall dan menurunkan Precision. Jika stakeholder ingin lebih selektif lagi dalam menangani kerugian chargeoff hal ini bisa diterapkan. <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/1b723340-447d-402b-9158-91077f1036b2)

2. Langkah selanjutnya, jika sudah diketahui nilai thresholds. Kita bisa melakukan prediksi menggunakan nilai tersebut untuk menaikkan recall. target recall untuk saat ini adalah 85%, yang artinya kita akan menurunkan thresholds mencapai angka 0.3. <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/7715f3e6-ac88-4f7b-8ac5-4bd7e7fd47fc) <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/ea79ee3a-ccdd-4e59-91df-4a65b7bc48ce)

Kesimpulan / Hasil Evaluasi : Kita telah berhasil menaikkan recall hingga sebanyak 85%, hal ini juga terdapat trade-off atau pertukaran yang harus dibayar, yaitu jika kita mengecilkan nilai threshold untuk menaikkan recall, maka nilai precision juga akan turun. Yang mana precision tersebut akan berhubungan dengan orang-orang yang sebenarnya bisa bayar, namun diprediksi tidak bisa bayar. Kita akan sedikit kehilangan potensi untuk meminjamkan uang kepada mereka.

## 7. Feature Importances

1. Fitur "Term": Fitur ini memiliki tingkat kepentingan tertinggi, menunjukkan bahwa durasi (term) dari suatu pinjaman adalah faktor yang paling signifikan dalam model ini. Ini mungkin berarti bahwa lamanya waktu pinjaman atau proyek sangat mempengaruhi hasil yang diprediksi oleh model.
2. Fitur "Recesion": Adanya resesi merupakan fitur terpenting kedua. Hal ini menunjukkan bahwa kemerosotan ekonomi mempunyai dampak besar terhadap hasil prediksi.
3. Fitur "BankISln": Merupakan fitur yang menandakan peminjam dan bank berada pada suatu wilayah atau state yang sama
4. Fitur "Lowdoc dan RevLineCr": Menunjukkan bahwa persyaratan dokumentasi atau adanya proses dokumentasi minim (LowDoc) memainkan peran penting dalam model.
5.Fitur lain: Fitur-fitur seperti "UrbanRural", "FranchiseCode", "BankState", "State", "Bank", dan lainnya memiliki tingkat kepentingan yang lebih rendah tetapi masih memberikan kontribusi terhadap model. <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/1b5db7a7-6dba-4ada-8fa0-ec6b524f58a7)

## 8. Insight dan Business Recommendation <br>
![image](https://github.com/heptaddc/SBA-Loan-Approval-Final-Project/assets/170295485/12e9b939-3db4-43a8-a36d-1d511a34919f)

Dapat dilihat dengan model yang telah dibuat:

- TP(87714) = Model sukses memprediksi positif (ChgOff) dan kenyataanya benar ChgOff
- TN(26575) = Model sukses memprediksi negatif (Tidak ChgOff) dan kenyataannya benar tidak ChgOff
- FP(58297) = Model memprediksi positif (ChgOff) tapi kenyataannya tidak ChgOff
- FN(4662) = Model memprediksi negatif (Tidak ChgOff) tapi kenyataannya ChgOff

### A. Kesimpulan Bisnis pada Confusion Matrix

- Mengacu pada business metrics kami pada awal project yaitu tentang Loan Default Rate, Sebelum dilakukan modeling kita memeiliki persentase gagal bayar sebanyak 17,61% yang mana sangat tinggi, Hampir mencapai 18%.
- Setelah dilakukannya modeling, terjadi penurunan yang cukup masif pada persentase chargeoff, yaitu sekitar 2.63%. Penurunan ini sangatlah besar sehingga besar kemungkinan untuk menurunkan kerugian meminjamkan uang kepada orang yang tidak bisa membayar.
- Kerugian sebelum menggunakan model adalah sebanyak 185.000.000 USD, namun setelah menggunakan model hanya terdapat 2.63% prediksi saja yang salah. yang mana angka ini akan menjadi 27.650.000 USD.
- Kerugian ini turun sebanyak 157.350.000 USD, yang mana turun 85% dari total kerugian.
- Berdasarkan penjabaran diatas, kami telah berhasil untuk memenuhi objektif awal dari business metrics, yaitu untuk mengurangi nilai kerugian awal dan mengurangi persentase peminjam yang default.
- Angka 185.000.000 USD diperoleh dari penjumlahan kolom ChgOffPrinGr pada dataset.

### B. Rekomendasi Bisnis Akhir

Jadi, dari semua uraian diatas kami menemukan kesimpulan berupa rekomendasi bisnis sebagai berikut:

- Mengembangkan Layanan Pinjaman Jangka Panjang. Dengan cara, Bank dapat menawarkan produk pinjaman dengan durasi yang lebih lama dengan suku bunga yang bersaing. karena rata-rata charge off terjadi pada peminjaman dengan jangka waktu yang pendek yaitu 0 sampai 60.
- Menyeleksi lebih ketat untuk industri yang memiliki persentasi gagal bayar yang tinggi seperti industri Real estate dan Finance Insurance, hal ini bisa diterapkan dengan tidak menetapkan sistem lowdoc khusus pada 2 industri tersebut.
- Fokus pemberian jaminan pinjaman pada sektor Pertambangan dan Perminyakan karena persentase gagal bayar rendah. Dapat diberikan jalur khusus pada sektor tersebut untuk mendorong jumlah pengajuan jaminan pinjaman.
- Penting bagi para pemberi pinjaman untuk lebih berhati-hati dalam mengambil keputusan untuk meminjamkan uang jika sedang terjadi krisis ekonomi pada daerah / tempat yang bersangkutan.
- Melihat korelasi BankIsIn yang tinggi, SBA bisa mencoba mengalokasikan pinjaman ke klien dari bank dengan state yang sama dengan klien.
