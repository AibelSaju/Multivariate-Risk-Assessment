# Stochastic Modeling of Hydro-Climatic Anomalies: A Multivariate VAR Approach to Atmospheric Risk in Coastal Kerala (1990–2025)

## 📌 Project Overview
This repository hosts the data processing pipeline, statistical analysis framework, and predictive analytics developed for my M.Sc. Statistics final year project at Nirmala College Autonomous, Muvattupuzha. The study establishes a multi-variable predictive roadmap for atmospheric volatility and extreme weather risk along the vulnerable coastline of Kerala, focusing on the Kochi and Thiruvananthapuram districts.

---

## 🎯 Objectives of the Study
* **Trend Profiling:** Analyze historical patterns across 8 key atmospheric variables over a continuous 36-year horizon (1990–2025).
* **Decadal Shift Mapping:** Statistically model variance inflation and non-stationarity across separate decadal blocks (1990s vs. 2020s).
* **System Cointegration:** Conduct multi-variable diagnostic tests (Johansen Trace Test) to prove the regional atmosphere operates as a single, physically interconnected system.
* **Adaptive Modeling:** Deploy a Walk-Forward Rolling Vector Autoregression (VAR) framework to capture real-time shocks and avoid predictive decay.
* **Stochastic Forecasting:** Generate a 52-week predictive roadmap for the year 2026 to calculate localized risk metrics for disaster preparedness.

---

## 🛠️ Software Tools & Libraries Used

### 1. Data Processing & Aggregation
* **Microsoft Excel (Power Query):** Used to ingest multi-gigabyte daily reanalysis data, executing structural cleaning and weekly grouping to eliminate noise.

### 2. Statistical Computing & Data Science (Python)
* `statsmodels`: Deployed for core econometric architectures (VAR), unit root testing (ADF), and Johansen cointegration checks.
* `scipy.stats`: Applied for Maximum Likelihood Estimation (MLE) parametric curve fitting and variance checks.
* `pandas` & `numpy`: Leveraged for vectorized matrix operations, data handling, and walk-forward rolling indexes.
* `matplotlib` & `seaborn`: Used to engineer all publication-grade diagnostic plots and heatmaps.

---

## 📊 Dataset & Core Variables
Data was extracted from the **ECMWF ERA5 Global Reanalysis via the Copernicus Climate Data Store (CDS)** at a high-resolution grid layout. 

* **Primary Target Variable:** Total Precipitation (`tp_mm`)
* **Thermodynamic Inputs:** 2m Temperature (`t2m`), 2m Dewpoint Temperature (`d2m`)
* **Synoptic Pressure Inputs:** Surface Pressure (`sp_hpa`)
* **Kinematic Wind Inputs:** 10m Wind Speed (`ws`), Zonal Wind Component (`u10`), Meridional Wind Component (`v10`), 10m Maximum Wind Gust (`fg10`)

---

## 🔬 Modeling Framework Overview
1. **Signal Isolation:** Log-transformations stabilize outlier peaks. Classical additive decomposition breaks down the data into Trend, Seasonality (52-week monsoonal tracks), and Stochastic Residuals.
2. **Cointegration Testing:** The Johansen Trace Test reveals a **Full Rank (r=8)** integration structure, proving true physical connectivity across variables.
3. **Adaptive Tracking:** An 8-week dynamic rolling window systematically rebuilds parameter weights every week, updating the model's short-term memory to capture sudden spikes.
4. **Parametric Curve Fitting:** Residual blocks are mapped to specialized distributions—**Gaussian (Normal)** for temperature/pressure, **Weibull** for wind speeds, and **Gamma** for skewed precipitation tails.

---

## 📈 Key Findings
* **Distribution Flattening:** Across all variables, narrow historical baseline distributions have flattened into broad, lower-density curves. Weather anomalies that were once rare outliers are now becoming regular components of the current climate cycle.
* **Regional Volatility Divergence:** Kochi displays extreme right-tail susceptibility regarding rainfall intensity spikes. Thiruvananthapuram exhibits higher underlying barometric and moisture range volatility.
* **2026 Outlook:** The model projects 2026 to be a highly active wet year for Thiruvananthapuram, anticipating an estimated 22% increase in total precipitation over its historical baseline, heavily pulled by low synoptic barometric pressure states.

---

## 🖼️ Visualizations Gallery

### 1. Trend & Correlation Explorations
* Weekly Climate Indices
* Monthly Climatology Comparison
* Atmospheric Correlation Matrix

### 2. Model Performance & Backtesting
* Johansen Trace Statistics vs. 95% Critical Limit
* Rolling VAR Out-of-Sample Validation Tracking

### 3. Decadal Probability Shifts
* Gamma Rainfall Shift Analysis
* Normal Temperature Destabilization Curve
