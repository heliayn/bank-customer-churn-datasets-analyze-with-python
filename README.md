# Bank Customer Churn Analysis | Exploratory Data Analysis (EDA)

An undergraduate-level Python/Jupyter project investigating how demographic, financial, and behavioral customer attributes are associated with customer churn (`Exited`). The project is **exploratory and descriptive**, not a deployed prediction system. Notebook explanations are primarily written in Persian.

## Research Question and Scope

Which characteristics of bank customers are associated with churn, and which customer groups warrant further investigation? This project inspects, prepares, visualizes, and compares customer records; it also discusses practical implications and the limitations of observational data.

## Dataset

- **File:** `Customer-Churn-Records.csv`
- **Size:** 10,000 customer records and 18 original columns (including identifiers and the target).
- **Target:** `Exited` (`0`: retained, `1`: churned).
- **Overall churn rate:** 20.38% (2,038 / 10,000).
- **Fields:** `RowNumber`, `CustomerId`, `Surname`, `CreditScore`, `Geography`, `Gender`, `Age`, `Tenure`, `Balance`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `EstimatedSalary`, `Exited`, `Complain`, `Satisfaction Score`, `Card Type`, `Point Earned`.
- **Countries:** France, Germany, Spain.
- **Card types:** DIAMOND, GOLD, PLATINUM, SILVER.

The CSV is included with the project. Its original publication details are not established in these files; add the original dataset URL and license if known.

## Files

| File | Purpose |
| --- | --- |
| `data_set_analyze(1).ipynb` | Main Jupyter notebook containing data preparation, EDA, plots, churn-rate comparisons, outlier analysis, and interpretation. |
| `Customer-Churn-Records.csv` | Input dataset. |
| `README.md` | Project overview and run instructions. |
| `Bank_Churn_Project_Guide_FA.docx` | Persian academic introduction and project guidance for the instructor. |

## Workflow in the Notebook

1. **Load and inspect:** read the CSV with Pandas; inspect sample rows, shape, types, and summary statistics.
2. **Clean:** drop `RowNumber`, `CustomerId`, and `Surname`; check missing values (none reported in the CSV).
3. **Encode categorical variables:** map `Gender` to `Female=0`, `Male=1`; one-hot encode `Geography` and `Card Type` with `drop_first=True`.
4. **Examine associations:** plot a correlation heatmap; inspect the unusually high `Complain`–`Exited` association and cross-tabulate complaints versus churn.
5. **Visualize distributions:** generate counts, histograms, and comparative boxplots for customer features and churn status.
6. **Compare churn rates:** group by gender, country, card type, credit-card ownership, activity status, number of products, and satisfaction score; show counts, churned customers, and rates.
7. **Find potential outliers:** compute Q1, Q3, IQR, detection bounds, and outlier counts; plot feature boxplots and show sample outlier records.
8. **Interpret and conclude:** summarize observed patterns, managerial hypotheses, and limitations.

The notebook also contains explanatory text about Chi-Square and Mann–Whitney U tests. Consult the notebook itself for the currently implemented code and outputs; this README does not report results from those tests.

## Selected Descriptive Findings

| Customer group | Customers | Churn rate |
| --- | ---: | ---: |
| **Overall** | 10,000 | 20.38% |
| France | 5,014 | 16.17% |
| Germany | 2,509 | 32.44% |
| Spain | 2,477 | 16.67% |
| Female | 4,543 | 25.07% |
| Male | 5,457 | 16.47% |
| Inactive (`IsActiveMember=0`) | 4,849 | 26.87% |
| Active (`IsActiveMember=1`) | 5,151 | 14.27% |
| 1 product | 5,084 | 27.71% |
| 2 products | 4,590 | 7.60% |
| 3 products | 266 | 82.71% |
| 4 products | 60 | 100.00% |

- `Complain` and `Exited` are almost perfectly associated (approximately **r = 0.9957**). The source data do **not** establish when complaints were recorded relative to churn or whether these fields were generated independently. Treat this relationship cautiously; it does not demonstrate causation.
- Age has a positive association with churn; activity has a negative association in the notebook's correlation analysis.
- Some numeric features have IQR-defined outliers. An outlier is not automatically an erroneous record, and the notebook does not recommend removing all outliers without review.
- Group comparisons are **descriptive**, not causal; very small groups (for example, customers with four products) need special care.

## Requirements and Execution

- Python 3 with Jupyter support, or VS Code with the **Python** and **Jupyter** extensions.
- Libraries: Pandas, NumPy, Matplotlib, Seaborn, SciPy, and a Jupyter kernel (`ipykernel`).

Install dependencies **in the same Python environment as your notebook kernel**:

```bash
python -m pip install pandas numpy matplotlib seaborn scipy ipykernel
```

In VS Code, open `data_set_analyze(1).ipynb`, select the correct **Jupyter kernel** at the top right, and run cells **from top to bottom**. Keep `Customer-Churn-Records.csv` in the notebook's working directory. If a relative CSV path fails, verify the working directory or update the `pd.read_csv(...)` path.

If Pylance shows a type warning, distinguish it from actual notebook execution errors; the Jupyter kernel and VS Code interpreter should point to the same Python installation.

## Limitations

- Cross-sectional observational data cannot establish causal effects.
- The timestamps and origins of `Complain` and `Exited` are unspecified; the extremely high association warrants source verification and may produce target leakage in a predictive setting.
- Representativeness, the original data collection period, and dataset provenance are not documented here.
- Group rates should be evaluated together with group sizes.
- The notebook focuses on EDA; no validated, deployed churn-prediction model is included.

## Future Work

- Obtain time-stamped complaint and churn events and verify dataset provenance.
- Explore interactions among age, account balance, activity, and products.
- Fit and evaluate predictive models only after addressing potential leakage and using appropriate train/test splits, class-imbalance-aware metrics, and out-of-sample evaluation.
- Test customer-retention interventions empirically before asserting business impact.

## Project Documentation

The accompanying Persian Word document presents the problem statement, motivation, objectives, data dictionary, methods, observed findings, practical recommendations, limitations, and execution guidance in a format suitable for an undergraduate university instructor.
