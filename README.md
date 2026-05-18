# Harris-County-Property-Value-Prediction-Model

**Predicts property appraised values with 98.14% accuracy using machine learning**

## 🎯 Quick Facts

- **Accuracy:** 98.14% (R² = 0.9814)
- **Average Error:** $41,879
- **Dataset:** 83,595 Harris County properties
- **Best Model:** Linear Regression

## 📊 Results

| Metric 		            | Value 	      |
|-----------------------|---------------|
| **R² Score** 		      | 0.9814 	      |
| **RMSE** 		          | $259,597 	    |
| **MAE** 		          | $41,879 	    |
| **Test Accuracy** 	  | 98% 		      |

## 🏗️ What Drives Property Value

1. **Prior Year Appraised Value (45%)** - Historical assessment baseline
2. **Prior Year Building Value (27%)** - Previous building assessment
3. **Prior Year Land Value (8%)** - Previous land value
4. **Total Area (4%)** - Combined building + land size
5. **School District (3%)** - Location factor

## 🔍 Data & Methodology

**Dataset:**
- 83,595 properties from Harris County
- Cleaned from 700k total records
- Removed 16% invalid/outlier records

**Feature Engineering:**
- Property characteristics (size, age, type)
- Prior year assessments
- Location factors (neighborhood, school district)
- Derived metrics (property type classification)

**Model Development:**
- Linear Regression (Winner)
- Random Forest
- XGBoost
- Train/validation/test split: 70/15/15

## 📁 Project Structure
├── 01_data_cleaning.ipynb          (Data prep & validation)
├── 02_exploratory_analysis.ipynb   (EDA & insights)
├── 03_model_building.ipynb         (Model training & evaluation)
├── models/
│   ├── model_linear_regression.pkl (⭐ Best model)
│   ├── scaler.pkl
│   └── label_encoders.pkl
└── visualizations/
│   ├── eda_analysis.png
│   ├── model_comparison.png
│   └── feature_importance.png

## 🚀 How to Use

**1. View Results (No Code Needed)**
- Open `01_data_cleaning.ipynb` → final summary shows cleaned data
- Open `02_exploratory_analysis.ipynb` → visualizations of property data
- Open `03_model_building.ipynb` → model performance comparison

**2. Make Predictions**
```python
import joblib
import pandas as pd

# Load model
model = joblib.load('models/model_linear_regression.pkl')

# Prepare data
property_data = pd.DataFrame({
    'prior_tot_appr_val': [250000],
    'prior_bld_val': [150000],
    'prior_land_val': [100000],
    # ... other 21 features
})

# Predict
prediction = model.predict(property_data)
print(f"Predicted value: ${prediction[0]:,.0f}")
```

## 💡 Key Findings

✅ **Linear Regression is optimal** - Property tax assessments follow mathematical formulas, so linear models perfect

✅ **Prior year values are critical** - Historical assessments are the best predictor of current assessments

✅ **98% accuracy achievable** - With proper feature engineering and data cleaning

✅ **Robust across property types** - Works well for commercial, agricultural, and residential properties

## 🎓 What This Demonstrates

✓ **Full ML Pipeline:** Data cleaning → EDA → modeling → evaluation

✓ **Data Quality:** Detected and removed data leakage, handled outliers

✓ **Model Selection:** Tested multiple algorithms, chose best for domain

✓ **Domain Expertise:** Applied property tax knowledge to feature engineering

✓ **Production Mindset:** Saved models, documented process, ready for deployment

## 🛠️ Technologies

- **Python**
- **Pandas** (data manipulation)
- **Scikit-learn** (Linear Regression, preprocessing)
- **XGBoost** (gradient boosting)
- **Matplotlib/Seaborn** (visualization)

## 📈 Model Performance

| Scenario 			                | Accuracy 	    | Typical Error |
|-------------------------------|---------------|---------------|
| Properties <$200k 		        | 98%+ 		      | ±$25k-40k 	  |
| Properties $200k-$500k 	      | 98%+ 		      | ±$40k-60k 	  |
| Properties $500k-$1M 		      | 97%+ 		      | ±$60k-100k 	  |
| Properties >$1M 		          | 96%+ 		      | ±$100k-200k 	|

## 👤 Author Notes

This project demonstrates:
- Understanding of property tax assessment methodology
- ML best practices (data leakage detection, cross-validation)
- Production-ready code and documentation
- Ability to select appropriate algorithms for domain problems

---

**Last Updated:** 2026
