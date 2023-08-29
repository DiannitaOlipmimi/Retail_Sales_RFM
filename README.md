# Retail_Sales_RFM

# K-Means Clustering on Mall Customer

**Clustering**

Analisis cluster merupakan salah satu analisis multivariat yang termasuk dalam metode interdependensi, yaitu variabel bebas 𝑥 atau faktor penyebab tidak dibedakan dengan variabel terikat 𝑦 atau respon. Analisis cluster adalah suatu metode statistik yang mengidentifikasi kelompok sampel berdasarkan karakteristik serupa. Analisis cluster mengelompokkan elemen mirip sebagai objek penelitian yang mempunyai tingkat homogenitas yang tinggi antar objek menjadi cluster yang berbeda dengan tingkat heterogenitas objek yang tinggi antar cluster (Sigit, 2008). 

terdapat 2 jenis clustering yaitu,
1. clustering hierarki

    Analisis kelompok merupakan teknik peubah ganda yang mempunyai tujuan utama untuk mengelompokkan objek-objek berdasarkan kemiripan karakteristik yang dimilikinya. Karakteristik objek-objek dalam suatu kelompok memiliki tingkat kemiripan yang tinggi, sedangkan karakteristik antar objek pada suatu kelompok dengan kelompok lain memiliki tingkat kemiripan yang rendah.

2. clustering non hierarki
    Analisis kelompok non hirarki merupakan pengelompokan objek dengan jumlah kelompok yang telah ditentukan terlebih dahulu. Pada analisis non hirarki, data yang dapat digunakan lebih besar dari analisis hirarki. Namun, analisis ini memiliki kelemahan yaitu pada data outlier atau pencilan, ukuran jarak yang digunakan, dan kerelevannan suatu variabel.

**⛳Deskripsi Masalah:**

Terdapat Supermarket yang memiliki data kartu member. data ini mengandung beberapa informasi dasar pengunjung mall atau customer. manager mall ini ingin mengetahui customer yang dapat dijadikan target penjualan berdasarkan informasi dasar yang terapat dalam kartu member.

**⛳Tujuan:**

Untuk melihat konsumen yang dapat dijadikan target penjulanan maka dilakukan segmentasi dengan menggunakan algoritma K-Means pada customer mall.

## 📌Table of contents
- [Dataset dan Variabel](https://github.com/DiannitaOlipmimi/Clustering_on_Mall_Customer#data-dan-variabel)
- [Result](https://github.com/DiannitaOlipmimi/Clustering_on_Mall_Customer#result)
- [Links](https://github.com/DiannitaOlipmimi/Clustering_on_Mall_Customer#links)


## 🧵Data dan Variabel:

**📒Dataset:**

| CustomerID | Gender | Age | Annual Income (k$) | Spending Score (1-100) |
| ---------- | ------ | --- | ------------------ | ---------------------- |
| 1          | Male   | 19  | 15                 | 39                     |
| 2          | Male   | 21  | 15                 | 81                     |
| 3          | Female | 20  | 16                 | 6                      |
| 4          | Female | 23  | 16                 | 77                     |
| 5          | Female | 31  | 17                 | 40                     |

**📒Variabel:**
- `CustomerID`
- `Gender`
- `Age`
- `Annual Income (k$)`
- `Spending Score (1-100)`

## 🧵Result

✅ Data Preparation:
1. Memuat data kasus COVID-19
2. Melakukan pemilihan variabel yang digunakan
3. Melakukan Identifikasi awal menggunakan matriks korelasi
Handle missing values, if any, by imputing them or removing the corresponding records.

    ```R
    # pengecekan data
    dim(data)
    names(data)

    # missing value 
    sum(is.na(data)) # total keseluruhan NA bila ada
    colSums(is.na(data)) # total NA per kolom

    # Statistik Deskriptif 
    #install.packages("pastecs")
    library(pastecs)
    stat.desc(data)
    ```

✅ Exploratory Data Analysis (EDA):
1. Membuat scatter plot untuk melihat hubungan masing-masing variabel

    ![Alt text](Rplot1.png)

    berdasarkan plot yang terbentuk:
    - Age VS Annual Income memiliki hubungan yang lemah bahkan hampir tidak ada
    - Age VS Spending Score memiliki hubungan yang lemah negatif, dimana semakin besar `Age` atau usia maka semakin kecil `Spending Score` atau nilai pengeluarannya
    - Spending Csore VS Annual Income memiliki hubungn yang lemah

2. Membuat Bar plot untuk melihat lebih jauh mengenai variabel 

    ![Alt text](Rplot2.png)

    ![Alt text](Rplot3.png)

3. Melakukan Pengecekan Outlier
    
    ![Alt text](Rplot4.png)

4. Mengidentifikasi Outlier dan menghapusnya

5. Identifikasi lebih lanjut dengan Matrix Correlation

    ![Alt text](Rplot5.png)

✅Feature Scaling:
1. Menguji asumsi K-Means clustering (no multikolinieritas) dengan nilai VIF 

    ```R
    #uji asumsi multikolinieritas
    library(car)

    Gender=lm(index$Gender~index$Age+index$Annual.Income..k..+index$Spending.Score..1.100., new_data = index)
    age=lm(index$Age~index$Gender+index$Annual.Income..k..+index$Spending.Score..1.100., new_data = index)
    annual=lm(index$Annual.Income..k..~index$Spending.Score..1.100.+index$Age+index$Gender, new_data = index)
    spending=lm(index$Spending.Score..1.100.~index$Age+index$Gender+index$Annual.Income..k.., new_data = index)

    #membuat function untuk menghitung nilai VIF
    vif_value = function(model){
    #mengambil nilai r squared
    summary_value = summary(model)
    r_squared = summary_value$r.squared
    
    #menghitung VIF
    vif_val = 1/(1-r_squared)
    print(vif_val)
    }

    vif_value(Gender)
    vif_value(age)
    vif_value(annual)
    vif_value(spending)
    ```

2. Melakukan standarisasi data agar hasil clustering K-means menjadi lebih tepat

    ```R
    #standarisasi data
    data_standarisasi = scale(index)
    data_standarisasi_mat = as.matrix(data_standarisasi)
    #View(data_standarisasi_mat)
    #write.csv(data_standarisasi_mat, file = "standarisasi.csv")

    ```


✅K-Means Clustering:
1. Menggunakan *Elbow method* untuk menentukan berapa banyak k cluster yang paling optimal

    ![Alt text](Rplot6.png)

    ![Alt text](Rplot7.png) 

2. Memilah masing-masing cluster yang dihasilkan beserta anggotanya
3. Menghitung *centroid* masing-masing cluster yang telah dihasilkan untuk dianalsis lebih lanjut

    ![Alt text](Rplot8.png)


✅Evaluasi:
1. Menganalisis karakteristik atau kesamaan dari setiap cluster
2. Menghitung statistik deskriptif dari maisng-masing cluster untuk mendapatkan nilai-nilai seperti rata-rata
3. Memvisualisasikan cluster untuk memudahkan gambaran penempatan cluster berdasarkan *sum of square distances*
4. Interpretasi masing-masing cluster

    | Profil          | Gender | Age  | Annual.Income..k.. | Spending.Score..1.100. | cluster |
    | --------------- | ------ | ---- | ------------------ | ---------------------- | ------- |
    | kluster1 | 1      | 30   | 76                 | 81                     | 1       |
    | kluster2 | 1      | 45.5 | 24.5               | 16                     | 2       |
    | kluster3 | 1      | 51   | 54                 | 48                     | 3       |
    | kluster4 | 2      | 41.5 | 86.5               | 15                     | 4       |
    | kluster5 | 1      | 26   | 57.5               | 53                     | 5       |

    dari hasil diatas dapat diketahui:
    - customer mall dapat dibedakan menjadi 5 kategori dengan tingkatan pada setiap variabelnya, sangat tinggi, tinggi, sedang, rendah, sangat rendah.
    - kluster 1 merupakan customer dengan spending score sangat tinggi, annual income tinggi, dengan rata-rata umur 30 dan gender Female atau perempuan.
    - kluster 2 merupakan customer dengan spending score rendah, dengan rata-rata annual income sangat rendah dan umur 45.5 tahun.
    - kluster 3 merupakan customer dengan spending score sedang, annual income rendahdengan rata-rata umur 51 dan gender perempuan.
    - kluster 4 merupakan customer dengan spending score sangat rendah, rata-rata annual income tinggi dengan rata-rata umur 41.5 dan gender male.
    - kluster 5 merupakan customer dengan spending score tinggi, anuual income sedang dengan rata-rata umur 26 dan gender female.
    - kepada manager mall dapat dilaporkan bahwa kluster 1 dan 5 dapat menjadi customer target penjualan dengan pertimbangan spending score yang sangat tinggo dan tinggi.

## 🧵Links

📊 Kaggle Dataset

https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python

📊github dataset knowledgement

https://github.com/SteffiPeTaffy/machineLearningAZ/blob/master/Machine%20Learning%20A-Z%20Template%20Folder/Part%204%20-%20Clustering/Section%2025%20-%20Hierarchical%20Clustering/Mall_Customers.csv


