***Modeling Nigeria's GDP with Econometrics and Machine Learning***


This project analyzes how key macroeconomic variables shape Nigeria's economic performance and compares traditional econometric modeling with modern machine learning for GDP prediction.

Using annual Nigerian macroeconomic data from the 1970s through 2023, the analysis evaluates how oil price, oil production, foreign direct investment (FDI), and exchange rate dynamics relate to GDP. The workflow combines time series diagnostics, feature engineering, and predictive modeling to answer a practical question:

When forecasting GDP in an oil-dependent economy like Nigeria, do machine learning models outperform conventional econometric approaches?

The answer from this project is clear: yes. Among the models tested, XGBoost delivered the strongest predictive performance, followed by Random Forest, while ARDL provided a more interpretable but less accurate benchmark.

**Why This Project Matters**

Nigeria's economy is highly exposed to oil market conditions, exchange rate volatility, and external capital flows. That makes macroeconomic forecasting both important and difficult.

**This project is valuable because it shows how to:**

translate an economics research question into a reproducible machine learning workflow, 
combine domain-aware time series preprocessing with predictive modeling, 
compare interpretability-focused econometrics against accuracy-focused ML, 
extract insight from a relatively small macroeconomic dataset without ignoring temporal structure, 

**For recruiters and hiring managers, this project demonstrates practical strength in:**

exploratory data analysis, 
time series reasoning\, 
feature engineering, 
model comparison and evaluation, 
communicating technical findings in an applied economic context, 
Research Objective, 

The goal of the analysis is to model and predict Nigeria's GDP using macroeconomic indicators that are especially relevant in an oil-based economy:

Crude oil price, 
Crude oil production, 
Foreign direct investment (FDI), 
Exchange rate, 

**The notebook compares four modeling approaches:**
Linear Regression, 
Random Forest Regressor, 
XGBoost Regressor, 
ARDL (Autoregressive Distributed Lag), 

**Dataset**
The analysis uses annual macroeconomic data for Nigeria, covering the 1970s to 2023.

**Variables**

gdp_const: Constant GDP, used as the prediction target, 
oil_price: Crude oil price, 
oil_production: Crude oil production, 
fdi_pct: Foreign direct investment percentage, 
exg_rate: Exchange rate, 
year: Time index, 

The notebook reads the data from API.csv.

****Analytical Workflow****
1. Exploratory Data Analysis
The notebook begins with univariate time series plots for each macroeconomic variable. These visualizations show:

sharp oil price volatility over time
changing oil production patterns
irregular FDI behavior
long-run GDP growth
substantial exchange rate escalation in later years
This stage establishes the economic context before modeling begins.

2. Correlation Analysis
A correlation heatmap is used to inspect linear relationships among the macroeconomic variables and GDP. This helps surface early patterns while also motivating the need for models that can capture more than simple linear dependence.

3. Stationarity Testing
The notebook applies the Augmented Dickey-Fuller (ADF) test to each variable.

Key finding:

fdi_pct is stationary at level
oil_price, oil_production, gdp_const, and exg_rate are non-stationary in raw form
This is an important time series step because macroeconomic variables often exhibit trends, structural shifts, and changing variance.

4. Feature Engineering
To improve model readiness, the analysis applies:

log transformation to oil price, oil production, GDP, and exchange rate
lag-1 features to capture temporal dependence
The transformed and lagged features allow the models to learn both current macroeconomic conditions and recent historical effects.

5. Time-Aware Train/Test Split
Instead of shuffling the data, the notebook preserves chronological order:

39 observations for training
11 observations for testing
This is the correct approach for forecasting-style problems because future values should not leak into past training data.

6. Feature Importance Screening
A Random Forest model is first used to estimate feature importance. The most influential predictors were:

log_exg_rate_lag1, 
log_exg_rate, 
log_oil_price,
log_oil_production, 
log_oil_price_lag1, 
This result suggests that exchange rate dynamics are especially important for GDP prediction in this dataset.

7. Model Training and Comparison

The project trains and evaluates:
Linear Regression as a baseline linear model, 
Random Forest for nonlinear ensemble learning, 
XGBoost for boosted tree-based prediction, 
ARDL for econometric time series modeling with lag structure.

***Results***

**Test Performance**
| Model             | Test MSE | Test RMSE |
| ----------------- | -------: | --------: |
| Linear Regression | 0.050233 |  0.224126 |
| Random Forest     | 0.001378 |  0.037126 |
| XGBoost           | 0.000803 |  0.028346 |
| ARDL              | 0.003730 |  0.061073 |

***Best Model***

XGBoost achieved the best predictive accuracy, with the lowest MSE and RMSE on the test set.

Interpretation
XGBoost captured the most complex nonlinear structure in the data, 
Random Forest also performed strongly and confirmed the value of tree-based models for macroeconomic prediction, 
ARDL performed reasonably well and remained useful for interpretability and lag-based economic reasoning, 
Linear Regression was the weakest performer, suggesting that the GDP dynamics in this dataset are not adequately explained by simple linear relationships alone, 

***Key Insights***
Machine learning models outperformed the traditional linear benchmark and the econometric ARDL model on forecasting accuracy, 
Exchange rate variables, especially the lagged exchange rate, emerged as the strongest predictors, 
Log transformation and lagged features materially improved modeling quality, 
Nigeria's GDP dynamics in this analysis appear to contain important nonlinear patterns that tree-based models capture better than linear methods, 

Tech Stack, 
Python, 
Pandas, 
NumPy, 
Matplotlib, 
Seaborn, 
scikit-learn, 
statsmodels, 
XGBoost, 

Project Files
machine_learning-2.ipynb - main analysis notebook, 
API.csv - dataset used in the notebook

Modeling Macroeconomic Indicators in Nigeria manuscript.pdf - research manuscript that provides the academic context for the analysis

**How to Run**
Clone this repository, 
Install the required Python libraries, 
Place API.csv in the same working directory as the notebook, 
Open machine_learning-2.ipynb in Jupyter Notebook or JupyterLab, 
Run the notebook cells in order.

Suggested packages:

pip install pandas numpy matplotlib, 
seaborn,  
scikit-learn,  
statsmodels xgboost notebook.

What This Project Demonstrates

This project highlights the ability to:

work with real-world macroeconomic time series data, 
apply statistical diagnostics before modeling, 
engineer lagged and transformed features thoughtfully, 
Compare econometric and machine learning methods fairly, 
Communicate model performance with business and policy relevance. 

It is especially relevant for roles in:

Data Science, 
Machine Learning, 
Economic Research, 
Quantitative Analysis, 
Policy Analytics, 

Future Improvements
Expand the feature set with inflation, unemployment, interest rate, and trade indicators, 
test rolling-window validation for stronger time series evaluation, 
add SHAP or permutation importance for better model interpretability, 
tune hyperparameters for Random Forest and XGBoost, 
compare against ARIMA, VAR, Prophet, or LSTM-based models.

Author Note
This repository presents the analysis companion to a broader research study on macroeconomic forecasting in Nigeria. The emphasis here is on the hands-on data science workflow: from exploratory analysis and preprocessing to model building, evaluation, and insight extraction.

If you are viewing this as part of my portfolio, this project reflects my interest in using data science to solve economically meaningful problems and to bridge the gap between research thinking and practical predictive modeling.

