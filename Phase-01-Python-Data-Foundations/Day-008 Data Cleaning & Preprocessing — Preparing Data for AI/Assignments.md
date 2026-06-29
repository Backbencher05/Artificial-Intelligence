# Day 008 Assignment (My Answers)

---

# Q1. Why is data cleaning considered one of the most important stages in AI projects?

Data cleaning is one of the most important stages because **an AI model can only learn from the quality of the data it receives**.

A common saying in AI is:

> **"Garbage In, Garbage Out (GIGO)."**

If the data contains errors, duplicates, missing values, or incorrect formats, the model will learn incorrect patterns and produce unreliable predictions.

---

## Why Data Cleaning Matters

### 1. Improves Model Accuracy

Clean data helps the model learn meaningful relationships instead of noise.

Example:

```text
Experience → Salary
```

is a useful relationship.

But if many salary values are incorrect, the model may learn the wrong pattern.

---

### 2. Removes Noise

Real-world datasets often contain:

* Missing values
* Typographical errors
* Duplicate records
* Outliers
* Inconsistent formatting

Cleaning removes these issues.

---

### 3. Prevents Biased Learning

Suppose a customer appears five times due to duplicate records.

The model may incorrectly give more importance to that customer, introducing bias.

---

### 4. Makes Data Consistent

Example:

```text
IT
Information Technology
I.T.
```

All represent the same department but appear differently.

Cleaning standardizes such values.

---

### AI Perspective

In many real-world AI projects:

* Data Collection → **20%**
* Data Cleaning & Preparation → **60–80%**
* Model Training → **20–40%**

This shows that most of an AI engineer's effort is spent preparing high-quality data rather than building models.

---

## Summary

Data cleaning ensures that the model learns from accurate, consistent, and reliable data, leading to better performance and trustworthy predictions.

---

# Q2. What are missing values (NaN)? What are some common ways to handle them?

A missing value, represented as **NaN (Not a Number)** in Pandas, indicates that no value is available for a particular field.

Example:

| CustomerID | Age | Salary |
| ---------- | --: | -----: |
| 101        |  25 |  50000 |
| 102        | NaN |  60000 |

Here, the age of Customer 102 is unknown.

---

## Why Missing Values Matter

Machine learning models generally cannot process missing values directly.

Before training, these values must be handled appropriately.

---

## Common Ways to Handle Missing Values

### 1. Remove the Rows

If only a few rows contain missing values:

```python
df.dropna()
```

Suitable when very little data is lost.

---

### 2. Fill with Mean

Useful for numerical columns.

Example:

```text
Ages:

20
25
30
NaN
35
```

Mean:

```text
27.5
```

Replace NaN with 27.5.

---

### 3. Fill with Median

Preferred when data contains outliers.

Example:

```text
20
25
27
28
500
```

The median is more representative than the mean.

---

### 4. Fill with Mode

Useful for categorical data.

Example:

```text
Department

IT
HR
IT
NaN
```

Replace NaN with:

```text
IT
```

because it is the most frequent value.

---

### 5. Predict Missing Values

Advanced techniques use machine learning models to estimate missing values based on other features.

---

## Summary

Missing values should never be ignored. Depending on the dataset and context, we may remove them or replace them using statistical or predictive methods.

---

# Q3. Why are duplicate records problematic? When might duplicates actually be valid?

Duplicate records occur when the same data appears more than once.

Example:

| CustomerID | Age | Salary |
| ---------- | --: | -----: |
| 103        |  30 |  70000 |
| 103        |  30 |  70000 |

---

## Why Duplicates Are Problematic

### 1. Bias the Model

If one customer appears multiple times, the model may give that customer more influence than others.

---

### 2. Distort Statistics

Duplicates can affect:

* Average salary
* Department counts
* Customer distribution

leading to misleading analysis.

---

### 3. Waste Storage and Processing Time

More duplicate data means unnecessary memory usage and slower computations.

---

## When Duplicates Are Valid

Not every duplicate is an error.

Examples:

### Banking

A customer can make multiple transactions.

| CustomerID | Transaction |
| ---------- | ----------- |
| 101        | Deposit     |
| 101        | Withdrawal  |

These are valid because each row represents a different event.

---

### E-commerce

A customer may place multiple orders.

---

### Hospital

A patient can have multiple visits.

---

### Key Rule

Duplicates are problematic only when **the rows are supposed to represent unique entities** but appear multiple times accidentally.

---

## Summary

Duplicates should be removed only after understanding the meaning of each row in the dataset.

---

# Q4. Why is checking data types important before training an AI model?

Each feature must have the correct data type because machine learning algorithms expect data in a specific format.

Example:

```text
Age → Integer
Salary → Float
Department → Category/String
```

---

## Problems with Incorrect Data Types

Suppose:

```text
Salary

"50000"
"60000"
"70000"
```

If Salary is stored as text (object) instead of numeric:

* We cannot calculate averages.
* Mathematical operations will fail.
* Models cannot train correctly.

---

## Another Example

```text
Age

"Twenty Five"
```

This should be an integer, not a string.

---

## AI Perspective

Checking data types helps ensure:

* Numerical features are truly numeric.
* Categorical features can be encoded correctly.
* Dates are parsed properly.
* No unexpected object columns remain.

---

## Common Pandas Check

```python
df.info()
```

This quickly shows:

* Data types
* Missing values
* Column information

---

## Summary

Correct data types ensure that data can be processed, transformed, and understood correctly by machine learning algorithms.

---

# Q5. Suppose you receive this dataset:

| CustomerID | Age | Salary | Department |
| ---------- | --: | -----: | ---------- |
| 101        |  25 |  50000 | IT         |
| 102        | NaN |  60000 | HR         |
| 103        | 250 |  70000 | Sales      |
| 103        | 250 |  70000 | Sales      |

Describe, step by step, how you would clean this dataset before using it in a machine learning model.

### Step 1: Load the Data

```python
import pandas as pd

df = pd.read_csv("customers.csv")
```

---

### Step 2: Inspect the Dataset

```python
df.head()
df.info()
df.shape
```

Purpose:

* Verify successful loading.
* Check data types.
* Understand the dataset structure.

---

### Step 3: Handle Missing Values

Age contains:

```text
NaN
```

First, I would investigate why it is missing.

If only one value is missing and the dataset is large, I would replace it with the median age because age can contain outliers.

Example:

```python
df["Age"] = df["Age"].fillna(df["Age"].median())
```

---

### Step 4: Detect Invalid Values

Age:

```text
250
```

This is almost certainly invalid for a customer dataset.

I would:

* Verify it against the source system if possible.
* If it is a data entry error and cannot be corrected, treat it as missing and then impute it.

Example:

```python
df.loc[df["Age"] > 120, "Age"] = pd.NA
df["Age"] = df["Age"].fillna(df["Age"].median())
```

---

### Step 5: Remove Duplicate Records

The last two rows are identical.

I would remove duplicates:

```python
df.drop_duplicates(inplace=True)
```

This prevents one customer from being counted twice.

---

### Step 6: Verify Data Types

Using:

```python
df.info()
```

Ensure:

* CustomerID → Integer
* Age → Numeric
* Salary → Numeric
* Department → Category/String

---

### Step 7: Validate the Cleaned Dataset

Finally, I would check:

```python
df.describe()
df.isnull().sum()
df.shape
```

to confirm:

* No missing values remain.
* No duplicate records remain.
* No unrealistic ages remain.
* Numerical columns have sensible statistics.

---

## Final Cleaning Workflow

```text
Load Dataset
        ↓
Inspect (head, info, shape)
        ↓
Handle Missing Values
        ↓
Detect & Fix Invalid Values
        ↓
Remove Duplicates
        ↓
Verify Data Types
        ↓
Validate Final Dataset
        ↓
Ready for Feature Engineering and Model Training
```

---

# Key Learning from Day 008

By Day 008, the AI workflow has become much clearer:

```text
Raw Data
      ↓
Pandas DataFrame
      ↓
Inspect Data
      ↓
Clean Data
      ↓
Handle Missing Values
      ↓
Remove Duplicates
      ↓
Validate Data Types
      ↓
Feature Engineering
      ↓
Train Machine Learning Model
```

The most important lesson from today is that **a machine learning model is only as good as the data it receives**. Before thinking about algorithms or accuracy, an AI engineer must ensure the dataset is clean, consistent, and trustworthy. This data-first mindset is what separates robust AI systems from unreliable ones.
