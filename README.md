# Project Information

Project Name : Indonesia Food and Nutrition Deficiency Prediction and Analytics Platform  
Created By : Team 4 (WASAWIT)  
Date : February 19, 2026  
Version : 1.0.0  

# Executive Summary

## 1.1 Project Overview

Tujuan Project : Mengembangkan sistem prediksi dan analitik untuk memantau dan menganalisa kekurangan pangan dan gizi di indonesia  

Scope Project : Integrasi data persebaran pangan, nutrisi makanan, konsumsi pangan dan rekomendasi pangan  

Expected Outcomes : Model prediksi potensi kekurangan nutrisi dan gizi pada suatu wilayah dan dashboard analitik interaktif peta daerah kekurangan nutrisi dan gizi  

Timeline : 3 bulan  

## 1.2 Stakeholders

Project Owner : Badan Pangan Nasional Indonesia  

### Team Members
- Data Engineer : Riza Hanafi
- Data Analyst : Vicky Rizkianto
- Project Manager : Alan Herva

### End Users
- Badan Pangan Nasional
- Masyarakat Umum

# 2. Data Source Analysis

## 2.1 Data Pemerintah

### Source Detail
Dataset Name : Jumlah Penduduk yang Mengalami Ketidakcukupan Konsumsi Pangan Provinsi Update Tahun 2024  
URL/Access Point : https://data.badanpangan.go.id/datasetpublications/dfu/jumlah-pou-provinsi-2024  
Data Owner : Badan Pangan Nasional Indonesia  
Update Frequency : Tahunan  

### Data Analysis
Format Data : CSV, JSON, Excel  
Volume Data : 17 KB  
Time Coverage : 2018 - 2024  

### Data Fields
- No (integer)
- Tahun (integer)
- Kode_provinsi (Integer)
- PoU (Double/Float/Decimal)
- Jumlah_Penduduk (Integer)
- Penduduk_Underdourish (Integer)

### Data Quality
Completeness : 100 %  
Accuracy : High (verified by Badan Pangan Nasional Indonesia)  
Consistency : Good  
Timeliness : Update Tahunan  

---

## 2.2 Dataset Kaggle

### Source Detail
Dataset Name : Indonesian Food And Drink Nutrition  
URL/Access Point : https://www.kaggle.com/datasets/anasfikrihanif/indonesian-food-and-drink-nutrition-dataset  
Data Owner : Ministry of Health of the Republic of Indonesia  
Update Frequency : Tahunan  

### Data Analysis
Format Data : CSV  
Volume Data : 75 KB  
Time Coverage : -  

### Data Field
- id (integer)
- calories (integer)
- proteins (integer)
- fat (integer)
- carbohydrat (integer)
- name (string)
- image (string)

### Data Quality
Completeness : 100 %  
Accuracy : High (verified by Ministry of Health of the Republic of Indonesia)  
Consistency : Good  
Timeliness : Updated 2 years ago  
Documentation Quality : Good  

---

## 2.3 Data Pemerintah

### Source Detail
Dataset Name : Rata-rata Konsumsi per Jenis Pangan Penduduk Indonesia Provinsi  
URL/Access Point : https://data.badanpangan.go.id/datasetpublications/gsp/konsumsi-provinsi  
Data Owner : Badan Pangan Nasional Indonesia  
Update Frequency : Tahunan  

### Data Analysis
Format Data : CSV, JSON, Excel  
Volume Data : 457 KB  
Time Coverage : 2018 - 2024  

### Data Field
- No (integer)
- Tahun (integer)
- Kode Provinsi (integer)
- Provinsi (string)
- Kelompok Bahan Pangan (string)
- Komoditas (string)
- Konsumsi Pangan (Float)

### Data Quality
Completeness : 100 %  
Accuracy : High (verified by Badan Pangan Nasional Indonesia)  
Consistency : Good  
Timeliness : Update Tahunan  
Documentation Quality : Good
