# 🏡 King County House Price Prediction 

Ciao! 👋 This is my personal **Machine Learning** project, originally born from a university course where we didn’t use Python.  
I decided to **rebuild the entire pipeline in Python** to deepen my understanding of the process.  

Compared to the original KNIME version, this Python implementation adds several new components and improvements.  
The aim here is not to achieve *state-of-the-art* performance, but to build a **clear, robust and reusable pipeline**: something that can serve as a solid base for future projects.

---

## 🚀 Goal
The primary goal was to create a **clean and modular pipeline** that is:
- Easy to understand
- Reusable for other regression tasks
- Flexible enough to adapt to new data

---

## 📋 Project Scope
This repository contains the **full machine learning workflow**, from raw data exploration to final model evaluation and interpretation, including:

### 🔍 Data Exploration & Preprocessing
- In-depth **EDA** (Exploratory Data Analysis)
- **Feature engineering**: creation of new variables (and clustering)  
- **Feature transformation**: handling skewness, scaling, and encoding

### 🏗️ Modeling Workflow
- **Baseline model**: Linear Regression with **ElasticNet-based** feature selection  
- **Non-linear models**: RFECV feature selection using Random Forest importance  
- **1-SE rule** to simplify selected feature sets without hurting performance

### 🤖 Models Implemented
- **Random Forest**
- **Histogram Gradient Boosting**
- **XGBoost**
- **LightGBM**
- **MLP Neural Network**
- **Stacking Model** -> combining XGBoost & Random Forest, with Ridge Regression as the meta-model

### 📊 Evaluation & Insights
- Full performance comparison using **MAE** and other metrics  
- **Residual analysis** with visual diagnostics and confidence interval 
- **SHAP analysis** for XGBoost interpretability

Final Model Comparison

| Model                         | Train MAE ($) | Test MAE ($) | Test R²  | Test MAPE |
|-------------------------------|---------------|--------------|----------|-----------|
| XGBoost_OPTUNA                | 38,275.63     | 60,139.62    | 0.9115   | 0.1120    |
| Stacking                      | 41,087.46     | 60,261.25    | 0.9131   | 0.1113    |
| LightGBM_OPTUNA               | 37,319.18     | 60,834.00    | 0.9157   | 0.1125    |
| HistGradientBoosting_OPTUNA   | 45,217.81     | 61,998.50    | 0.9125   | 0.1146    |
| NNMLP_OPTUNA                  | 60,961.95     | 68,311.52    | 0.8817   | 0.1225    |
| RandomForest_OPTUNA           | 48,624.16     | 71,608.65    | 0.8462   | 0.1243    |
| LinearRegression_ElasticNetCV | 71,308.79     | 74,208.29    | 0.8768   | 0.1331    |

Price Interval with MAPIE

| Price Bin                     | Coverage | Avg Interval Width ($) | Avg True Price ($) | Count |
|-------------------------------|---------|-----------------------|------------------|-------|
| 1. Lowest Price (Bottom 20%)  | 85.1%   | 142,490               | 239,228          | 1305  |
| 2. Low-Mid Price (20-40%)     | 92.2%   | 165,155               | 346,416          | 1289  |
| 3. Mid Price (40-60%)         | 93.4%   | 212,003               | 455,102          | 1296  |
| 4. High-Mid Price (60-80%)    | 91.4%   | 280,552               | 605,485          | 1297  |
| 5. Highest Price (Top 20%)    | 85.0%   | 575,206               | 1,083,360        | 1297  |


---

## 📦 Dataset
The project uses the [**House Sales in King County, USA** dataset](https://www.kaggle.com/datasets/harlfoxem/housesalesprediction) from Kaggle.  

---

## 🗂️ Repository Structure
- `ML_python.ipynb/` -> Jupyter notebooks for data exploration, preprocessing, and modeling
- `Data/` -> X_train and test & X_train and test after feature selection
- `Pictures/` -> Some graphs obtained during the development 
