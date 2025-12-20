Predicting Year-to-Year Changes in Suicide Rates in South Africa

A Panel-Based Socioeconomic Modeling Approach

📌 Project Overview

This project develops a data-driven, statistically grounded machine learning model to predict year-to-year changes in suicide rates in South Africa, using socioeconomic signals learned from a multi-country panel dataset.

Rather than predicting absolute suicide levels, the model focuses on annual changes, which:

Reduces non-stationarity

Avoids spurious trend learning

Aligns with best practices in epidemiological and economic time-series modeling

The project emphasizes interpretability, robustness, and uncertainty awareness, making it suitable for research, policy analysis, and academic work.

🎯 Objectives

Predict annual changes in suicide rates for South Africa

Learn structural relationships from comparable countries using panel data

Avoid temporal leakage using time-aware validation

Quantify uncertainty in predictions

Produce an interpretable and defensible baseline model

🧠 Methodological Summary
Target Variable

SuicideRate_diff
Year-over-year change in suicide mortality rate (per 100,000 population)

Predictors (3-Year Rolling Averages)

Alcohol consumption per capita

Intentional homicide rate

GDP per capita (current US$)

Rolling averages are used to capture structural trends while reducing short-term noise.

📊 Data Sources

All data comes from authoritative international sources:

Suicide mortality rate – UN SDG / WHO

Alcohol consumption – WHO / UN SDG

Homicide rate – UN SDG

GDP per capita – World Bank (NY.GDP.PCAP.CD)

Countries were selected based on:

Data availability (2000–2024)

Reporting consistency

Socioeconomic comparability

South Africa is explicitly held out as the prediction target.

🧩 Modeling Approach

Model type: Ridge Regression (L2-regularized linear model)

Training strategy:

Panel learning on multiple countries

South Africa excluded from training

Validation:

Time-ordered splits (no future leakage)

Evaluation metrics:

Mean Absolute Error (MAE)

Directional accuracy

Prediction intervals (uncertainty bounds)

This approach was chosen due to:

Small sample sizes per country

High feature collinearity

Need for interpretability and stability

📈 Key Results

SA-only baseline MAE: ~0.369

Panel-trained MAE: ~0.346

Improvement: ~6% reduction in error using panel learning

Residual standard deviation: ~0.53
(Indicates substantial influence of unobserved shocks)

Interpretation

Structural socioeconomic variables explain long-term levels of suicide rates but have limited power over short-term fluctuations, which are dominated by external shocks (e.g., crises, policy changes, societal disruptions).

🔍 Uncertainty & Responsible Interpretation

Predictions are accompanied by 95% uncertainty intervals, reflecting:

Irreducible real-world variability

Ethical responsibility when modeling sensitive outcomes

The model is not intended for individual-level prediction or real-time intervention, but for structural analysis and long-term forecasting insight.


▶️ Example Usage
predict_next_suicide_rate(
    last_rate=22.3,
    alcohol_roll3=7.8,
    homicide_roll3=12.5,
    gdp_roll3=65000
)


Returns a predicted suicide rate for the following year, along with uncertainty bounds.

⚠️ Limitations

Annual data limits sensitivity to short-term shocks

Mental health service indicators are not included due to data gaps

Results should be interpreted at population level only

These limitations are acknowledged and discussed explicitly in the analysis.

🔮 Future Work

Add explicit shock indicators (e.g., COVID, economic crises)

Incorporate health expenditure and mental health proxies

Extend to higher-frequency data where available

Formalize into a publishable academic paper

📜 Disclaimer

This project is intended for research and educational purposes only.
It does not provide clinical, diagnostic, or individual-level predictions.

👤 Author

Rohin Maharaj
Data Science & Applied Machine Learning
South Africa
