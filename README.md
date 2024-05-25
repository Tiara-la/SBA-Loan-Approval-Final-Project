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

##  2. Data Preprocessing

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
### NewExist, FranchiseCode, UrbanRural, RevLineCr

![screen](https://gcdnb.pbrd.co/images/OGhNaZk8ACXz.png?o=1)

- NewExist: Jumlah bisnis yang menerima pinjaman dalam dataset didominasi oleh bisnis yang sudah existing (label 1) dibandingkan dengan bisnis baru (label 2). Kemungkinan penjelasan untuk hal ini adalah: bisnis yang sudah ada memiliki rekam jejak yang lebih panjang dan stabil, sehingga lebih mudah untuk mendapatkan pinjaman.

- FranchiseCode: Sebagian besar bisnis yang menerima pinjaman adalah bisnis independen atau bukan bagian dari franchise. Ini bisa mencerminkan kenyataan bahwa bisnis independen mungkin lebih membutuhkan dukungan finansial dibandingkan dengan bisnis yang merupakan bagian dari sistem franchise

- UrbanRural: Data menunjukkan bahwa sebagian besar pinjaman diberikan kepada bisnis di daerah perkotaan. Ini mungkin disebabkan oleh beberapa faktor: Konsentrasi bisnis yang lebih tinggi di daerah perkotaan, Akses yang lebih mudah ke layanan perbankan dan keuangan di daerah perkotaan, Potensi pasar yang lebih besar di daerah perkotaan. Meskipun jumlahnya lebih sedikit, ada sejumlah signifikan pinjaman yang diberikan di daerah pedesaan. Ini menunjukkan bahwa ada kebutuhan akan dukungan finansial di daerah pedesaan, meskipun aksesnya mungkin lebih terbatas dibandingkan dengan daerah perkotaan.

- RevLineCr: Data menunjukkan bahwa sebagian besar pinjaman diberikan tanpa revolving line of credit. Ini mungkin disebabkan oleh beberapa faktor: Bisnis mungkin lebih memilih pinjaman konvensional dengan struktur pembayaran tetap daripada revolving line of credit yang lebih fleksibel namun mungkin lebih kompleks. Kebijakan pemberian pinjaman dari lembaga keuangan yang mungkin lebih ketat untuk revolving line of credit. <br>

### RealEstate, BankIsIn, CompanyType, Prod

![screen](https://gcdnb.pbrd.co/images/stzZlwuRwtlS.png?o=1)

- RealEstate: Setelah kolom Term dilakukan handle outlier dengan metode IQR, nilai Term pada dataset ada di bawah 240. 

- BankIsIn: Jumlah pinjaman, dimana bisnisnya berada pada state yang sama dengan Bank pemberi pinjamnannya terlihat tidak berbeda signifikan.

- CompanyType: Jumlah bisnis yang sudah ada dan berada di perkotaan paling tinggi, diikuti oleh bisnis baru dan ada di perkotaan. Sisanya adalah bisnis yang ada di pedesaan, baik yang sudah ada maupun baru.

- Prod: Sebagian besar data menunjukkan bahwa jumlah pekerjaan yang diciptakan (CreateJob) lebih besar daripada pekerjaan yang dipertahankan (RetainedJob). Ini bisa mengindikasikan bahwa banyak bisnis yang menerima pinjaman berhasil menciptakan lebih banyak lapangan pekerjaan baru daripada mempertahankan pekerjaan yang ada.

### Industri, Bank

![screen](https://gcdnb.pbrd.co/images/jNqNVG67xLMJ.png?o=1)

- Industri: Frekuensi distribusi industri tertinggi di bidang Other Services karena banyak yang nilai awalnya 0 dimasukkan ke kategori ini. Nilai awal 0 menandakan perusahaan tidak diberikan label NAICS, yaitu tipikal pinjaman sebelum NAICS berdiri tahun 1997. Setelah itu, 3 sektor teratas adalah Retail, Manufacturing dan Accomodation & Food Services, mencerminkan pentingnya ketiga industri ini dalam perekonomian. Selanjutnya, sektor construction, healthcare dan social assistance juga menunjukan aktivitas yang signifikan dalam memperoleh pinjaman. Sektor lainnya: Wholesale Trade, Administrative Support, Transportation & Warehousing, dan sektor lainnya menunjukkan aktivitas yang lebih rendah tetapi tetap signifikan.

- Bank: Kategori di kolom ini yang paling banyak kuantitasnya adalah Others. Ini karena bank yang hanya muncul < 1500 dimasukkan ke dalam kategori ini dan bank dengan karakteristik seperti ini ternyata banyak. Bank yang paling dipakai untuk meminjam ke SBA adalah Bank of America, Wells Fargo, JP Morgan, US Bank National of Association, dan Citizens Bank National Association.

### State, BankState, MIS_Status

![screen](https://gcdnb.pbrd.co/images/pegAF8IVnnPO.png?o=1)

- State: Dari total 50 state di USA, peminjam paling banyak ada pada state California, Texas, New York, Florida, dan Philadelphia. Untuk fokus implementasi program improvement kepada customer, SBA bisa fokus kepada customer di 5 state ini.

- BankState: Dari total 50 state di USA, bank peminjam paling banyak ada pada state California, North Carolina, Illinois, Ohio, dan Rhode Island. Untuk fokus implementasi program improvement kepada bank, SBA bisa fokus kepada bank ke 5 state ini.

- MIS_Status: Setelah dilakukan class imbalance, persentase rasio CHGOFF dan PIF tidak berubah, yakni masing-masing masih sekitar 18% dan 72% dari total dataset.

### Barchart with Hue - Low Correlation

![screen](https://gcdnb.pbrd.co/images/oFB5wHcHPHyO.png?o=1)

Tidak ada perbedaan rasio antara peminjam gagal bayar dengan tidak gagal bayar pada kolom NewExist, FranchiseCode, UrbanRural, CompanyType, Industri, dan RealEstate. Hal ini sejalan dengan korelasi kolom ini yang rendah terhadap kolom MIS_Status. SBA tidak disarankan melihat ke fitur-fitur ini untuk mengecek MIS_Status.

### Barchart with Hue - Intermediate Correlation

![screen](https://i.postimg.cc/9M16r2r4/2024-05-25-20-40-58-Half-Stage-1-PT-Heptad-Data-Collector-Kelompok-4-DS-Batch-43-pptx-Google.png)

Ada perbedaan rasio yang cukup signifikan antara peminjam gagal bayar dengan tidak gagal bayar pada kolom BandIsIn, Recession, dan Prod. Hal ini sejalan dengan korelasi kolom ini yang tinggi terhadap kolom MIS_Status. Begitu juga pada kolom kategorikal LowDoc dan RevLineCr. Maka dari itu SBA bisa melihat ke kriteria-kriteria di mana CHGOFF rendah pada kolom-kolom ini: peminjam melakukan LowDoc yang berarti memiliki kredit skor yang bagus dan income stabil, peminjam memakai bank yang sama dengan state dia berada, peminjam membuka job lebih banyak, tidak memiliki kredit bergulir dan tahun tersebut USA tidak mengalami resesi. 

### Barchart with Hue - Intermediate Correlation

![screen](https://i.postimg.cc/ZR0GBg3V/2024-05-25-20-43-38-Half-Stage-1-PT-Heptad-Data-Collector-Kelompok-4-DS-Batch-43-pptx-Google.png)

Seperti yang sudah diperlihatkan di heatmap, korelasi bank terhadap MIS_Status termasuk yang paling besar. Ada beberapa bank yang bahkan tidak memiliki kadar kredit gagal bayar seperti pada bank SBA - EDF Enforcement Action, Florida Business Development Action, dan CDC Small Business Finance Corporation. Disarankan untuk SBA agar jika ingin menyalurkan pinjaman dengan risiko gagal bayar rendah bisa ke bank bebas CHGOFF atau rendah CHGOFF. 

### B. Univariate Analysis - Numerical
### Term, NoEmp, CreateJob, RetainedJob

![screen](https://gcdnb.pbrd.co/images/xPCRHKvVNYCT.png?o=1)

- Term: Setelah di-handle outlier dengan metode IQR, limit atas Term berubah menjadi kurang dari 240. Ini tercermin di kolom RealEstate yang menandakan bahwa tidak ada Term di atas 240. Untuk distribusi dari Term sendiri bisa dilihat menyerupai distribusi normal.

- NoEmp: Setelah ditransform dengan robust scaler karena distribusi awal kolom ini positive skew dan di-handle outlier dengan metode Z-score, kolom ini masih memiliki distribusi yang kurang lebih positive skew. Hanya saja ada perubahan limit maksimumnya yang menjadi hanya 29. Perusahaan peminjam memiliki karyawan yang

- CreateJob: Setelah ditransform dengan robust scaler karena distribusi awal kolom ini positive skew dan di-handle outlier dengan metode Z-score, kolom ini masih memiliki distribusi yang kurang lebih positive skew. Hanya saja ada perubahan limit maksimumnya yang menjadi hanya 600.

- RetainedJob: Setelah ditransform dengan robust scaler karena distribusi awal kolom ini positive skew dan di-handle outlier dengan metode Z-score, kolom ini masih memiliki distribusi yang kurang lebih positive skew. Hanya saja ada perubahan limit maksimumnya yang menjadi hanya 150.

### Heatmap

![screen](https://gcdnb.pbrd.co/images/mxG2OwULoStH.png?o=1)

Pada matriks korelasi dapat dilihat bahwa urutan korelasi absolut paling besar dari 14 kolom lain yang bisa dikorelasi (1 kolom, RealEstate tidak bisa dikorelasi) jika diurutkan adalah:

- Term (0.35)
- Recession (0.21)
- BankIsin (0.19)
- Bank (0.13)
- Prod (0.11)
- NAICS (0.10)
- NoEmp (0.07)
- Ind_code (0.07)
- CreateJob (0.02)
- RetainedJob (0.02)
- Industri (0.01)
- NewExist (0)
- UrbanRural (0)
- CompanyType (0)

Dengan ini dapat dilihat bahwa 5 faktor teratas yang sangat berkaitan dengan MIS_Status adalah jangka waktu kredit, tahun resesi, apakah letak bank sama dengan letak peminjam, bank dari peminjam, dan apakah pembukaan pekerjaan lebih tinggi dibanding pekerjaan yang di-retain.

### Pairplot

![screen](https://gcdnb.pbrd.co/images/WoakBiD5OFqP.png?o=1)

Pada pairplot untuk kolom numerikal, dapat dilihat bahwa rata-rata korelasi antara kolom numerikal tidak terlalu terlihat signifikan. Scatterplot terlihat random berserak. Untuk distribusi kategori MIS_Status pada kolom Term bisa terlihat bahwa rata-rata pinjaman gagal bayar ada di distribusi rendah, begitu pula dengan NoEmp, CreateJob, dan RetainedJob. SBA bisa mengacu pada grafik ini bahwa untuk menghindari pinjaman dengan risiko tinggi. SBA harus menghindari term yang rendah, peminjam dengan karyawan dan pekerjaan yang sedikit, serta peminjam yang sedikit membuka lapangan pekerjaan baru.
