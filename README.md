# Heart Disease Prediction - Kaggle Playground Series

A comprehensive machine learning project for predicting heart disease presence using gradient boosting and ensemble models.

**Competition:** [Kaggle Playground Series - Season 6, Episode 2](https://www.kaggle.com/competitions/playground-series-s6e2)

## 🎯 Project Objective

Predict the presence of heart disease in patients using a classification model trained on medical diagnostic data. The competition requires probability predictions (0.0-1.0) for each test sample.

## 📊 Dataset Information

- **Training Samples:** 41,687 records
- **Test Samples:** 10,000+ records  
- **Input Features:** 12 medical and demographic attributes
- **Target Variable:** Binary classification (Disease/No Disease)
- **Class Distribution:** Imbalanced dataset

### Features
The dataset includes numerical and categorical features representing:
- Blood pressure metrics
- Cholesterol levels
- Heart rate measurements
- Medical history indicators
- Demographic information

## 🔧 Models Implemented

### 1. Random Forest (Baseline)
- **Type:** Tree-based ensemble method
- **Advantages:**
  - Distribution-agnostic (no need for transformation)
  - Fast training and inference
  - Good interpretability
  - Minimal feature engineering required
- **Configuration:**
  - n_estimators: 500
  - max_depth: 8
  - min_samples_split: 10
  - Class weights: balanced

### 2. CatBoost (Final Selected Model) ⭐
- **Type:** Advanced gradient boosting framework
- **Advantages:**
  - Superior performance on imbalanced data
  - Native categorical feature handling
  - Class weights for imbalanced datasets
  - Better generalization capability
- **Configuration:**
  - iterations: 900
  - learning_rate: 0.11
  - depth: 4
  - class_weights: [1, 3]
  - l2_leaf_reg: 12

**Selection Rationale:** CatBoost demonstrated superior predictive performance on the validation set and was selected for the final competition submission.

## 📈 Project Pipeline

1. **Data Loading & Preprocessing**
   - Load training and test datasets
   - Normalize column names
   - Handle missing values
   - Encode target variable

2. **Exploratory Data Analysis (EDA)**
   - Distribution analysis for numerical features
   - Categorical feature proportions
   - Outlier detection and visualization
   - Negative value checks
   - Skewness observations

3. **Model Training**
   - Train Random Forest with GridSearchCV
   - Train CatBoost with optimized hyperparameters
   - Validate on held-out test set
   - Compare model performance

4. **Evaluation**
   - Classification report (precision, recall, F1)
   - Confusion matrix analysis
   - Cross-validation scoring

5. **Prediction & Submission**
   - Generate probability predictions on test set
   - Create submission file in required format

## 📁 File Structure

```
playground-series-s6e2
├── README.md                          # This file
├── notebook_project.ipynb             # Main Jupyter notebook with full analysis
├── train.csv                          # Training dataset
├── test.csv                           # Test dataset
```

## 🚀 How to Run

### Prerequisites
```bash
Python >= 3.8
pandas >= 1.0
numpy >= 1.19
scikit-learn >= 0.24
catboost >= 1.0
matplotlib >= 3.3
seaborn >= 0.11
```

### Installation
```bash
# Clone or download the repository
cd playground-series-s6e2

# Install required packages
pip install pandas numpy scikit-learn catboost matplotlib seaborn
```

### Execution
```bash
# Option 1: Run the Jupyter notebook
jupyter notebook notebook_project.ipynb

# Option 2: Extract and run specific cells
# The notebook is structured with clear sections for:
# - EDA
# - Random Forest model training
# - CatBoost model training
# - Prediction generation
```

### Generate Predictions
The main notebook will automatically:
1. Train both models
2. Evaluate performance
3. Generate probability predictions on test set
4. Save `submission.csv` with predictions

## 📋 Submission Format

The final submission file contains predictions in the required format:

```csv
id,Heart Disease
630000,0.2345
630001,0.7891
630002,0.1234
...
```

- **id:** Test sample identifier
- **Heart Disease:** Predicted probability of disease presence (0.0-1.0)

## 🎓 Key Learnings

- **Class Imbalance Handling:** Using class weights in CatBoost effectively handles imbalanced data
- **Gradient Boosting:** CatBoost's normalized splits and ordered boosting provide superior performance
- **Hyperparameter Optimization:** Validation on appropriate train-test splits crucial for model selection
- **Probability Calibration:** CatBoost provides well-calibrated probability predictions essential for ranking-based competitions

## 📊 Model Comparison Summary

| Metric | Random Forest | CatBoost |
|--------|--------------|----------|
| F1 Score | ~0.78 | ~0.82 |
| Precision | ~0.75 | ~0.80 |
| Recall | ~0.81 | ~0.85 |
| Generalization | Good | Excellent |
| Training Time | Fast | Moderate |

**Result:** CatBoost selected for superior predictive performance and generalization.

## 🔍 Feature Analysis

The model uses 12 features from the base dataset. No additional feature engineering was performed, as tree-based models handle feature interactions naturally.

**Distribution Patterns:**
- max_hr: Left-skewed
- st_depression: Right-skewed  
- bp: Right-skewed
- Other features: Approximately normal

## 📝 Notes

- **No Preprocessing Required:** Tree-based models handle skewed distributions without transformation
- **Categorical Features:** CatBoost natively handles categorical features without explicit encoding
- **Imbalance Strategy:** Class weights adjusted to penalize misclassification of minority class
- **Validation:** 95-5 train-test split to maximize training data for final model

## 🔗 References

- [CatBoost Documentation](https://catboost.ai/)
- [Scikit-learn RandomForest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)
- [Kaggle Playground Series](https://www.kaggle.com/competitions/playground-series-s6e2)

## 📧 Contact & Attribution

This project is part of the Kaggle Playground Series Season 6 Episode 2 competition. 

## 📜 License

This project is provided as-is for educational and competition purposes.

---

**Status:** ✅ Complete - Submission ready for Kaggle competition
