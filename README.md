# YouTube Channel Performance & Revenue Analytics

An end-to-end data analytics and predictive machine learning project built to analyze YouTube channel performance metrics, compute key audience engagement KPIs, and accurately predict estimated video revenue while avoiding target leakage.

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Dataset Summary](#-dataset-summary)
- [Key Features & Workflow](#-key-features--workflow)
- [Exploratory Data Analysis & Feature Engineering](#-exploratory-data-analysis--feature-engineering)
- [Machine Learning Model](#-machine-learning-model)
- [Key Insights & Findings](#-key-insights--findings)
- [Repository Structure](#-repository-structure)
- [Installation & How to Run](#-installation--how-to-run)
- [Future Enhancements](#-future-enhancements)

---

## 📌 Project Overview
The objective of this project is to perform comprehensive data exploratory analysis, data cleaning, and feature engineering on YouTube performance data, and subsequently build a robust machine learning regression model to forecast **Estimated Revenue (USD)**.
By identifying the primary operational and engagement drivers of channel revenue, this analytics pipeline provides actionable intelligence for content strategies, revenue optimization, and audience retention.

---

## 📊 Dataset Summary
- **Source**: Kaggle YouTube Channel Performance Dataset
- **Total Records**: 364 rows (video-level aggregated performance logs)
- **Features**: 70 initial columns capturing impressions, watch time, subscriber counts, traffic sources, device types, and monetary revenue breakdowns.
- **Data Quality**: 0 null values across primary metrics after automated verification and cleaning.

---

## 🚀 Key Features & Workflow

### 1. Data Cleaning & Preprocessing
- Converted date-string representations (`Video Publish Time`) into native datetime structures for temporal trend evaluation.
- Parsed duration formats into standardized total operational duration in seconds.
- Handled negative values in differential metrics (e.g., net dynamic Subscriber gains/losses) during descriptive statistics.

### 2. Feature Engineering
Designed domain-specific derived indicators to quantify video efficiency and audience engagement:
- **Engagement Rate (%)**
- **Revenue Per View (RPV)**

### 3. Target Leakage Prevention
To prevent artificial performance inflation and ensure model validity in real-world deployment:
- **Explicit Feature Selection**: Selected pure operational indicators (`Views`, `Subscribers`, `Likes`, `Shares`, `Comments`, `Engagement Rate`).
- **Revenue Exclusion**: Explicitly excluded direct financial components (`Estimated AdSense Revenue`, `Watch Page Ads Revenue`, `YouTube Premium Revenue`, and `RPV`) from feature space $X$.

---

## 🤖 Machine Learning Model

- **Evaluation Metrics**:
  - **Mean Squared Error (MSE)**
  - **R-squared ($R^2$) Score**
- **Artifact Export**: Model persisted as `youtube_revenue_predictor.pkl` via `joblib` for future deployment pipelines.

---

## 💡 Key Insights & Findings
1. **Views & Watch Time Drive Revenue**: Views remain the single highest contributor to estimated revenue, but total watch duration scales monetization exponentially due to mid-roll ad placements.
2. **Engagement Amplifies Distribution**: High engagement rate strongly correlates with higher organic view reach, indirectly driving higher overall revenue.
3. **Outlier Impact**: A small subset of viral long-form videos accounts for a disproportionately large share of total channel revenue.

---

## 📁 Repository Structure
```text
.
├── data/
│   └── youtube_channel_data.csv    # Raw analytics dataset
├── notebooks/
│   └── YouTube_Revenue_Analysis.ipynb # Main end-to-end Python notebook
├── models/
│   └── youtube_revenue_predictor.pkl  # Trained Random Forest model artifact
├── README.md                       # Documentation & Internship Summary
└── requirements.txt                # Dependencies and required libraries
```

---

## 🛠️ Installation & How to Run

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/youtube-revenue-analytics.git
   cd youtube-revenue-analytics
   ```

2. **Set Up Virtual Environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows use: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch Jupyter Notebook**:
   ```bash
   jupyter notebook notebooks/YouTube_Revenue_Analysis.ipynb
   ```

---

## 🔮 Future Enhancements
- Implement time-series analysis (ARIMA/Prophet) to project seasonal revenue spikes.
- Build an interactive Streamlit dashboard for real-time video performance scoring.
- Incorporate Natural Language Processing (NLP) on video titles and tags to evaluate content topic profitability.
