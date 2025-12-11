# 🌍 Project: World Happiness Report Analysis and Prediction

## 📋 Project Description
Exploratory analysis and predictive modeling of the World Happiness Report using 2015 data, with the goal of predicting countries' happiness scores based on economic and social factors.

---

## 🔄 Steps Performed

### 1️⃣ Data Loading and Exploration
- 📥 Downloaded dataset from Kaggle (World Happiness Ranking Dataset)
- 📊 Loaded 1,231 records with 14 columns
- 🔍 Identified significant null values in multiple columns

### 2️⃣ Exploratory Analysis
- 📈 Visualized missing values using `missingno`
- 🔥 Generated correlation matrix to identify relationships between variables
- ⭐ Notable correlation: Happiness Score and Family (0.694)

### 3️⃣ Data Cleaning
- 🧹 Removed records without Happiness Score
- ❌ Dropped columns with high missing data or irrelevant features:
  - Unnamed: 0
  - Region
  - Happiness Rank
  - Standard Error
  - Family
  - Health (Life Expectancy)
  - Trust (Government Corruption)
  - Dystopia Residual
- 🎯 Filtered data for year 2015
- ✅ Final dataset: 158 records

### 4️⃣ Final Variables Used
**🎯 Target Variable:**
- Happiness Score

**📊 Predictor Variables:**
- Economy (GDP per Capita)
- Freedom
- Generosity
- Country

### 5️⃣ Data Preparation
- 📂 Dataset split:
  - 60% training
  - 20% validation
  - 20% testing
- ⚙️ Preprocessing pipeline:
  - Missing value imputation (SimpleImputer with 'mean' strategy for numerical)
  - Robust scaling (RobustScaler)
  - One-hot encoding for categorical variables

### 6️⃣ Model Evaluation
Tested 13 regression models using cross-validation (RepeatedKFold, 3 splits, 3 repeats):

| Model | Mean MAE | Std. Dev. |
|--------|----------|-----------|
| Linear Regression | 0.500 | 0.050 |
| Random Forest | 0.478 | 0.050 |
| Extra Trees | 0.478 | 0.058 |
| AdaBoost | 0.503 | 0.045 |
| Gradient Boosting | 0.505 | 0.043 |
| Theil-Sen | 0.508 | 0.058 |
| SGD Regressor | 0.516 | 0.064 |
| Poisson | 0.526 | 0.055 |
| KNN | 0.534 | 0.059 |
| SVR | 0.547 | 0.053 |
| Decision Tree | 0.579 | 0.056 |
| Tweedie | 0.701 | 0.081 |
| Quantile | 0.954 | 0.110 |

### 7️⃣ Selected Model
**🏆 Linear Regression** was chosen for:
- ✅ Good balance between accuracy and simplicity
- 📊 Greater stability across validations
- 💡 Better interpretability
- 🎯 Consistent results

### 8️⃣ Final Model Evaluation

**📈 Validation Metrics:**
- MAE: 0.500
- MSE: 0.350
- RMSE: 0.592
- R²: 0.730

**🎯 Test Metrics:**
- MAE: 0.490
- MSE: 0.340
- RMSE: 0.583
- R²: 0.740

---

## 🎯 Results

The Linear Regression model successfully explained approximately **74% of the variance** in happiness scores (R² = 0.74), with an average error of **0.49 points** on the happiness scale.

---

## 💡 Key Findings

1. **🔗 Significant correlation:** The "Family" factor showed a 0.694 correlation with Happiness Score, being one of the most relevant predictors before its removal.

2. **⚖️ Model stability:** Linear Regression proved more robust than more complex models like Random Forest or Extra Trees, despite these showing slightly lower MAE values.

3. **🔄 Imputation order irrelevant:** Different imputation orders (roman, arabic, ascending, descending) were tested with IterativeImputer, all producing identical results, confirming that order doesn't affect performance on this dataset.

4. **⚡ Effective simplicity:** More complex models didn't offer significant improvements to justify their greater computational complexity.

5. **💰 Economic and social predictors:** The variables Economy (GDP per Capita), Freedom, and Generosity were sufficient to obtain reasonable predictions of happiness levels.

---

## 🎓 Conclusions

✅ Linear Regression is an effective solution for predicting Happiness Score, balancing accuracy, interpretability, and simplicity.

✅ With only three numerical variables (Economy, Freedom, Generosity), it's possible to reasonably predict a country's happiness level.

✅ The average error of ~0.5 points is acceptable considering the scale ranges from 0 to 10 and the observed range was 2.8 to 7.6.

⚠️ The high amount of missing data in the original dataset (especially in recent years) limited the analysis to 2015 data.

🚀 To improve the model, it would be beneficial to obtain more complete and recent data, as well as explore interactions between variables.
