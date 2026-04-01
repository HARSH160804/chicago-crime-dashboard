# 🔍 Chicago Crime Dashboard

An interactive **R Flexdashboard** for Urban Crime Pattern Analysis and Hotspot Detection using the [Chicago Crime Dataset (2001–2017)](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-present/ijzp-q8t2) — 4.5 million records.

##  Dashboard Pages

### 1. Overview
- **Value Boxes** — Total crimes, arrest rate, most common crime type
- **Top 10 Crime Types** — Interactive horizontal bar chart
- **Crimes by Hour** — Line chart showing daily crime rhythm

### 2. Trends
- **Monthly & Seasonal** distributions
- **Yearly trend** line (2001–2017)
- **Heatmap** — Crime type × time of day

### 3. Hotspot Map
- **Leaflet** interactive map with 10K sampled points
- **K-Means clusters (K=5)** color-coded by zone
- Click any marker for crime type & location details

### 4. ML Results
- **Random Forest** — Confusion matrix & feature importance (arrest prediction)
- **Linear Regression** — R² = 0.083 analysis & explanation
- **K-Means** — Cluster size distribution pie chart

##  Tech Stack

| Component | Technology |
|-----------|------------|
| Framework | R + flexdashboard |
| Charts | plotly |
| Map | leaflet |
| Data Wrangling | dplyr, lubridate |
| ML | randomForest, K-Means |

## 📁 Project Structure

```
├── chicago_crime_dashboard.Rmd   # Source dashboard
├── chicago_crime_dashboard.html  # Rendered output (self-contained)
├── crime_data_clean.rds          # Cleaned dataset — 4.5M rows (not in repo, >100MB)
├── coords_clusters.rds           # 100K sampled coords with cluster labels
├── kmeans_model.rds              # Trained K-Means model (K=5)
├── rf_model.rds                  # Trained Random Forest model
└── ds-lab.ipynb                  # Data preprocessing notebook
```

##  Getting Started

### Prerequisites
- **R** (≥ 4.0)
- **Pandoc** (for knitting)

### Install Dependencies
```r
install.packages(c(
  "flexdashboard", "plotly", "leaflet", "dplyr",
  "ggplot2", "lubridate", "scales", "kableExtra",
  "tidyr", "DT", "htmltools", "rmarkdown"
))
```

### Render the Dashboard
```r
rmarkdown::render("chicago_crime_dashboard.Rmd")
```

> **Note:** You need `crime_data_clean.rds` (245 MB) in the project root to render. This file is excluded from the repo due to GitHub's file size limit. Generate it using `ds-lab.ipynb` or download the dataset from the [Chicago Data Portal](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-present/ijzp-q8t2).

##  Key Insights

- **THEFT** is the most common crime type across all years
- Crime peaks during **summer months** and in the **afternoon/evening**
- **PrimaryType** is by far the strongest predictor of arrest (Random Forest)
- Linear regression's low R² (0.083) confirms the non-linear nature of arrest prediction
- K-Means identifies **5 distinct geographic crime zones** across Chicago

##  License

This project is for educational purposes as part of a Data Science Lab course.
