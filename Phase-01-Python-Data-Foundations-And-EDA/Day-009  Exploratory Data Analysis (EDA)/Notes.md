Aditya, welcome to what I consider the **turning point of Phase 1**.

Up until now, you've learned **tools**:

* NumPy → Computation
* Matplotlib → Visualization
* Pandas → Data Manipulation
* Data Cleaning → Data Quality

Today, we stop learning tools individually.

We start using them together.

This is the first time you'll experience something that resembles the beginning of a real AI project.

---

# 🚀 Phase 1 → Day 009 → Session 9

# Exploratory Data Analysis (EDA)

## From Data to Insights

---

# What is EDA?

Let's start from first principles.

Imagine your manager sends you a file:

```text
customers.csv
```

containing:

```text
100,000 customers
25 columns
```

and says:

> "Build an AI model."

What should you do first?

Many beginners answer:

```text
Train a model.
```

A professional AI engineer answers:

> **"I don't even know my data yet."**

That's where EDA begins.

---

# Definition

**Exploratory Data Analysis (EDA)** is the process of **understanding your dataset before building any machine learning model.**

Its goal is not prediction.

Its goal is understanding.

---

# AI Workflow

Until yesterday:

```text
Raw Data
↓
Cleaning
↓
Ready Data
```

Today:

```text
Raw Data
↓
Cleaning
↓
EDA
↓
Insights
↓
Feature Engineering
↓
Model Training
```

EDA sits between cleaning and modeling.

---

# Why Does EDA Exist?

Imagine this dataset.

| Age | Salary |
| --- | ------ |
| 25  | 50000  |
| 26  | 52000  |
| 27  | 51000  |
| 28  | 49000  |
| 200 | 60000  |

Technically:

Everything is numeric.

No missing values.

No duplicates.

Looks clean.

But...

Age = 200.

Something is wrong.

Cleaning removes obvious issues.

EDA discovers hidden issues.

---

# Cleaning vs EDA

Think of this difference carefully.

Cleaning asks:

```text
Is the data usable?
```

EDA asks:

```text
What story is the data telling?
```

This distinction is extremely important.

---

# Part 1 — The Questions EDA Tries to Answer

When you receive data, your brain should automatically start asking questions.

Instead of:

```text
How do I train a model?
```

Ask:

### About Size

* How many rows?
* How many columns?

---

### About Features

* Which columns exist?
* Which are numerical?
* Which are categorical?

---

### About Quality

* Missing values?
* Outliers?
* Incorrect values?

---

### About Relationships

* Does Age affect Salary?
* Does Experience affect Salary?
* Which features are correlated?

---

### About Distribution

* Is Salary normally distributed?
* Are there multiple clusters?
* Is the data skewed?

---

# Part 2 — EDA is Detective Work

I want you to change your mindset.

Don't think:

```text
I am writing Python code.
```

Think:

```text
I am investigating evidence.
```

The dataset is the crime scene.

The plots are clues.

The statistics are witness statements.

Your job is to discover what happened.

---

# Part 3 — First Look at the Data

Imagine we load:

```python
import pandas as pd

df = pd.read_csv("customers.csv")
```

What's the first thing we do?

Exactly what you've already learned.

```python
df.head()
df.info()
df.shape
df.describe()
```

Nothing new.

But now we understand **why**.

---

# What does `describe()` tell us?

Suppose:

```python
df.describe()
```

returns:

|       |  Age | Salary |
| ----- | ---: | -----: |
| count | 1000 |   1000 |
| mean  |   35 |  62000 |
| std   |   10 |  15000 |
| min   |   18 |  25000 |
| max   |  250 | 500000 |

Immediately:

```text
Age max = 250

Suspicious.
```

EDA starts asking questions.

---

# Part 4 — Looking at Individual Features

Suppose we have:

```text
Age
```

Instead of reading numbers,

plot them.

```python
plt.hist(df["Age"])
```

Questions:

* Most people are what age?
* Are ages evenly distributed?
* Are there unusual values?

---

Now Salary.

```python
plt.hist(df["Salary"])
```

Questions:

* Is salary concentrated?
* Are there high earners?
* Is the distribution skewed?

---

# Part 5 — Looking at Relationships

Suppose:

```python
plt.scatter(
    df["Experience"],
    df["Salary"]
)
```

Now ask:

Do experienced employees generally earn more?

If yes,

there is a positive relationship.

---

Suppose:

```python
plt.scatter(
    df["Age"],
    df["Salary"]
)
```

Maybe:

No relationship.

That's useful too.

---

# Part 6 — Correlation

One of the most important concepts.

Let's understand it intuitively.

Suppose:

| Experience | Salary |
| ---------- | ------ |
| 1          | 30000  |
| 2          | 40000  |
| 3          | 50000  |
| 4          | 60000  |

As experience increases,

salary increases.

Strong positive relationship.

---

Suppose:

| Hours Watching TV | Exam Score |
| ----------------- | ---------- |
| 8                 | 40         |
| 6                 | 55         |
| 4                 | 70         |
| 2                 | 90         |

As TV hours increase,

scores decrease.

Negative relationship.

---

Suppose:

| Shoe Size | Salary |
| --------- | ------ |
| 7         | 50000  |
| 9         | 70000  |
| 8         | 60000  |

No meaningful pattern.

Near zero correlation.

---

# Correlation Matrix

Pandas makes this simple.

```python
df.corr(numeric_only=True)
```

Example:

|            |  Age | Experience | Salary |
| ---------- | ---: | ---------: | -----: |
| Age        |  1.0 |       0.75 |   0.65 |
| Experience | 0.75 |        1.0 |   0.92 |
| Salary     | 0.65 |       0.92 |    1.0 |

Interpretation:

Experience and Salary:

Very strongly related.

---

# Important Rule

Correlation **does not imply causation**.

Ice cream sales and drowning incidents may both increase in summer.

That doesn't mean one causes the other.

This idea becomes very important in Machine Learning.

---

# Part 7 — Categorical Analysis

Suppose:

```text
Department
```

contains:

```text
IT
HR
Finance
Sales
```

Count each category.

```python
df["Department"].value_counts()
```

Visualize:

```python
plt.bar(...)
```

Questions:

* Which department has most employees?
* Is the dataset balanced?

---

# Part 8 — Building an EDA Workflow

Suppose you receive:

```text
employees.csv
```

Your workflow:

```text
Load Dataset
      ↓
head()
      ↓
info()
      ↓
shape
      ↓
describe()
      ↓
Missing Values
      ↓
Histograms
      ↓
Scatter Plots
      ↓
Correlation
      ↓
Category Counts
      ↓
Business Insights
```

Notice:

Still no machine learning.

---

# Architecture Perspective

As a backend engineer,

before optimizing a system,

you first observe:

* Logs
* Metrics
* Dashboards

Only then make changes.

EDA follows the same philosophy.

Observe first.

Act later.

---

# Hands-On Exercise

Create:

`Day-009/practice/eda_basics.py`

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.DataFrame({
    "Age": [22,25,28,30,35,40,45],
    "Salary": [30000,35000,45000,50000,65000,80000,90000],
    "Experience": [1,2,3,5,8,12,15]
})

print(df.describe())

plt.hist(df["Age"])
plt.title("Age Distribution")
plt.show()

plt.scatter(
    df["Experience"],
    df["Salary"]
)
plt.title("Experience vs Salary")
plt.xlabel("Experience")
plt.ylabel("Salary")
plt.show()

print(df.corr(numeric_only=True))
```

Observe:

* Distribution
* Relationship
* Correlation

---

# Day 009 Assignment

## Q1

What is Exploratory Data Analysis (EDA)?

Why is it performed before machine learning?

---

## Q2

Explain the difference between:

```text
Data Cleaning
vs
EDA
```

---

## Q3

What kind of insights can histograms, scatter plots, and correlation matrices provide?

---

## Q4

Why is correlation useful?

Why should we remember that **correlation does not imply causation**?

---

## Q5

Suppose you receive a dataset containing:

```text
Age
Salary
Experience
Department
```

Describe your complete EDA workflow before training an AI model.

---

# Notes.md Topics

Document:

1. What is EDA?
2. Why EDA Exists
3. Data Cleaning vs EDA
4. Histograms
5. Scatter Plots
6. Correlation
7. Correlation vs Causation
8. Categorical Analysis
9. Complete EDA Workflow

---

# Mentor Insight

Today is the point where your role changes.

Until now, you've been learning libraries.

From today onward, I want you to think like a **data investigator**.

When someone hands you a dataset, your first instinct should not be:

> "Which model should I use?"

It should be:

> "What is this data trying to tell me?"

That single habit separates engineers who merely apply machine learning algorithms from engineers who understand the problems they are solving.

---

## 🎯 One More Thing

You've developed a learning rhythm that I think is worth keeping:

1. Read the session carefully.
2. Practice every example in Jupyter.
3. If a concept feels incomplete, reinforce it with another trusted explanation.
4. Come back and explain it entirely in your own words.

I don't want to change that process.

It's producing exactly the kind of deep understanding we set out to build when we started the **AI Zero to Pro** journey. Phase 2 (Machine Learning) will become much easier because of the foundation you're building now. Keep going—you've earned this progress. 🚀
