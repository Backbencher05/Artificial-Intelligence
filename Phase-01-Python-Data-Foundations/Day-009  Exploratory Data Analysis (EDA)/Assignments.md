# Day 009 Assignment (My Answers)

---

# Q1. What is Exploratory Data Analysis (EDA)? Why is it performed before machine learning?

**Exploratory Data Analysis (EDA)** is the process of **understanding, exploring, and analyzing a dataset** before building a machine learning model.

The goal of EDA is not to train a model but to answer questions like:

* What does the data look like?
* Are there missing values?
* Are there outliers?
* Are the features related?
* Is the data balanced?
* Are there any unexpected patterns?

EDA helps us understand the story behind the data before making modeling decisions.

---

## Why is EDA performed before Machine Learning?

A machine learning model learns patterns from the data.

If we don't understand the data first, we risk training a model on:

* Incorrect data
* Biased data
* Noisy data
* Poor-quality data

EDA helps us identify and fix these issues before training.

---

### Benefits of EDA

### 1. Understand Data Structure

We learn:

* Number of rows
* Number of columns
* Data types
* Feature distributions

---

### 2. Detect Data Quality Issues

EDA helps identify:

* Missing values
* Duplicate records
* Outliers
* Invalid values

---

### 3. Discover Relationships

For example:

```text id="e0j3cw"
Experience ↑
      ↓
Salary ↑
```

A scatter plot may reveal this relationship.

---

### 4. Improve Feature Selection

EDA helps determine:

* Which features are useful
* Which features are redundant
* Which features require transformation

---

## Summary

EDA is performed before machine learning because understanding the data is essential for building accurate, reliable, and trustworthy AI models.

---

# Q2. Explain the difference between Data Cleaning vs EDA.

Although they are closely related, they have different goals.

---

## Data Cleaning

Data Cleaning focuses on **fixing problems in the dataset**.

Typical tasks include:

* Removing duplicates
* Handling missing values
* Correcting invalid values
* Fixing data types
* Standardizing formats

Example:

```text id="jxwj03"
Age = 250
```

This is clearly invalid and needs correction.

The goal is to make the data clean and consistent.

---

## Exploratory Data Analysis (EDA)

EDA focuses on **understanding the data**.

Typical tasks include:

* Visualizing distributions
* Finding correlations
* Identifying trends
* Detecting outliers
* Understanding feature relationships

Example:

Using a scatter plot to observe:

```text id="dpycfk"
Experience
      ↓
Salary
```

---

## Simple Analogy

Imagine buying a used car.

### Data Cleaning

Repair the car.

* Fix brakes
* Change tires
* Repair engine

---

### EDA

Inspect the car.

* Check mileage
* Test drive
* Look for damage
* Understand its condition

---

## Summary

| Data Cleaning       | EDA                              |
| ------------------- | -------------------------------- |
| Fixes data problems | Explores and understands data    |
| Corrects errors     | Finds patterns and relationships |
| Makes data usable   | Helps make modeling decisions    |

---

# Q3. What kind of insights can histograms, scatter plots, and correlation matrices provide?

Each visualization answers a different question.

---

## Histogram

A histogram shows **how a numerical feature is distributed**.

Example:

Salary distribution.

It helps us understand:

* Distribution shape
* Skewness
* Spread
* Outliers

Example:

```text id="dbxxcj"
Most salaries

40K–60K

One salary

10 Million
```

The unusual value immediately stands out.

---

## Scatter Plot

A scatter plot shows the relationship between two numerical variables.

Example:

```text id="5zhgkx"
Experience vs Salary
```

It helps us identify:

* Positive correlation
* Negative correlation
* Clusters
* Outliers
* Trends

---

## Correlation Matrix

A correlation matrix measures how strongly numerical features are related.

Example:

| Feature    | Salary |
| ---------- | ------ |
| Age        | 0.65   |
| Experience | 0.92   |

Interpretation:

Experience has a stronger relationship with salary than age.

This helps identify useful features for machine learning.

---

## Summary

| Visualization      | Insight                                                     |
| ------------------ | ----------------------------------------------------------- |
| Histogram          | Distribution of one feature                                 |
| Scatter Plot       | Relationship between two features                           |
| Correlation Matrix | Strength of relationships among multiple numerical features |

---

# Q4. Why is correlation useful? Why should we remember that correlation does not imply causation?

Correlation measures **how strongly two variables move together**.

If one variable increases and another also tends to increase, they have a positive correlation.

Example:

```text id="80rkof"
Experience ↑

Salary ↑
```

This is a positive correlation.

---

## Why Correlation is Useful

Correlation helps us:

* Select useful features
* Detect redundant features
* Understand relationships
* Improve model design

Example:

If:

```text id="26x5p4"
Experience → Salary

Correlation = 0.92
```

Experience is likely an important feature.

---

## Correlation Does Not Imply Causation

Just because two variables are related does **not** mean one causes the other.

Example:

Ice cream sales increase during summer.

Drowning incidents also increase during summer.

Does eating ice cream cause drowning?

No.

The actual cause is:

```text id="26kh4l"
Hot Weather
```

Hot weather leads to:

* More ice cream sales
* More people swimming

Both variables increase together because of a third factor.

---

### AI Perspective

Machine learning models detect patterns, not causes.

A model might find:

```text id="t7vyeg"
Department
↓

Higher Salary
```

This does not prove that the department itself causes higher salaries. Other factors, such as experience, skills, or job role, may influence both.

Understanding this prevents us from making incorrect conclusions based solely on correlation.

---

## Summary

Correlation is useful for discovering relationships, but additional analysis and domain knowledge are needed before claiming cause-and-effect.

---

# Q5. Suppose you receive a dataset containing:

```text id="4gf1y8"
Age
Salary
Experience
Department
```

Describe your complete EDA workflow before training an AI model.

I would follow a structured workflow to understand the dataset thoroughly before modeling.

---

## Step 1: Load the Dataset

```python id="djjy38"
import pandas as pd

df = pd.read_csv("employees.csv")
```

---

## Step 2: Inspect the Data

```python id="3d8w5g"
df.head()
df.info()
df.shape
```

Purpose:

* Verify successful loading.
* Check column names.
* Review data types and dataset size.

---

## Step 3: Generate Summary Statistics

```python id="2o3uyh"
df.describe()
```

Purpose:

Understand:

* Mean
* Median
* Minimum
* Maximum
* Standard deviation

This helps detect unusual values.

---

## Step 4: Check Missing Values

```python id="j2gt6c"
df.isnull().sum()
```

Purpose:

Identify columns requiring data cleaning.

---

## Step 5: Check Duplicate Records

```python id="r1vf2m"
df.duplicated().sum()
```

Purpose:

Ensure each observation is unique unless duplicates are expected.

---

## Step 6: Visualize Numerical Features

Create histograms for:

* Age
* Salary
* Experience

Purpose:

* Understand distributions.
* Detect skewness.
* Identify potential outliers.

---

## Step 7: Analyze Relationships

Create scatter plots:

```text id="8o2k8m"
Experience vs Salary

Age vs Salary

Age vs Experience
```

Purpose:

Understand relationships between numerical features.

---

## Step 8: Analyze Categorical Features

```python id="zud7mb"
df["Department"].value_counts()
```

Purpose:

Understand:

* Department distribution.
* Class balance.

---

## Step 9: Calculate Correlations

```python id="axp0vd"
df.corr(numeric_only=True)
```

Purpose:

Identify strong relationships between numerical features.

---

## Step 10: Summarize Findings

Before training the model, I would document:

* Missing values
* Outliers
* Feature distributions
* Strong correlations
* Potential data quality issues
* Features that may require encoding or scaling

This provides a clear understanding of the dataset and guides the next steps in preprocessing and feature engineering.

---

## Complete EDA Workflow

```text id="u6vuy9"
Load Dataset
       ↓
Inspect (head, info, shape)
       ↓
Summary Statistics (describe)
       ↓
Check Missing Values
       ↓
Check Duplicates
       ↓
Histograms
       ↓
Scatter Plots
       ↓
Analyze Categorical Features
       ↓
Correlation Matrix
       ↓
Document Insights
       ↓
Feature Engineering
       ↓
Train Machine Learning Model
```

---

# Key Learning from Day 009

By Day 009, you've completed the journey from loading raw data to understanding it deeply before modeling.

```text id="3lwf1n"
Raw Data
      ↓
Pandas DataFrame
      ↓
Data Cleaning
      ↓
Exploratory Data Analysis (EDA)
      ↓
Understand Patterns
      ↓
Feature Engineering
      ↓
Machine Learning Model
```

The biggest takeaway from today is that **EDA is about asking questions before asking the model to learn**. A good AI engineer doesn't rush into training algorithms—they first explore the data, understand its strengths and weaknesses, and use those insights to build a more accurate and reliable AI system.
