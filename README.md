# EDA-workflow

This project follows a complete **Exploratory Data Analysis (EDA)** workflow to understand the Titanic dataset, check data quality, discover patterns, and generate meaningful insights.

### EDA Flow

```text
Understand the Problem
        ↓
Load the Data
        ↓
Understand the Data
        ↓
Check Data Quality
        ↓
Clean the Data
        ↓
Univariate Analysis
        ↓
Bivariate Analysis
        ↓
Multivariate Analysis
        ↓
Outlier Analysis
        ↓
Feature Engineering
        ↓
Correlation Analysis
        ↓
Final Insights
```

### 1. Understand the Problem

The first step is to clearly define the question we want to answer.

For this project:

> **What factors are related to passenger survival on the Titanic?**

---

### 2. Load the Data

The Titanic dataset is loaded using Seaborn.

```python
df = sns.load_dataset("titanic")
```

The first few records are viewed using:

```python
df.head()
```

---

### 3. Understand the Data

The dataset is explored using:

```python
df.shape
df.columns
df.head()
df.info()
df.describe()
df.dtypes
```

The Titanic dataset contains **891 rows and 15 columns**.

Important columns include:

- `survived` – Survival status
- `pclass` – Passenger class
- `sex` – Gender
- `age` – Age
- `sibsp` – Siblings/spouse
- `parch` – Parents/children
- `fare` – Ticket fare
- `embarked` – Embarkation port
- `alone` – Whether the passenger travelled alone

---

### 4. Check Data Quality

Data quality is checked before performing analysis.

The notebook covers:

- Missing values
- Missing-value percentages
- Missing-value visualization
- Duplicate records
- Data types

Example:

```python
df.isnull().sum()
```

---

### 5. Clean the Data

Missing values are handled based on the nature of the column.

The notebook covers cleaning of:

- `age`
- `embarked`
- `deck`

The objective is to prepare the data for further analysis without unnecessarily removing useful information.

---

### 6. Univariate Analysis

Univariate analysis examines **one variable at a time**.

The notebook analyzes:

- Survival
- Gender
- Passenger class
- Age
- Fare

Common visualizations include:

- Countplot
- Histogram
- KDE plot
- Boxplot

---

### 7. Bivariate Analysis

Bivariate analysis examines the relationship between **two variables**.

The notebook analyzes:

- Gender vs Survival
- Class vs Survival
- Age vs Survival
- Fare vs Survival
- Embarkation vs Survival
- Family Size vs Survival
- Travelling Alone vs Survival

---

### 8. Multivariate Analysis

Multivariate analysis examines relationships involving **multiple variables**.

The notebook covers:

- Gender + Class + Survival
- Age + Class + Survival
- Age + Fare + Survival

These analyses help identify patterns that may not be visible when studying variables individually.

---

### 9. Outlier Analysis

Outlier analysis identifies unusually high or low values.

The notebook uses:

- Boxplots
- IQR (Interquartile Range)

```text
IQR = Q3 - Q1
```

Outliers are investigated rather than automatically removed.

---

### 10. Feature Engineering

New features are created from existing columns.

#### Family Size

```python
df["family_size"] = df["sibsp"] + df["parch"] + 1
```

#### Child / Adult

```python
df["is_child"] = df["age"] < 18
```

These new features are used to study their relationship with survival.

---

### 11. Correlation Analysis

Correlation analysis is used to study relationships between numerical variables.

The notebook uses:

- Correlation
- Heatmap

Correlation values range from:

```text
-1 → Negative relationship
 0 → No linear relationship
+1 → Positive relationship
```

---

### 12. GroupBy Analysis

`groupby()` is used to compare survival rates across different groups.

For example:

```python
df.groupby("sex")["survived"].mean()
```

This helps compare survival rates between categories such as gender and passenger class.

---

### 13. Pivot Table Analysis

A pivot table is used to analyze survival across multiple categories.

```python
pd.pivot_table(
    df,
    values="survived",
    index="sex",
    columns="class",
    aggfunc="mean"
)
```

This provides a clear comparison of survival rates by gender and passenger class.

---

### 14. Final Data Quality Check

After cleaning and feature engineering, the dataset is checked again for missing values.

```python
df.isnull().sum()
```

This confirms whether important missing values still remain.

---

### 15. Final Insights

The final stage is to convert the analysis into meaningful conclusions.

The complete EDA covers:

- Data Understanding
- Data Quality
- Univariate Analysis
- Bivariate Analysis
- Multivariate Analysis
- Outlier Analysis
- Feature Engineering
- Correlation Analysis
- GroupBy Analysis
- Pivot Table Analysis
- Final Insights

### 🎯 EDA Golden Rule

```text
Question
   ↓
Code
   ↓
Visualization
   ↓
Observation
   ↓
Insight
```

> **EDA is not just about creating graphs. It is about understanding the data, identifying patterns, and converting those patterns into meaningful insights.**
