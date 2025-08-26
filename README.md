# 🔍 Distributed Credit Risk Prediction Analysis

## 📖 Project Overview
This project tackles the challenge of predicting customer credit scores ("Good", "Standard", "Poor") based on financial behavior patterns. Leveraging a dataset of 100,000 records and 28 features, the workflow encompasses rigorous **data cleaning**, **exploratory data analysis**, **machine learning model development**, and a **high-performance distributed computing** implementation.

**Research Question:** "How can we predict customer credit scores using financial behavior patterns and distributed data analysis?"

## 📊 Dataset
**Source:** [Credit Score Classification Dataset on Kaggle](https://www.kaggle.com/datasets/parisrohan/credit-score-classification)
- **Size:** 100,000 records, 28 features
- **Key Features:** `Annual_Income`, `Num_Credit_Card`, `Outstanding_Debt`, `Credit_Utilization_Ratio`, `Payment_Behaviour`, `Credit_History_Age`, `Credit_Score` (Target Variable)

> **Note:** Due to Kaggle's terms of use, the raw dataset is not included in this repo. Please download the `train.csv` file from the source link above and place it in the `data/raw/` directory to run the code.

## 🛠️ Tech Stack
- **Languages:** R 
- **Libraries & Frameworks:** Pandas, NumPy, Scikit-learn, XGBoost, PySpark, Matplotlib, Seaborn
- **Platforms:** Hadoop, Jupyter Notebook, Git
- **Paradigms:** Distributed Computing, Machine Learning, Predictive Analytics

## 📁 Project Structure
## 🔧 Methodology & Results

### 1. Data Cleaning & Preprocessing
Implemented a novel **customer-centric cleaning framework** (grouped by `Customer_ID`) to ensure temporal consistency across records.
- **Handled Missing Values:** Imputed `Occupation` and `Name` using the most frequent value per customer.
- **Fixed Data Types:** Converted text-based `Credit_History_Age` (e.g., "22 Years and 1 Months") to a numeric value (total months).
- **Capped Outliers:** Limited illogical values (e.g., `Num_Credit_Card` ≤ 20, `Age` between 18-100).
- **Standardized Formats:** Removed special characters from financial columns and normalized categorical variables like `Payment_Behaviour`.

### 2. Exploratory Data Analysis (EDA)
- Discovered a significant **class imbalance** in the target variable: "Standard" (53.2%), "Poor" (29.0%), "Good" (17.8%).
- Identified strong **correlations**: `Outstanding_Debt` vs. `Annual_Income` (+0.33), `Interest_Rate` vs. `Num_of_Loan` (+0.46).
- **Key Insights:**
  - Customers with "Poor" scores had significantly higher `Credit_Utilization_Ratio` (avg 42% vs. 28% for "Good").
  - 62% of "Poor" scores were associated with **"High Spent, Large Value Payments"** behavior.
  - Longer credit history was a strong indicator of a "Good" score (22.1 yrs vs. 18.3 yrs for "Poor").

### 3. Machine Learning Modeling
- **Algorithms:** XGBoost (R) and Random Forest (Python - tuned for comparison).
- **Class Handling:** Applied upsampling to balance the minority classes ("Poor", "Good").
- **Feature Engineering:** Created powerful new features like `Debt_to_Income_Ratio` and `Payment_Stability`.
- **Results:**
  | Model | Accuracy | Sensitivity (Poor) | Specificity (Good) | Top Features |
  | :--- | :--- | :--- | :--- | :--- |
  | **XGBoost (R)** | 69.6% | 46.85% | 91.57% | Credit_Utilization_Ratio, Payment_Behaviour |
  | **Random Forest (Python)** | **80.2%** | **65.2%** | - | Outstanding_Debt, Credit_History_Age |

### 4. Distributed Computing Implementation
- Built a **distributed processing pipeline** using PySpark on a Hadoop cluster to handle the 100,000-record dataset efficiently.
- Split data into chunks and processed them in parallel, achieving a **40% reduction in processing time**.
- Mapped customers into segmented risk profiles: **Low (34%), Medium (33%), High (33%) Risk**.

## 📈 Key Findings
- The most important predictors of credit score were **`Credit_Utilization_Ratio` (28%)**, **`Payment_Behaviour` (19%)**, and **`Outstanding_Debt` (15%)**.
- **Random Forest** outperformed XGBoost for this specific task, demonstrating better handling of class imbalance.
- Distributed computing (**PySpark & Hadoop**) is highly effective for scaling risk analysis on large financial datasets.

## 🔮 Future Work
- Experiment with advanced sampling techniques (e.g., SMOTE) to improve sensitivity for the "Poor" class.
- Develop an API wrapper for the `predict_credit_score()` function for real-time deployment.
- Incorporate time-series analysis for more dynamic risk profiling.
- Explore deep learning models for enhanced predictive accuracy.

## 👨‍💻 Developer
**Nazeeb Ullah**
- MSc Data Science & Analytics | Economist
- [LinkedIn](https://www.linkedin.com/in/nazeeb-ullah-a812a3105)
- [GitHub](https://github.com/nazeebullah)

---

*This project was completed as part of the CSS811 Distributed Data Analysis module at Brunel University London.*
