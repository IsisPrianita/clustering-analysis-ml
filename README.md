# Clustering Analysis — Machine Learning

Unsupervised learning project menggunakan algoritma clustering pada dua dataset: **Penguins** (contoh/eksplorasi) dan **Fall Detection IMU Sensor** (main dataset).

---

## 📁 Struktur Repository

```
clustering-analysis-ml/
├── data/
│   ├── Train.csv          # Training data (fall detection)
│   └── Test.csv           # Testing data (fall detection)
├── penguins.csv           # Dataset eksplorasi
├── Untitled-1.ipynb       # Main notebook (penguins + fall detection)
└── README.md
```

---

## 📊 Dataset

### 1. Penguins Dataset
Dataset eksplorasi berisi data fisik penguin (bill length, flipper length, body mass, dll) dari 3 spesies di 3 pulau berbeda.

### 2. Fall Detection — IMU Sensor
Dataset utama berisi data sensor accelerometer dan gyroscope untuk mendeteksi aktivitas jatuh (*fall*) vs aktivitas normal.

| Kolom | Deskripsi |
|---|---|
| `acc_max` | Nilai maksimum accelerometer |
| `gyro_max` | Nilai maksimum gyroscope |
| `acc_kurtosis` | Kurtosis accelerometer |
| `gyro_kurtosis` | Kurtosis gyroscope |
| `lin_max` | Nilai maksimum linear acceleration |
| `acc_skewness` | Skewness accelerometer |
| `gyro_skewness` | Skewness gyroscope |
| `post_gyro_max` | Post-event gyro max |
| `post_lin_max` | Post-event linear max |
| `label` | Jenis aktivitas (FKL, SDL, FOL, WAL, dll) |
| `fall` | Target: 1 = jatuh, 0 = tidak jatuh |

- Train: **1428 samples**, 13 aktivitas
- Test: **356 samples**

---

## 🔧 Metode

### Preprocessing
- Drop kolom non-fitur (`Unnamed: 0`, `label`, `fall`)
- Drop baris dengan nilai null
- Standarisasi dengan **StandardScaler**

### Algoritma Clustering

| Algoritma | Parameter Terbaik | Silhouette Score |
|---|---|---|
| **K-Means** | k=2 | 0.4139 |
| **DBSCAN** | eps=1.5, min_samples=2 | 0.4151 |
| **Agglomerative** | n=2 | 0.4014 |

### Evaluasi
- **Silhouette Score** — mengukur seberapa baik setiap data point cocok dengan cluster-nya sendiri vs cluster lain (range -1 hingga 1, semakin tinggi semakin baik)
- **Inertia / Elbow Method** — untuk menentukan jumlah cluster optimal pada K-Means

---

## 🚀 Cara Menjalankan

### Requirements
```bash
pip install pandas scikit-learn matplotlib
```

### Langkah
1. Clone repository ini
```bash
git clone https://github.com/<username>/clustering-analysis-ml.git
cd clustering-analysis-ml
```

2. Pastikan file `Train.csv` dan `Test.csv` ada di folder `data/`

3. Buka notebook
```bash
jupyter notebook Untitled-1.ipynb
```

4. **Restart Kernel & Run All**

---

## 📦 Dependencies

```
pandas
scikit-learn
matplotlib
jupyter
numpy
```
