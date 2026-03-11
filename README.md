# 📈 Global Stock Market Analytics — Predicting Market Direction

**OJT Project | Binal Doshi | SAP ID: 53026250002**

A data-driven analysis of six major global stock market indices from 2016–2025, culminating in a binary classification model that predicts whether the **NIFTY 50 will open positive or negative** on any given trading day.

---

## 🌍 Indices Covered

| Index | Market |
|---|---|
| NIFTY 50 (`^NSEI`) | India |
| Dow Jones (`^DJI`) | USA |
| NASDAQ Composite (`^IXIC`) | USA |
| Hang Seng (`^HSI`) | Hong Kong |
| Nikkei 225 (`^N225`) | Japan |
| DAX (`^GDAXI`) | Germany |
| VIX (`^VIX`) | Volatility Index |

---

## 🗂️ Project Structure

### Phase 1 — Data Collection & Preprocessing
- Downloaded ~10 years of OHLCV data (2016–2025) using `yfinance`
- Computed daily percentage returns for each index
- Merged all indices into a single master dataset, aligned by trading date
- Handled missing values via forward-fill (LOCF)
- Confirmed no structural nulls in any index

### Phase 2 — Exploratory Data Analysis
- **Normality Testing**: Shapiro-Wilk test confirmed daily returns for all indices are non-normal (p-values ≪ 0.05), meaning fat-tailed distributions are present
- **Box-Whisker Plots**: Visualised return distributions by year — 2020 stands out with the widest boxes and most extreme outliers (COVID-19 impact)
- **Yearly Summary Table**: Per-index count, mean, and standard deviation of daily returns by year
- **Median Return Bar Charts**: Year-wise median returns highlighting key macro events (COVID crash in 2020, rate hike impact in 2022)
- **Quarterly Heatmaps**: Year × Quarter heatmaps for each index revealing seasonal patterns and recovery timelines
- **Correlation Matrix**: 10-year and 2025-specific correlation matrices — Dow Jones and NASDAQ are the most tightly correlated (r = 0.83); NIFTY 50 shows moderate global linkage

### Phase 3 — Pre-COVID vs Post-COVID Analysis
- Measured the time taken for each market to recover to its pre-COVID price level
- Compared volatility and trajectory of recovery across markets

### Phase 4 — NIFTY 50 Target Engineering & Feature Selection
- Created binary target variable `Nifty_Open_Dir`: **1** if today's NIFTY open > yesterday's close, **0** otherwise
- Analysed positive opening frequency by year (e.g. 74.6% in 2017 vs ~59% in 2022)
- Used lagged global index returns (especially Dow Jones) as predictive features
- Visualised global market behaviour split by NIFTY opening direction to guide feature selection

---

## 🔑 Key Findings

- **2020 was the most volatile year** across all markets due to COVID-19, but was followed by strong recoveries — especially in NASDAQ and NIFTY 50
- **NASDAQ showed the sharpest corrections in 2022**, driven by tech-sector selloffs and interest rate hikes
- **Hang Seng underperformed** persistently post-2021, reflecting prolonged stress in Chinese markets
- **Dow Jones' previous-day return is a strong leading indicator** for NIFTY 50's opening direction
- Daily returns across all indices **reject normality**, meaning standard statistical models based on Gaussian assumptions need to be used carefully

---

## 🛠️ Tech Stack

- **Python** — pandas, numpy, scipy
- **Data Source** — `yfinance`
- **Visualisation** — matplotlib, seaborn
- **Statistical Testing** — Shapiro-Wilk (normality), correlation analysis
- **Environment** — Jupyter Notebook

---

## 🚀 Getting Started

```bash
# Clone the repository
git clone https://github.com/yourusername/global-stock-market-analytics.git
cd global-stock-market-analytics

# Install dependencies
pip install yfinance pandas numpy scipy matplotlib seaborn jupyter

# Launch the notebook
jupyter notebook OJT_BINAL.ipynb
```

> **Note:** Data is fetched live via `yfinance` at runtime. An internet connection is required.

---

## 📌 Future Scope

- Train classification models (Logistic Regression, Random Forest, XGBoost) on engineered features to predict `Nifty_Open_Dir`
- Add macroeconomic indicators (USD/INR exchange rate, crude oil prices, bond yields)
- Deploy as a live prediction dashboard using Streamlit or Flask

---

## 👩‍💻 Author

**Binal Doshi** | OJT Project — Global Stock Market Analytics
