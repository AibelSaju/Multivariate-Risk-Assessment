# Stochastic Modeling of Hydro-Climatic Anomalies: A Multivariate VAR Approach to Atmospheric Risk in Coastal Kerala (1990–2025)

## 📌 Project Overview
This repository contains the end-to-end data processing pipeline, advanced statistical modeling frameworks, and empirical climate diagnostics developed for my final year M.Sc. Statistics project at Nirmala College Autonomous, Muvattupuzha. Mentored by Mr. Jecko Augustine (Senior Data Scientist, Austria) and coordinated under academic supervision, this study establishes a high-precision, predictive roadmap for atmospheric dynamics along the vulnerable coastline of Kerala, focusing on the Kochi and Thiruvananthapuram districts[cite: 2].

By analyzing a continuous, 36-year climate record (1990–2025) sourced from the ECMWF ERA5 Global Reanalysis[cite: 2], this research rigorously documents a decadal transition toward an extreme, high-variance climate regime[cite: 2]. It bypasses static, traditional forecasting limitations by engineering an adaptive, walk-forward rolling Vector Autoregression (VAR) system that treats the coastal atmosphere as a dynamically coupled physical engine[cite: 2].

---

## 🛠️ Software Tools & Programming Packages

### 1. Large-Scale Data Engineering
* **Microsoft Excel (Power Query):** Utilized for the initial ingestion, structural parsing, and row-merging of multi-gigabyte daily climate files[cite: 2]. It served as our primary tool for executing **Weekly Aggregation**, successfully eliminating high-frequency diurnal noise to isolate clear macro-level climate signals[cite: 2].
* **Structured CSV Storage:** Maintained as the uniform, zero-degradation transfer medium to port processed matrices directly into our programming environment[cite: 2].

### 2. Statistical Computing & Econometric Pipelines (Python)
* **Statsmodels:** The central engine for time-series infrastructure. Used to execute Augmented Dickey-Fuller (ADF) tests, estimate multi-lag Vector Autoregression matrices, and compute Johansen Trace Statistics[cite: 2].
* **SciPy (Stats Module):** Deployed for Maximum Likelihood Estimation (MLE) for decadal probability distribution fitting, heteroscedasticity checks, and computing Levene's variance tests[cite: 2].
* **Pandas & NumPy:** Engineered for fast vectorization, dynamic rolling window allocations, datetime slicing, and matrix manipulations[cite: 2].
* **Matplotlib & Seaborn:** Used to output high-resolution, publication-grade analytical plots, multi-panel line graphs, and correlation heatmaps[cite: 2].

---

## 📊 Dataset & Multi-Layer Variables
The research tracks a synchronized, 8-variable interconnected atmospheric system aggregated to weekly intervals over a 36-year horizon (1,820 observations per district)[cite: 2]:

| Variable Layer | Variable Code | Measurement Unit | Physical & Modeling Significance |
| :--- | :--- | :--- | :--- |
| **Precipitation (Target)** | `tp_mm` | mm / week | **Primary Target:** Heavily right-skewed, characterized by sudden stochastic rain shocks[cite: 2]. |
| **Thermodynamic** | `t2m` | Kelvin (K) | **Thermal Driver:** Captures ambient energy available for moisture evaporation[cite: 2]. |
| **Thermodynamic** | `d2m` | Kelvin (K) | **Humidity Proxy:** Measures dew point; functions as an indicator of air mass saturation[cite: 2]. |
| **Synoptic Barometric** | `sp_hpa` | hPa | **Barometric Indicator:** Regulates local wind convergence and monsoonal low-pressure systems[cite: 2]. |
| **Kinematic Energy** | `ws` | m/s | **Kinetic Proxy:** Tracks speed of moisture-laden vectors moving from the Arabian Sea[cite: 2]. |
| **Kinematic Component** | `u10` | m/s | **Zonal Wind:** Quantifies East-West directional air mass momentum[cite: 2]. |
| **Kinematic Component** | `v10` | m/s | **Meridional Wind:** Quantifies North-South directional air mass momentum[cite: 2]. |
| **Kinematic Shock** | `fg10` | m/s | **Wind Gusts:** Captures high-energy, volatile kinetic micro-shocks[cite: 2]. |

---

## 🔬 Methodological Framework in Detail

### 1. Pre-Processing & Mathematical Signal Extraction
To protect the multivariate framework from spurious results, data fields underwent a rigid preprocessing pipeline[cite: 2]:
* **Logarithmic Stabilization:** Log-transforms linearize exponential growth and anchor variances across severe weather shocks[cite: 2]:
  $$y_t = \ln(Y_t)$$
* **Additive Classical Decomposition:** Predictable 52-week seasonal monsoon tracks ($S_t$) and long-term deterministic climate drifts ($T_t$) were systematically isolated, outputting clean, unmasked stochastic anomaly residuals ($R_t$) for modeling[cite: 2]:
  $$Y_t = T_t + S_t + R_t$$
* **Decadal Block Standardization:** To combat heteroscedasticity across decades, data was standardized within ~12-year blocks[cite: 2]:
  $$Z_{t,i} = \frac{Y_{t,i} - \mu_i}{\sigma_i}$$
  *Post-correction validation via Levene's Test confirmed successful variance stabilization (Precipitation residual $p\text{-value} = 0.3340$)[cite: 2].*

### 2. Structural Connectivity & Johansen Cointegration
Before executing multivariate modeling, a Johansen Trace Test was implemented to evaluate system equilibrium[cite: 2]. Evaluated using eigenvalues $\hat{\lambda}_i$:
$$\lambda_{\text{trace}}(r) = -T \sum_{i=r+1}^{n} \ln(1 - \hat{\lambda}_i)$$
The analysis rejected the null hypothesis across all levels up to $r \le 7$, proving a **Full Rank ($r=8$) cointegration matrix**[cite: 2]. This mathematically confirms that temperature, pressure, and wind behave as a synchronized physical unit along the Kerala coast, preventing the statistical system from collapsing into chaos[cite: 2].

### 3. Dynamic Rolling Window VAR Architecture
To capture time-varying climate volatility, the repository utilizes a **Walk-Forward Validation Framework**[cite: 2]. Rather than running a static estimation, the model shifts forward weekly, continually ingesting fresh observations to rebuild its parameter weights[cite: 2]:
$$Y_t = c + \sum_{i=1}^{p} \Phi_i Y_{t-i} + \epsilon_t$$
Where $Y_t$ represents the coupled vector of anomalies, $\Phi_i$ represents structural interdependency coefficient matrices, and $\epsilon_t$ captures pure stochastic shock innovations[cite: 2]. This rolling pattern successfully bypasses predictive mean-reversion decay, preventing forecasts from flattening over extended horizons[cite: 2].

### 4. Parametric Decadal Probability Fitting
Residuals were grouped into separate decadal blocks (1990s, 2000s, 2010s, 2020s) to map statistical profile evolution[cite: 2]:
* **Gaussian (Normal) Curve Fitting:** Employed to track structural changes, flattening, and location shifts in thermodynamic ($t2m, d2m$) and barometric ($sp$) series[cite: 2].
* **Weibull Modeling:** Optimized for highly asymmetric wind dynamics ($ws, fg10$)[cite: 2].
* **Gamma Frameworks:** Applied directly to precipitation ($tp\_mm$) to mathematically map the expanding heavy-tail risk behavior of severe flood anomalies[cite: 2].

---

## 📉 Key Findings & Climatic Verdicts
* **The Normalization of Extremes:** Across all variables, a distinct decadal flattening of probability distributions is observed[cite: 2]. The high, stable density peaks characteristic of the 1990s have been replaced by wide, low-density curves in the 2020s, indicating that intense weather shocks have moved from historical outliers to structural norms[cite: 2].
* **Kochi vs. Thiruvananthapuram Divergence:** Kochi experiences severe right-tail vulnerabilities, expanding towards intense +400 unit precipitation surges and rapid thermal spikes[cite: 2]. Thiruvananthapuram exhibits a broader baseline dispersion inside its pressure and kinematic wind fields, rendering the southern coast highly susceptible to sudden synoptic-scale disruptions[cite: 2].
* **Barometric Pull Laws:** The data establishes a negative correlation between pressure and precipitation[cite: 2]. The final forecast for 2026 maps a significant wet year for Thiruvananthapuram, driven by a lower predicted barometric baseline (994.38 hPa) pulling in elevated monsoonal moisture[cite: 2].

---

## 🖼️ Figures & Visualizations Gallery
*(Once you upload your Python-generated PNG graphs to your repository folder, update the file paths below to view them directly on your profile)*

### 1. Exploratory Data Analytics & Trends
* **Weekly Atmospheric Heartbeat (1990-2025):** Tracks continuous fluctuations in temperature, wind speed, and rain surges.
  ![Figure 2.1 - Weekly Climate Trends](figures/figure_2_1.png)[cite: 2]
* **District Climatology Signatures:** Multi-panel seasonal comparison mapping Kochi's high precipitation ceilings against TVM's elevated monsoonal wind velocity.
  ![Figure 2.2 - Monthly Climatology Comparison](figures/figure_2_2.png)[cite: 2]
* **Atmospheric Correlation Matrix:** Quantifies the linear lead-lag interdependencies within the coastal climate ecosystem.
  ![Figure 2.8 - Kochi Variable Correlations](figures/figure_2_8.png)[cite: 2]

### 2. Model Diagnostics & Tracking Backtests
* **Johansen Trace Statistics vs. 95% Critical Threshold:** Visual confirmation of full-rank system cointegration.
  ![Figure 3.1 - Johansen Cointegration Output](figures/figure_3_1.png)[cite: 2]
* **Rolling VAR 2025 Walk-Forward Validation:** Stress test plotting the adaptive forecast tracking the actual climate lines of 2025 with zero mean-reversion collapse.
  ![Figure 3.2 - Rolling VAR Tracking](figures/figure_3_2.png)[cite: 2]

### 3. Decadal Probability Density Function (PDF) Evolutions
* **Gamma Precipitation Shift (Heavy-Tail Analysis):** Illustrates the visual extension of Kochi's right-tail rainfall risks across the decades.
  ![Figure 3.9 - Decadal Rainfall Shift](figures/figure_3_9.png)[cite: 2]
* **Gaussian Flattening of Temperature and Pressure:** Captures the structural widening and loss of climatic equilibrium from the 1990s through the 2020s.
  ![Figure 3.7 - Decadal Temperature Shift](figures/figure_3_7.png)[cite: 2]
