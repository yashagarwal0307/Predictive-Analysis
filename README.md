# Predictive-analysis
Predicted solar efficiency using Machine learning in Zelestra X AWS ML Ascend Challenge - 2nd Edition 
Here is a detailed and professional **README** explaining your approach to the solar panel efficiency prediction task:

---

# Solar Panel Efficiency Prediction

## 📌 Problem Statement

The goal of this project was to build a predictive model to estimate **solar panel efficiency** using the provided training and test datasets. The dataset included various environmental and operational features affecting the efficiency of solar panels.

---

## 🧰 Tools & Libraries

* **Python** (pandas, numpy, scikit-learn)
* **Machine Learning Models**: XGBoost, Random Forest, SVR, CatBoost, Gradient Boosting, ELM (Extreme Learning Machine)
* **Ensembling Techniques**: Voting Regressor
* **Visualization**: matplotlib, seaborn (optional for EDA)

---

## ⚙️ Approach

### 1. **Data Loading & Preprocessing**

* The datasets were read using **pandas**.
* Missing values in the dataset were handled using:

  * **Mean imputation** for general missing values.
  * **Median imputation** for specific engineered features (detailed below).

### 2. **Feature Engineering**

* **Data Type Conversion**:
  Columns such as `humidity`, `wind_speed`, and `pressure` were originally in string format. These were parsed and converted into appropriate **float** values.

* **Range Filtering & Imputation**:
  For selected features:

  * **`irradiance`** was constrained to a realistic range \[0, 1500].
  * **`humidity`** was clipped to \[0, 100].
  * **`soiling_ratio`** was restricted to \[0, 1].

  Values outside these ranges were treated as outliers and replaced with the **median** of valid entries.

### 3. **Feature Selection**

To identify the most relevant predictors:

* **Mutual Information (MI)** scores were calculated.
* **Pearson Correlation** was analyzed.
* **Variance Inflation Factor (VIF)** was used to detect multicollinearity and remove redundant features.

This step helped in reducing noise and dimensionality, and in improving model performance.

### 4. **Data Splitting & Normalization**

* The preprocessed training data was split into:

  * **Training set** (70%)
  * **Validation set** (30%)
* Features were normalized using **StandardScaler** from scikit-learn.

### 5. **Model Training**

Several regression models were trained and compared:

| Model                              | Description                                                       |
| ---------------------------------- | ----------------------------------------------------------------- |
| **XGBoost**                        | Gradient boosting tree model optimized for speed and performance. |
| **Random Forest**                  | Bagging ensemble of decision trees.                               |
| **SVR**                            | Support Vector Regressor with kernel trick.                       |
| **CatBoost**                       | Gradient boosting with categorical handling and regularization.   |
| **Gradient Boosting**              | Traditional scikit-learn implementation of boosting.              |
| **ELM (Extreme Learning Machine)** | Single hidden-layer feedforward network.                          |

An **ensemble model** was built using a **Voting Regressor**, combining predictions from the top-performing models (XGBoost, Random Forest, SVR, and CatBoost) to achieve better generalization.

### 6. **Test Data Prediction**

The test data was preprocessed using the same pipeline as the training data to ensure consistency. Predictions were made using the **voting ensemble model**, which gave the best performance.

---

## 🏆 Results

* **Best Model**: Voting Regressor (Ensemble)
* **Validation Score**: **89.79**


---

## 📈 Conclusion

The project successfully demonstrated a robust machine learning pipeline for predicting solar panel efficiency. Key takeaways include:

* Importance of data cleaning and feature transformation
* Effective use of feature selection methods
* Power of ensemble models for regression tasks
* Consistent preprocessing pipeline for both train and test data

---


Let me know if you want a version of this as a downloadable Markdown file or want it customized for GitHub.
