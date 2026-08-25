# 🏡 King County House Price Prediction 

Ciao! This is my personal **Machine Learning** project, originally born from a university course where we didn’t use Python.  
I decided to **rebuild the entire pipeline in Python** to deepen my understanding of the process.  

Compared to the original KNIME version, this Python implementation adds several new components and improvements.  
The aim here is not to achieve *state-of-the-art* performance, but to build a **clear, robust and reusable pipeline**: something that can serve as a solid base for future projects.

---

## Dataset
The project uses the [**House Sales in King County, USA** dataset](https://www.kaggle.com/datasets/harlfoxem/housesalesprediction) from Kaggle.  

---

## Repository Structure
- `ML_python.ipynb/` -> Jupyter notebooks for data exploration, preprocessing, and modeling
- `Data/` -> X_train and test & X_train and test after feature selection
- `Pictures/` -> Some graphs obtained during the development 

---

## Goal
The primary goal was to create a **clean and modular pipeline** that is:
- Easy to understand
- Reusable for other regression tasks
- Flexible enough to adapt to new data

---

## Project Scope
This repository contains the **full machine learning workflow**, from raw data exploration to final model evaluation and interpretation, including:

### Data Exploration & Preprocessing
- In-depth **EDA** (Exploratory Data Analysis)
- **Feature engineering**: creation of new variables (and clustering)  
- **Feature transformation**: handling skewness, scaling, and encoding

### Modeling Workflow
- **Baseline model**: Linear Regression with **ElasticNet-based** feature selection  
- **Non-linear models**: RFECV feature selection using Random Forest importance  
- **1-SE rule** to simplify selected feature sets without hurting performance

### Models Implemented
- **Random Forest**
- **Histogram Gradient Boosting**
- **XGBoost**
- **LightGBM**
- **MLP Neural Network**
- **Stacking Model** -> combining XGBoost & Random Forest, with Ridge Regression as the meta-model

### Evaluation & Insights
- Full performance comparison using **MAE** and other metrics  
- **Residual analysis** with visual diagnostics and confidence interval 
- **SHAP analysis** for XGBoost interpretability

Final Model Comparison

| Model                         | Train MAE ($) | Test MAE ($) | Test R²  | Test MAPE |
|-------------------------------|---------------|--------------|----------|-----------|
| Stacking                      | 39,005.30     | 60,485.97    | 0.9068   | 0.1108    |
| XGBoost_OPTUNA                | 35,802.73     | 60,584.01    | 0.9009   | 0.1115    |
| LightGBM_OPTUNA               | 36,601.14     | 61,317.34    | 0.8992   | 0.1122    |
| HistGradientBoosting_OPTUNA   | 40,332.58     | 62,304.12    | 0.8958   | 0.1145    |
| NNMLP_OPTUNA                  | 59,772.98     | 66,262.63    | 0.9003   | 0.1212    |
| RandomForest_OPTUNA           | 49,574.40     | 70,399.09    | 0.8488   | 0.1230    |
| LinearRegression_ElasticNetCV | 70,051.93     | 71,748.78    | 0.8938   | 0.1314    |

Price Interval with MAPIE

| Price Bin                     | Coverage | Avg Interval Width ($) | Avg True Price ($) | Count |
|-------------------------------|---------|-----------------------|------------------|-------|
| 1. Lowest Price (Bottom 20%)  | 84.7%   | 138,490               | 240,055          | 1323  |
| 2. Low-Mid Price (20-40%)     | 92.3%   | 168,910               | 351,006          | 1277  |
| 3. Mid Price (40-60%)         | 93.1%   | 211,462               | 459,650          | 1294  |
| 4. High-Mid Price (60-80%)    | 92.5%   | 275,370               | 610,143          | 1298  |
| 5. Highest Price (Top 20%)    | 87.8%   | 629,940               | 1,090,647        | 1292  |

