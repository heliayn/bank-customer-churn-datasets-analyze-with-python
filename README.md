# Bank Customer Churn Analysis

Exploratory Data Analysis (EDA) on a bank customer churn dataset, performed with Python, Pandas, and Seaborn. The goal of this project is to explore customer data, clean and prepare it, and visualize patterns that may relate to customer churn.

> **Note:** Code comments and markdown explanations inside the notebook are written in Persian (Farsi).

## Dataset

The dataset (`Customer-Churn-Records.csv`) contains **10,000 records** and **18 features**, including:

- `CreditScore` — customer's credit score
- `Geography` — customer's country (France, Germany, Spain)
- `Gender`
- `Age`
- `Tenure` — number of years as a customer
- `Balance` — account balance
- `NumOfProducts` — number of bank products used
- `HasCrCard` — whether the customer has a credit card
- `IsActiveMember`
- `EstimatedSalary`
- `Exited` — whether the customer churned (target variable)
- `Complain`
- `Satisfaction Score`
- `Card Type` (Diamond, Gold, Silver, Platinum)
- `Point Earned`

## Steps Performed

### 1. Data Loading & Inspection
- Loaded the dataset with Pandas
- Reviewed the first rows and column info (`.head()`, `.info()`)

### 2. Data Cleaning
- Removed irrelevant identifier columns (`RowNumber`, `CustomerId`, `Surname`)
- Checked for missing values across all columns (none found)

### 3. Data Preprocessing
- Encoded `Gender` as a binary variable (Male = 1, Female = 0)
- One-hot encoded categorical columns (`Geography`, `Card Type`), dropping the first category to avoid redundancy
- Standardized numeric columns (`CreditScore`, `Age`, `Balance`, `EstimatedSalary`) using z-score normalization for comparison purposes

### 4. Exploratory Analysis & Visualization
- **Correlation matrix (heatmap):** explored relationships between all numeric and encoded features
- **Distribution plots (histograms):** visualized the distribution of `CreditScore`, `Age`, `Balance`, and `EstimatedSalary`
- **Boxplot:** identified outliers in `CreditScore`
- **Bar charts:** visualized the distribution of `Card Type` and customer `Geography` (country)

## Key Observations
- No missing values were found in the dataset.
- `Complain` and `Exited` show an almost perfect correlation, suggesting complaints are strongly tied to churn.
- `Balance` shows a notable correlation with customers located in Germany.
- `Age` shows a moderate positive correlation with churn (`Exited`).
- A number of low-end outliers were detected in `CreditScore` via boxplot analysis.
- `EstimatedSalary` appears fairly uniformly distributed across customers.

## Tools & Libraries
- Python
- Pandas / NumPy
- Matplotlib / Seaborn

## How to Run
1. Clone this repository
2. Make sure `Customer-Churn-Records.csv` is in the same directory as the notebook
3. Install dependencies:
   ```
   pip install pandas numpy matplotlib seaborn
   ```
4. Open and run the notebook in Jupyter Notebook or JupyterLab

## Future Improvements
- Apply predictive models (e.g., Logistic Regression, Random Forest) to predict customer churn
- Perform deeper outlier treatment rather than only identifying them
- Add feature engineering based on correlation insights (e.g., combining `Complain` and `Satisfaction Score`)

## Author
Feel free to reach out with any questions or suggestions.
helia.nejadian@gmail.com
