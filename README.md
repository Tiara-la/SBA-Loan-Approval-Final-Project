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

