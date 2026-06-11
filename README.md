# Data Engineering

# Proyek : Indonesia Food and Nutrition Defiency Prediction

## Kontributor
| Nama | Nim | Peran |
|------|------|------|
| Alan Herva Ikhsan Saputra | 244311001 | Project Manager |
| Riza Hanafi | 244311026 | Data Engineer |
| Vicky Rizkyanto | 244311030 | Data Analyst |

# Deskripsi Proyek
Proyek ini bertujuan untuk mengembangkan sistem prediksi dan analitik guna mengidentifikasi potensi kekurangan pangan, nutrisi, dan gizi di berbagai wilayah di Indonesia. Sistem dibangun melalui integrasi data persebaran pangan, kandungan nutrisi makanan, serta pola konsumsi masyarakat untuk menghasilkan model prediksi risiko kekurangan gizi pada suatu wilayah. Selain itu, sistem menyediakan analitik berbasis peta yang membantu visualisasi daerah-daerah dengan tingkat kerawanan nutrisi dan gizi

# Manfaat Data / Use Case
 - **Tujuan Proyek**: Mengembangkan sistem prediksi dan analitik untuk menganalisa kekurangan pangan dan gizi di wilayah indonesia
 - **Manfaat**: Data yang digunakan dalam proyek ini memberikan gambaran menyeluruh mengenai kondisi pangan dan gizi masyarakat Indonesia, sehingga dapat dimanfaatkan untuk :
     - Mengidentifikasi wilayah dengan risiko kekurangan nutrisi dan gizi.
     - Menganalisis hubungan antara konsumsi pangan dan kecukupan nutrisi.
     - Menyediakan informasi yang mudah dipahami melalui visualisasi dan peta interaktif.

# Serving Analisis
Analisis pada proyek ini terdiri dari beberapa tahapan utama, yaitu pengambilan dan integrasi data dari berbagai sumber terkait persebaran pangan, kandungan nutrisi makanan, serta pola konsumsi masyarakat (extract). Selanjutnya dilakukan proses pembersihan, transformasi, dan penggabungan data berdasarkan wilayah dan periode waktu tertentu (transform), kemudian hasilnya disimpan ke dalam database untuk kebutuhan analitik dan pemodelan (load). Data yang telah tersimpan disajikan melalui dashboard dan visualisasi peta interaktif untuk memantau kondisi pangan, nutrisi, dan gizi di berbagai daerah dengan menggunakan data studio. Selain itu, data tersebut dimanfaatkan untuk membangun model machine learning yang dapat memprediksi potensi kekurangan nutrisi dan gizi pada suatu wilayah indonesia

# Serving Machine Learning
Dataset hasil proses ETL digunakan untuk membangun model prediksi tingkat kerawanan pangan dan gizi di Indonesia. Proyek ini mengimplementasikan algoritma Facebook Prophet untuk melakukan time series forecasting terhadap persentase penduduk yang mengalami undernourishment pada setiap provinsi berdasarkan data historis. Sebelum pemodelan, dilakukan validasi ketersediaan data sehingga hanya wilayah dengan jumlah data yang memadai yang diproses oleh model. Apabila data historis tidak mencukupi untuk membangun model Prophet, sistem secara otomatis menggunakan Linear Trend Forecasting sebagai metode alternatif untuk menghasilkan prediksi. Hasil prediksi kemudian digunakan untuk menentukan tingkat risiko wilayah (Aman, Waspada, atau Rawan) serta divisualisasikan dalam bentuk grafik dan peta analitik guna mendukung pengambilan keputusan berbasis data.

# Pipeline

## Extract ( Pengambilan Data )
- **Sumber Data**
  - Jumlah Penduduk yang Mengalami Ketidakcukupan Konsumsi Pangan Provinsi Update Tahun 2024 - Badan Pangan Nasional Indonesia (https://data.badanpangan.go.id/datasetpublications/dfu/jumlah-pou-provinsi-2024)
  - Indonesian Food And Drink Nutrition - Kaggle (https://www.kaggle.com/datasets/anasfikrihanif/indonesian-food-and-drink-nutrition-dataset)
  - Rata-rata Konsumsi per Jenis Pangan Penduduk Indonesia Provinsi - Badan Pangan Nasional Indonesia (https://data.badanpangan.go.id/datasetpublications/gsp/konsumsi-provinsi)
 
- **Metode Pengambilan**
  - Langsung download data
  - Membaca data dari file CSV menggunakan `pandas.read_csv()`
  - Melakukan validasi struktur dataset sebelum memasuki proses transformasi.
 
# Transform ( Pembersihan & Transformasi )
- **Pembersihan :**
  - Menstandarkan nama kolom menjadi format yang konsisten (lowercase dan snake_case).
  - Menghapus kolom yang tidak digunakan seperti kolom `No`.
  - Menghapus data duplikat.
  - Menghilangkan kolom kosong atau kolom teknis seperti `Unnamed`.
  - Membersihkan nilai string dari spasi yang tidak diperlukan.
- **Transformasi :**
  - Menggabungkan dataset konsumsi pangan dan dataset POU berdasarkan:
      - Tahun
      - Kode Provinsi
      - Nama Provinsi
- **Feature Engineering :**
  Beberapa fitur turunan dibuat untuk mendukung proses analitik dan prediksi:
  - **Konsumsi per 1000 Penduduk:**
    Mengukur tingkat konsumsi pangan relatif terhadap jumlah penduduk.
  - **Persentase Undernourishment:**
    Menghitung persentase penduduk yang mengalami kekurangan pangan pada setiap wilayah.
  - **Log Penduduk:** 
    Transformasi logaritmik jumlah penduduk untuk mengurangi pengaruh skala data yang terlalu besar pada model prediksi.

# Load ( Pemindahan ke Target )
- **Target:**
  - Sebuah tabel baru di dalam database pada server Aiven. Tabel ini merupakan output utama yang dapat diakses oleh layanan lain untuk melakukan analisis langsung di database.
- **Metode:**  
  - Fungsi to_sql() dari pandas digunakan untuk menulis data dari DataFrame langsung ke tabel di database PostgreSQL
  - konfigurasi fungsi to_sql() diatur dengan parameter-parameter kunci:
    - name diisi dengan yang mendefinisikan nama tabel tujuan
    - con diisi dengan variabel engine, yaitu objek koneksi dari SQLAlchemy
      yang telah dikonfigurasi sebelumnya untuk terhubung ke database Aiven
  - Data diverifikasi dengan membaca 5 baris pertama dari tabel baru tersebut menggunakan pd.read_sql() dan df.head()

## Arsitektur / Workflow ETL  
- **Alur Modular:**  
  - Proses ETL diringkas dalam sebuah fungsi `run_pipeline()` yang mencakup langkah-langkah membaca, membersihkan, mengisi, menggabungkan, dan mengubah data.
  -  Kode diorganisir secara sekuensial di dalam notebook Google Colab.

- **Tools yang Digunakan:**  
  - Python 3.x
  - Library: `pandas`, `numpy`, `sqlalchemy`, `matplotlib`, `prophet`, `scipy`
  - Platform: Google Colab


## Kode Program  
- **Struktur Kode:**  
  - Terdapat 2 notebook: satu untuk ETL, satu untuk Machine Learning.
  - Nama variabel dan fungsi deskriptif: `df_food`, `extract_data()`, `provinsi`, dll.
    
- **Machine Learning:**  
  - Model utama: Facebook Prophet untuk melakukan time series forecasting tingkat undernourishment (kekurangan pangan) pada setiap provinsi berdasarkan data historis.
  - Vvalidasi data : Hanya provinsi dengan minimal 3 tahun data historis yang diproses menggunakan Prophet untuk menjaga kualitas prediksi.
  - Model cadangan (fallback): Linear Trend Forecasting menggunakan regresi linear sederhana `(numpy.polyfit)` apabila data historis tidak mencukupi untuk membangun model Prophet.
  - Output model: Prediksi persentase undernourishment per provinsi pada tahun target beserta interval kepercayaan (confidence interval).
  - Risk Scoring: Hasil prediksi dikategorikan menjadi:
    - Aman (< 5%)
    - Waspada (5% – 10%)
    - Rawan (> 10%)

- **Link Projek:** 
  - ETL Pipeline: https://colab.research.google.com/drive/1cLeOAs0eW7DsCO5Zgw093u3PzytucPfX#scrollTo=Zf_WIb7kf05h
  - Machine Learning : https://colab.research.google.com/drive/1jhE7lNJprZK4csDcpa3tr_9OCCjDqxpU#scrollTo=ceDaV6IyjAcF
  - Data Studio (Looker) : https://datastudio.google.com/reporting/06b3b842-c65f-43b3-b947-5a6077af7c83/page/A5r0F
