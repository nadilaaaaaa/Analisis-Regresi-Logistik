# Analisis Regresi Logistik : Pengaruh Usia Ibu Hamil dan Jarak Kehamilan Terhadap Status Anemia

## 🏢 Project Overview
Projek ini merupakan bagian dari tugas kuliah yang menganalisis variabel-variabel yang memengaruhi **status anemia terhadap ibu hamil** menggunakan metode **regresi logistik biner**. Data bersumber dari penelitian skripsi yang relevan.

---

## 🎯 Project Objective
- Mengidentifikasi variabel-variabel yang secara signifikan memengaruhi status anemia pada ibu hamil. 
- Mengembangkan model prediktif berbasis **regresi logistik** untuk memperkirakan probabilitas anemia pada ibu hamil.
- Mengevaluasi performa model melalui uji kesesuain model

---

## 🧠 Key Responsibilities
Sebagai analis data, langkah-langkah utama yang dilakukan meliputi:
- Mengimpor dan membersihkan dataset ibu hamil menggunakan **R**.  
- Melakukan **eksplorasi data** untuk memahami distribusi dan hubungan antar variabel.  
- Mengkodekan variabel kategorik dan menyesuaikan tipe data.  
- Membangun model **regresi logistik biner** untuk memprediksi status anemia pada ibu hamil.
- Mengevaluasi model dengan **pseudo R²** dan **akurasi prediksi**.

---

## 📘 Dataset Description
Data yang digunakan adalah data sekunder yang bersumber dari skripsi Apriliyani Varamita dengan judul ***ANALISIS REGRESI LOGISTIK DAN APLIKASINYA PADA PENYAKIT ANEMIA UNTUK IBU HAMIL DI RSKD IBU DAN ANAK SITI FATIMAH MAKASSAR***.
### Variabel yang digunakan
| Variabel | Keterangan | Jenis |
|-----------|-------------|-------|
| Status anemia | Y=1 (hemoglobin < 10,5 g/dbl yang berarti pasien terkena anemia), Y=2 (hemoglobin > 10,5 g/dbl yang berarti pasien tidak terkena anemia)| Dependen |
| Usia ibu | Usia responden (tahun) | Independen |
| Jarak kehamilan | Jarak antar kehamilan (tahun) | Independen |

---

## 🧩 Tools
- **R Programming Language**  
- **Packages:** `openxlsx`, `pscl`, `performance`, `car`, `rcompanion`
  
---

## 📈 Analytical Steps
1. Data Cleaning & Exploratory Data Analysis (EDA)  
2. Transformasi variabel kategorik ke faktor  
3. Estimasi model logistik  
4. Interpretasi koefisien
5. Evaluasi model (Goodness of Fit, Pseudo R²)

---

## 💻 Code (R)
```r
# Import Packages
library(openxlsx)
library(pscl)
library(performance)
library(car)
library(rcompanion)

# Import Data
data_penyakit_anemia <- read.xlsx("Downloads/data penyakit anemia.xlsx")
data_penyakit_anemia

# Statistika Deskriptif
summary(data_penyakit_anemia)
hist(data_penyakit_anemia$`Status.anemia`, main = "Histogram Hemoglobin Pada Ibu Hamil", xlab = "Hb (g/dbl)", ylab = "frequency",col = "blue")

# Model Regresi Logistik
data_anemia <- read.xlsx("Downloads/data anemia.xlsx")
data_anemia
X1 <- data_anemia$Usia.ibu
X2 <- data_anemia$Jarak.kehamilan
Y <- as.factor (data_anemia$Status.anemia)
datafr <- data.frame(X1,X2,Y)
str(datafr)

reglog <- glm(Y~X1+X2, data = datafr, family = binomial)
summary(reglog)

# Uji Kesesuaian Model
performance_hosmer(reglog, n_bins = 10)

# Uji Nagelkerke’s R Square
nagelkerke(reglog)

# Uji Signifikansi Keseluruhan Model
pR2 (reglog)
qchisq(0.95,0)
```
---

# 👩‍💻 Author
Nadila
Mahasiswi Statistika (2023) - Universitas Brawijaya
##### 📍 Analisis ini disusun untuk tujuan akademik dan pengembangan keterampilan analisis data menggunakan R.
##### 📍 Penjelasan lebih rinci tersedia di RPubs: https://rpubs.com/NadilaNadila__/AnalisisRegresiLogistik

---

# 📚 References
- Varamita, A. (2017). Analisis Regresi Logistik dan Aplikasinya pada Penyakit Anemia untuk Ibu Hamil di RSKD Ibu dan Anak Siti Fatimah Makassar.
- Subandriyo, B. (2020). Analisis Korelasi dan Regresi. Badan Pusat Statistik.

---
