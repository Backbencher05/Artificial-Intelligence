# Day 006 Assignment (My Answers)

---

# Q1. Why is data visualization important in AI projects?

Data visualization helps us **understand the data before building a model**.

An AI model can only learn patterns that exist in the data. If we don't understand the data, we may train a model on incorrect, incomplete, or misleading information.

Visualization helps us:

### 1. Understand Data Distribution

We can see:

* How values are spread
* Whether data is balanced
* Whether data is skewed

---

### 2. Detect Outliers

Visualizations quickly reveal unusual values that may affect model performance.

Example:

```text
Most salaries: 30K - 100K

One salary: 10 Million
```

This suspicious value becomes obvious in a graph.

---

### 3. Discover Relationships

We can identify patterns such as:

```text
More Experience
        ↓
Higher Salary
```

before training any model.

---

### 4. Find Data Quality Issues

Visualizations often reveal:

* Missing values
* Incorrect entries
* Duplicate records
* Unexpected distributions

---

### 5. Improve Decision Making

Visualization helps answer:

> "Should I clean this data?"

> "Should I remove outliers?"

> "Should I engineer new features?"

before expensive model training begins.

---

## Summary

Data visualization turns raw numbers into insights, allowing AI engineers to understand, validate, and improve data before building models.

---

# Q2. What kind of information is best represented using:

## A. Line Plot

A line plot is best for showing:

### Trends over time

Examples:

* Stock prices
* Temperature changes
* Website traffic
* Model loss during training

Example:

```text
Day 1 → 100 users
Day 2 → 120 users
Day 3 → 150 users
```

Line plots help us see whether values are increasing, decreasing, or remaining stable.

---

## B. Bar Chart

A bar chart is best for comparing categories.

Examples:

* Sales by product
* Students by department
* Employees by team

Example:

```text
Python     → 80 students
Java       → 60 students
JavaScript → 70 students
```

Bar charts make category comparisons easy.

---

## C. Histogram

A histogram is best for understanding data distribution.

Examples:

* Age distribution
* Salary distribution
* Height distribution

Instead of showing individual values, it groups values into ranges (bins).

Example:

```text
20-30 years → 50 people
30-40 years → 70 people
40-50 years → 30 people
```

Histograms reveal:

* Skewness
* Spread
* Outliers
* Distribution shape

---

## D. Scatter Plot

A scatter plot is best for understanding relationships between two numerical variables.

Example:

```text
Experience vs Salary
```

Each point represents one observation.

Scatter plots help identify:

* Correlations
* Clusters
* Trends
* Outliers

---

## Summary

| Visualization | Best For                                |
| ------------- | --------------------------------------- |
| Line Plot     | Trends over time                        |
| Bar Chart     | Comparing categories                    |
| Histogram     | Understanding distributions             |
| Scatter Plot  | Finding relationships between variables |

---

# Q3. Why do AI engineers often visualize data before training a model?

Because training a model without understanding the data is risky.

A model learns patterns from the data it receives.

If the data contains:

* Errors
* Missing values
* Outliers
* Imbalances

the model may learn incorrect patterns.

---

### Visualization Helps Answer Important Questions

#### Is the data clean?

```text
Unexpected values?
Missing values?
```

---

#### Is the data balanced?

Example:

```text
95% Cats
5% Dogs
```

A model trained on this dataset may become biased.

---

#### Are features useful?

Example:

```text
Experience ↑
Salary ↑
```

A scatter plot might reveal a strong relationship.

---

#### Are there outliers?

Example:

```text
Experience = 5 years
Salary = 50 Million
```

Clearly suspicious.

---

### Industry Rule

Many experienced AI engineers spend more time understanding and cleaning data than training models.

A common saying is:

> Better data beats a more complex model.

---

## Summary

Visualization helps AI engineers understand data quality, detect problems, discover patterns, and make better modeling decisions.

---

# Q4. What is an outlier? Why can outliers be problematic?

An outlier is a data point that is significantly different from the rest of the dataset.

Example:

```text
Salary Data:

40K
50K
55K
60K
65K
70K
10M
```

The value:

```text
10M
```

is an outlier.

---

## Why Outliers Occur

### Data Entry Errors

Example:

```text
Age = 250
```

instead of:

```text
Age = 25
```

---

### Measurement Errors

Sensors can produce incorrect readings.

---

### Genuine Rare Events

Some outliers are valid and should not be removed.

Example:

```text
Billionaire salaries
```

---

## Why Outliers Are Problematic

### 1. Distort Statistics

Average salary:

```text
Without Outlier → 56K

With Outlier → Much Higher
```

---

### 2. Mislead Models

Models may try to fit rare abnormal values.

This can reduce general performance.

---

### 3. Increase Training Instability

Large values can dominate calculations and gradients.

---

## Summary

Outliers are unusually large or small values that can distort analysis and negatively affect model performance if not handled carefully.

---

# Q5. Suppose you receive a dataset containing:

```text
Age
Salary
Years Experience
```

Which visualizations would you use first and why?

I would start with **histograms** and **scatter plots**.

---

## Step 1: Histograms

For:

* Age
* Salary
* Years Experience

Purpose:

* Understand distributions
* Detect skewness
* Identify outliers
* Observe value ranges

Example histogram for Salary:

```text
20K-40K
40K-60K
60K-80K
80K-100K
```

This helps me understand how salaries are distributed.

A simple example of a histogram:

---

## Step 2: Scatter Plot (Experience vs Salary)

Purpose:

* Identify correlation
* Verify whether salary increases with experience
* Detect unusual observations

Example:

---

## Step 3: Scatter Plot (Age vs Salary)

Purpose:

* Check whether age and salary are related.
* Detect clusters and anomalies.

---

## Step 4: Scatter Plot (Age vs Experience)

Purpose:

* Validate data consistency.

Example:

```text
Age = 22
Experience = 20 years
```

This would immediately look suspicious.

---

## My Initial Visualization Workflow

```text
1. Histogram → Age

2. Histogram → Salary

3. Histogram → Experience

4. Scatter Plot → Experience vs Salary

5. Scatter Plot → Age vs Salary

6. Scatter Plot → Age vs Experience
```

This would give me a strong understanding of the dataset before performing any feature engineering or model training.

---

# Key Learning from Day 006

Days 001–005 focused on:

```text
Python
↓
NumPy
↓
Vectors
↓
Matrices
↓
Linear Algebra
```

Day 006 introduces something equally important:

```text
Raw Data
↓
Visualization
↓
Understanding
↓
Cleaning
↓
Model Training
```

A good AI engineer does not immediately train a model. They first **look at the data, understand the data, and question the data**. Visualization is one of the fastest ways to do that.


Example salary distribution

Histogram-style salary bins for understanding distribution.

range	count
20K-40K	12
40K-60K	28
60K-80K	35
80K-100K	15

Experience vs Salary

Example relationship between experience and salary.

experience	salary
1	300,000
3	500,000
5	800,000
8	1,200,000
10	1,500,000