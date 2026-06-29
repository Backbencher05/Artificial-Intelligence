🚀 Phase 1 → Day 007 → Session 7
# Pandas Fundamentals — The Language of Data

Welcome to one of the most practical topics in the entire AI roadmap.

If NumPy taught us:

How AI computes

then Pandas teaches us:

How AI engineers work with data

In real-world AI projects, you'll often spend more time with Pandas than with machine learning models.

Session Goal

By the end of today, you should understand:

Why Pandas exists.
What a DataFrame is.
Rows and columns.
Reading datasets.
Inspecting data.
Selecting and filtering data.
Sorting data.
Basic aggregations.
How Pandas fits into the AI workflow.
Part 1: Why Does Pandas Exist?

Let's imagine a dataset:

Name      Age     Salary
Aditya    28      100000
Rahul     32      120000
Priya     25       90000

You could store this using:

[
    ["Aditya", 28, 100000],
    ["Rahul", 32, 120000],
    ["Priya", 25, 90000]
]

But then questions become painful.

Example:

Find everyone older than 30.

You'd write loops.

Or:

Average salary?

More loops.

Or:

Sort by salary.

Even more code.

Pandas Idea

Pandas says:

Data is usually tabular.

Let's represent it as a table.

Part 2: What Is a DataFrame?

The most important Pandas object:

DataFrame

Think:

Excel Spreadsheet
+
SQL Table
+
Python Object

Example:

import pandas as pd

df = pd.DataFrame({
    "Name": ["Aditya", "Rahul", "Priya"],
    "Age": [28, 32, 25],
    "Salary": [100000, 120000, 90000]
})

Output:

     Name  Age  Salary
0  Aditya   28  100000
1   Rahul   32  120000
2   Priya   25   90000
What Is Happening?

Rows:

People

Columns:

Attributes

This pattern appears everywhere in AI.

Part 3: Rows vs Columns

Dataset:

Name     Age    Salary
Row

Represents:

One Observation

Example:

Aditya
28
100000

One row.

Column

Represents:

One Feature

Example:

Age

Column.

AI Translation

Rows:

Samples

Columns:

Features

This becomes very important in ML.

Part 4: Reading Data

Most datasets arrive as:

CSV Files

Example:

df = pd.read_csv("employees.csv")

Now:

CSV
↓
DataFrame
Why This Matters

Real AI workflow:

CSV
↓
Pandas
↓
Cleaning
↓
Analysis
↓
Model
Part 5: Inspecting Data

Before doing anything:

Understand the dataset.

First Rows
df.head()

Output:

First 5 rows
Last Rows
df.tail()

Output:

Last 5 rows
Dataset Shape
df.shape

Example:

(1000, 10)

Meaning:

1000 rows
10 columns
Column Names
df.columns
Data Types
df.info()

Output:

Column Names
Data Types
Missing Values
Why AI Engineers Love info()

One command reveals:

Data Quality

very quickly.

Part 6: Selecting Data
Single Column
df["Salary"]

Output:

Entire Salary Column
Multiple Columns
df[["Age", "Salary"]]
AI Interpretation

Selecting features.

Example:

Age
Salary
Experience

for modeling.

Part 7: Filtering Data

One of the most common operations.

Example:

df[df["Age"] > 30]

Result:

Only people older than 30

Another:

df[df["Salary"] > 100000]
SQL Analogy

Backend connection:

SELECT *
FROM employees
WHERE age > 30;

Pandas:

df[df["Age"] > 30]
Part 8: Sorting Data
Highest Salary First
df.sort_values(
    by="Salary",
    ascending=False
)

Output:

Highest Salary
↓
Lowest Salary
Why Useful?

Find:

Top customers
Largest transactions
Highest salaries
Part 9: Aggregations

Another extremely important concept.

Average Salary
df["Salary"].mean()
Maximum Salary
df["Salary"].max()
Minimum Salary
df["Salary"].min()
Count
df["Salary"].count()
Why Important?

This is the first step in understanding data statistically.

Part 10: Grouping Data

One of Pandas' superpowers.

Example:

Department
Salary

Question:

Average salary per department?

Answer:

df.groupby("Department")[
    "Salary"
].mean()

Result:

Engineering → 120000

HR → 70000

Sales → 90000
Why This Matters

This is how analysts discover patterns.

Real AI Workflow

Imagine:

Customer Dataset

Using Pandas:

Load
↓
Inspect
↓
Clean
↓
Filter
↓
Aggregate
↓
Visualize
↓
Model

Notice:

Modeling comes later.
Architecture Perspective

Backend Engineer:

Database Query
↓
Business Logic

AI Engineer:

DataFrame Query
↓
Data Understanding

Many Pandas operations feel surprisingly similar to SQL.

That similarity is not accidental.

Hands-On Exercise

Install Pandas:

pip install pandas

Create:

import pandas as pd

df = pd.DataFrame({
    "Name": ["Aditya", "Rahul", "Priya"],
    "Age": [28, 32, 25],
    "Salary": [100000, 120000, 90000]
})

print(df)

Try:

print(df.head())

print(df.shape)

print(df["Salary"])

print(df["Salary"].mean())

Try Filtering:

print(
    df[df["Age"] > 28]
)

Try Sorting:

print(
    df.sort_values(
        by="Salary",
        ascending=False
    )
)
Day 007 Assignment
Q1

Why does Pandas exist when Python already has lists and dictionaries?

Q2

What is a DataFrame?

Why is it important in AI workflows?

Q3

Explain the difference between:

Row
vs
Column

from an AI perspective.

Q4

Why do AI engineers usually inspect data using:

head()
info()
shape

before performing analysis?

Q5

Suppose you receive a customer dataset containing:

CustomerID
Age
Salary
Department

Describe the first Pandas operations you would perform and why.




What's Coming Next?

This is where AI becomes much more realistic.

Until now, we've assumed our datasets are clean.

Real datasets are not.

Real datasets contain:

Missing Values

Duplicate Rows

Incorrect Data Types

Outliers

Invalid Entries

Inconsistent Formatting

And here's a surprising statistic that you'll hear often in industry:

Building the model:
~20%

Preparing the data:
~80%

That isn't an exact rule, but it reflects a common reality: data preparation usually consumes far more effort than model training.