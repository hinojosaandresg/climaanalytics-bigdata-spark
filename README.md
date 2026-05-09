# 🌎 ClimaAnalytics

> Big Data + Machine Learning on 1.6M weather records with Apache Spark, PySpark ML, and Databricks.

[![Spark](https://img.shields.io/badge/Apache%20Spark-3.5-E25A1C?logo=apachespark&logoColor=white)](https://spark.apache.org/)
[![Databricks](https://img.shields.io/badge/Databricks-Free%20Edition-FF3621?logo=databricks&logoColor=white)](https://www.databricks.com/)
[![Python](https://img.shields.io/badge/Python-3.10-3776AB?logo=python&logoColor=white)](https://www.python.org/)

---

## 📌 Overview

Can we automatically group 36 cities around the world into homogeneous climate profiles without manual labeling? Which variable — temperature, humidity, pressure, or wind — best differentiates these groups?

This project answers both questions by processing **1,629,108 hourly weather records** (5 years, 36 cities) with Apache Spark on Databricks, applying a PySpark ML Pipeline with K-Means (k=5) and evaluating it via Silhouette Score.

**Key finding:** **relative humidity**, not temperature, is the variable that most differentiates climates — a counterintuitive result with practical applications in agriculture, energy, tourism, and climate risk modeling.

---

## 🛠️ Tech stack

| Component | Technology |
|-----------|-----------|
| Platform | Databricks Free Edition (Serverless) |
| Distributed processing | Apache Spark 3.5 + PySpark |
| SQL analytics | Spark SQL |
| Machine Learning | PySpark ML — `Pipeline` + `KMeans` + `StandardScaler` |
| Evaluation | `ClusteringEvaluator` (Silhouette Score) |
| Language | Python 3.10 |

---

## 📂 Repository structure

```
ClimaAnalytics/
├── README.md                          ← this file
├── notebooks/
│   └── ClimaAnalytics_Showcase.ipynb  ← main notebook (portfolio version)
├── docs/
│   └── ClimaAnalytics_Report.pdf      ← full academic report
└── images/
    ├── cluster_distribution.png       ← visualizations (optional)
    └── temperature_trend.png
```

---

## 🚀 How to run it

### Option 1: Databricks Free Edition (recommended)
1. Create a free account at [Databricks Free Edition](https://www.databricks.com/learn/free-edition).
2. Download the dataset CSVs from [Kaggle](https://www.kaggle.com/datasets/selfishgene/historical-hourly-weather-data).
3. Upload the files to a Unity Catalog volume (`/Volumes/workspace/default/clima_g5/`).
4. Import the notebook and run the cells in order.

### Option 2: Local Spark
1. Install PySpark: `pip install pyspark`
2. Adjust the `BASE` variable to point to your local path.
3. Run the notebook with Jupyter.

---

## 📊 Key results

### The 5 climate profiles identified

| Cluster | Avg. temp | Humidity | Climate profile |
|---------|-----------|----------|-----------------|
| 0 | 12.83°C | 76.91% | Cold and humid |
| 1 | 18.22°C | 80.27% | Mild and very humid |
| 2 | 24.54°C | 40.56% | Hot and dry |
| 3 | 3.55°C  | 70.09% | Very cold and windy |
| 4 | 14.61°C | 49.61% | Atypical (low pressure) |

### Geographic validation of clusters

- **Eilat (Israel)** → 55.6% in Cluster 2 ✅ Consistent with its desert geography
- **Chicago, Boston, Detroit** → Cluster 3 ✅ Consistent with the U.S. Northeast
- **Atlanta** → Cluster 1 ✅ Consistent with Southeast U.S. climate

### Metrics

- **Silhouette Score:** 0.2924 (low but expected on hourly data with seasonal variation)
- **Most discriminative variable:** relative humidity

---

## 🩺 Application to the biomedical domain

The techniques used in this project are **identical** to those applied in clinical and biomedical research:

| Here (climate) | In biomedical research |
|----------------|------------------------|
| Clustering cities by climate variables | Patient phenotyping by physiological variables |
| K-Means on 1.6M hourly records | Clustering on time-series data from wearables, EEG, ECG |
| Silhouette Score to validate groups | Same score to validate disease subtypes |
| Distributed pipeline on Databricks | Genomic or EHR data processing at scale |

---

## 👥 Authors

- **Andrés Felipe Hinojosa Galindo** — Systems Engineering + Biomedical Engineering  
  [LinkedIn](#) · [GitHub](#)
- **Diego Alexander Millan Gualdron** — Systems Engineering  
  [LinkedIn](#)

**University:** UNICIENCIA — Bucaramanga, Colombia  
**Course:** Big Data (ISN0503)  
**Instructor:** Eng. Jacksson Sonny González Bayona

---

## 📚 References

- [Historical Hourly Weather Data — Kaggle](https://www.kaggle.com/datasets/selfishgene/historical-hourly-weather-data)
- [Apache Spark MLlib documentation](https://spark.apache.org/docs/latest/ml-guide.html)
- [Databricks Free Edition docs](https://docs.databricks.com/aws/en/getting-started/free-edition)
- Zaharia, M. et al. (2010). *Spark: Cluster computing with working sets*. HotCloud.

---

## 📄 License

Academic project for educational purposes. Dataset under Kaggle's public license.
