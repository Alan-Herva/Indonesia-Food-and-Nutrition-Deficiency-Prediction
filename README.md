# Indonesia Food and Nutrition Deficiency Prediction and Analytics Platform

## Project Information
**Project Name:** Indonesia Food and Nutrition Deficiency Prediction and Analytics Platform  
**Created By:** Team 4 (WASAWIT)  
**Date:** February 19, 2026  
**Version:** 1.0.0  

---

# 1. Executive Summary

## 1.1 Project Overview

**Project Objective**  
Develop a prediction and analytics system to monitor and analyze food and nutrition deficiencies in Indonesia.

**Project Scope**
- Integration of food distribution data
- Food nutrition data analysis
- Food consumption analysis
- Food recommendation system

**Expected Outcomes**
- Predictive model for potential nutrition deficiencies in specific regions
- Interactive analytics dashboard showing regions with food and nutrition deficiencies

**Timeline**
- Project duration: 3 months

---

## 1.2 Stakeholders

### Project Owner
Badan Pangan Nasional Indonesia

### Team Members
| Role | Name |
|-----|-----|
| Project Manager | Alan Herva |
| Data Engineer | Riza Hanafi |
| Data Analyst | Vicky Rizkianto |

### End Users
- Badan Pangan Nasional
- General Public

---

# 2. Data Source Analysis

## 2.1 Government Dataset

### Source Details
| Attribute | Information |
|---|---|
| Dataset Name | Jumlah Penduduk yang Mengalami Ketidakcukupan Konsumsi Pangan Provinsi Update Tahun 2024 |
| Source | https://data.badanpangan.go.id/datasetpublications/dfu/jumlah-pou-provinsi-2024 |
| Data Owner | Badan Pangan Nasional Indonesia |
| Update Frequency | Annual |

### Data Characteristics
| Attribute | Description |
|---|---|
| Format | CSV, JSON, Excel |
| Volume | 17 KB |
| Time Coverage | 2018 – 2024 |

### Data Fields
| Field | Type |
|---|---|
| No | Integer |
| Tahun | Integer |
| Kode_provinsi | Integer |
| PoU | Float |
| Jumlah_Penduduk | Integer |
| Penduduk_Undernourish | Integer |

### Data Quality Assessment
| Metric | Result |
|---|---|
| Completeness | 100% |
| Accuracy | High (verified by Badan Pangan Nasional Indonesia) |
| Consistency | Good |
| Timeliness | Annual updates |

---

## 2.2 Kaggle Dataset

### Source Details
| Attribute | Information |
|---|---|
| Dataset Name | Indonesian Food and Drink Nutrition |
| Source | https://www.kaggle.com/datasets/anasfikrihanif/indonesian-food-and-drink-nutrition-dataset |
| Data Owner | Ministry of Health of the Republic of Indonesia |
| Update Frequency | Annual |

### Data Characteristics
| Attribute | Description |
|---|---|
| Format | CSV |
| Volume | 75 KB |
| Time Coverage | Not specified |

### Data Fields
| Field | Type |
|---|---|
| id | Integer |
| calories | Integer |
| proteins | Integer |
| fat | Integer |
| carbohydrate | Integer |
| name | String |
| image | Base64 |

### Data Quality Assessment
| Metric | Result |
|---|---|
| Completeness | 100% |
| Accuracy | High (verified by Ministry of Health of the Republic of Indonesia) |
| Consistency | Good |
| Timeliness | Last updated 2 years ago |
| Documentation Quality | Good |

---

## 2.3 Government Dataset

### Source Details
| Attribute | Information |
|---|---|
| Dataset Name | Rata-rata Konsumsi per Jenis Pangan Penduduk Indonesia Provinsi |
| Source | https://data.badanpangan.go.id/datasetpublications/gsp/konsumsi-provinsi |
| Data Owner | Badan Pangan Nasional Indonesia |
| Update Frequency | Annual |

### Data Characteristics
| Attribute | Description |
|---|---|
| Format | CSV, JSON, Excel |
| Volume | 457 KB |
| Time Coverage | 2018 – 2024 |

### Data Fields
| Field | Type |
|---|---|
| No | Integer |
| Tahun | Integer |
| Kode Provinsi | Integer |
| Provinsi | String |
| Kelompok Bahan Pangan | String |
| Komoditas | String |
| Konsumsi Pangan | Float |

### Data Quality Assessment
| Metric | Result |
|---|---|
| Completeness | 100% |
| Accuracy | High (verified by Badan Pangan Nasional Indonesia) |
| Consistency | Good |
| Timeliness | Annual updates |
| Documentation Quality | Good |
