🚀 Phase 1 → Day 008 → Session 8
Data Cleaning & Preprocessing — Preparing Data for AI

Welcome to one of the most important sessions in AI.

If I asked you:

"What does an AI engineer do every day?"

Many people would answer:

Train models.

Reality is very different.

A more realistic workflow is:

Receive messy data
        ↓
Understand the data
        ↓
Clean the data
        ↓
Transform the data
        ↓
Only then train the model

The model is often the easiest part.

Session Goal

By the end of today, you'll understand:

Why real-world data is messy.
Missing values (NaN).
Duplicate records.
Incorrect data types.
Outliers.
Renaming columns.
Dropping unnecessary columns.
Creating new features.
Building a clean dataset for AI.
Part 1: Why Data Cleaning Exists

Let's imagine a company gives you this dataset.

Name	Age	Salary	Department
Aditya	28	100000	IT
Rahul	30	(missing)	HR
Priya	25	90000	IT
Priya	25	90000	IT
Aman	250	50000	Sales

Immediately, we see problems.

Problem 1

Missing salary.

Problem 2

Duplicate record.

Problem 3

Age = 250.

Probably incorrect.

Should we train an AI model on this?

No.

Why?

Because:

An AI model learns from whatever data you give it.

Bad data → Bad model.

This idea is often summarized as:

Garbage In
↓
Garbage Out
Part 2: Missing Values (NaN)

One of the most common problems.

Example:

Name	Salary
Aditya	100000
Rahul	NaN
Priya	90000

NaN means:

Not a Number

or simply:

Missing value
Detect Missing Values
df.isnull()

Returns:

True
False
False
Count Missing Values
df.isnull().sum()

Example:

Name          0
Age           0
Salary        1
Department    0

Now we know exactly where the problem is.

Part 3: What Should We Do With Missing Values?

There isn't one correct answer.

It depends on the business problem.

Common approaches:

Option 1: Remove Rows
df.dropna()

Use when:

Few missing rows
Missing data isn't important
Option 2: Fill Missing Values

Example:

df["Salary"].fillna(50000)

Or better:

df["Salary"].fillna(df["Salary"].mean())

This replaces missing salaries with the average salary.

Engineering Question

Don't ask:

"Which method is correct?"

Ask:

"Why is the value missing?"

That question is often more important.

Part 4: Duplicate Records

Example:

Name	Age	Salary
Priya	25	90000
Priya	25	90000

Duplicates can distort analysis.

Detect Duplicates
df.duplicated()
Remove Duplicates
df.drop_duplicates()
Part 5: Incorrect Data Types

Imagine:

Salary

stored as:

"100000"

instead of:

100000

One is text.

One is a number.

Check types:

df.info()

Convert types:

df["Salary"] = df["Salary"].astype(int)
Why This Matters

You can't calculate:

"100000" + "50000"

as numbers.

The model expects numeric features.

Part 6: Outliers

We introduced outliers yesterday.

Now let's handle them.

Example salaries:

40000
50000
60000
70000
10000000

Should we remove the 10 million salary?

Maybe.

Maybe not.

Engineering Thinking

Ask:

Is it:

Data entry error?
Real CEO salary?
Billionaire customer?

Business context matters.

Part 7: Renaming Columns

Sometimes datasets contain names like:

cust_age
emp_sal
dept_nm

Rename:

df.rename(columns={
    "cust_age": "Age",
    "emp_sal": "Salary"
})

Cleaner code.

Part 8: Dropping Unnecessary Columns

Example:

CustomerID

If every ID is unique, it usually doesn't help the model.

Drop it:

df.drop(columns=["CustomerID"])
Why?

Because:

CustomerID

doesn't contain meaningful patterns.

It only identifies records.

Part 9: Feature Engineering

One of the most valuable skills in AI.

Suppose we have:

Salary
Age

Create:

df["Salary_per_Age"] = df["Salary"] / df["Age"]

You've created a new feature.

Sometimes engineered features are more useful than original ones.

Part 10: Complete Workflow

Imagine receiving:

customers.csv

Your workflow:

Load CSV
      ↓
head()
      ↓
info()
      ↓
shape
      ↓
describe()
      ↓
Check missing values
      ↓
Remove duplicates
      ↓
Fix data types
      ↓
Handle outliers
      ↓
Create new features
      ↓
Clean dataset
      ↓
Model Training
Architecture Perspective

Backend engineers know:

Don't trust user input.

AI engineers think similarly:

Don't trust raw data.

Every dataset should be validated before use.

Hands-On Exercise

Create a file:

Day-008/practice/data_cleaning.py

import pandas as pd
import numpy as np

df = pd.DataFrame({
    "Name": ["Aditya", "Rahul", "Priya", "Priya"],
    "Age": [28, 30, 25, 25],
    "Salary": [100000, np.nan, 90000, 90000],
    "Department": ["IT", "HR", "IT", "IT"]
})

print("Original Data")
print(df)

print("\nMissing Values")
print(df.isnull().sum())

print("\nDuplicates")
print(df.duplicated())

print("\nAfter Removing Duplicates")
print(df.drop_duplicates())

print("\nFill Missing Salary with Mean")
df["Salary"] = df["Salary"].fillna(df["Salary"].mean())

print(df)

Run it and observe how the dataset changes after each step.

# Day 008 Assignment
Q1

Why is data cleaning considered one of the most important stages in AI projects?

Q2

What are missing values (NaN)?

What are some common ways to handle them?

Q3

Why are duplicate records problematic?

When might duplicates actually be valid?

Q4

Why is checking data types important before training an AI model?

Q5

Suppose you receive this dataset:

CustomerID	Age	Salary	Department
101	25	50000	IT
102	NaN	60000	HR
103	250	70000	Sales
103	250	70000	Sales

Describe, step by step, how you would clean this dataset before using it in a machine learning model.

Notes.md Topics

Document:

Why Data Cleaning Exists
Missing Values
Handling Missing Data
Duplicate Records
Data Types
Outliers
Column Renaming
Dropping Columns
Feature Engineering
Complete Data Cleaning Workflow
Mentor Insight

There's a quote you'll hear often in AI:

"A simple model trained on clean data often outperforms a sophisticated model trained on poor-quality data."

The reason is simple:

Models don't understand truth.

They understand patterns.

If the patterns in the data are wrong, the model will faithfully learn the wrong thing.

Learning to clean and question data is one of the skills that separates an AI engineer from someone who only knows how to call a machine learning library.