# Project Step 3 — Data Quality Assessment

Tomorrow (or in the next session), we'll investigate questions like:

Which columns have missing values?
How many missing values?
Which columns are complete?
Are there duplicate rows?
Are the data types appropriate?
Are there obvious inconsistencies?


Perfect.

Now the real investigation begins.

Up until now we've answered:

> **What is this dataset?**

Now we answer:

> **Can I trust this dataset?**

This is one of my favorite parts of an AI project because this is where engineering thinking starts to shine.

---

# 🚀 Project 1 – AI Data Investigation

## Step 3 – Data Quality Assessment

Today we're going to inspect the **health** of the dataset.

Think like a doctor.

Before prescribing medicine, a doctor first checks:

* Temperature
* Blood pressure
* Heart rate
* Medical history

Similarly, before cleaning data, an AI engineer checks its "vital signs."

---

# Our Goal Today

By the end of this step, you should be able to answer:

* Is the dataset complete?
* Are there missing values?
* Are there duplicate records?
* Are the data types correct?
* Which columns need attention first?

Notice that we're **still not fixing anything**.

We're only observing and documenting.

---

# Step 3.1 – Revisit `info()`

You've already run:

```python
df.info()
```

Let's look at it again, but this time with an investigator's mindset.

You saw:

```text
Age        714 non-null
Cabin      204 non-null
Embarked   889 non-null
```

Everything else:

```text
891 non-null
```

---

## Question

What does this tell us?

Not:

> "Age has missing values."

Go one level deeper.

It tells us:

> **Some information was not available for every passenger.**

That's an important distinction.

The dataset isn't "wrong."

It's **incomplete** in certain places.

---

# Step 3.2 – Quantify Missing Values

Now let's measure them.

Run:

```python
df.isnull().sum()
```

You'll get something similar to:

```text
PassengerId      0
Survived         0
Pclass           0
Name             0
Sex              0
Age            177
SibSp            0
Parch            0
Ticket           0
Fare             0
Cabin          687
Embarked         2
```

---

# Stop and Think

Don't rush to the next command.

Ask yourself:

> Which missing values concern me the most?

Is it:

```text
Embarked → 2
```

or

```text
Cabin → 687
```

Why?

---

# Step 3.3 – Calculate Missing Percentages

Absolute numbers are useful.

Percentages are even more useful.

Let's calculate them.

```python
missing_percentage = (
    df.isnull().sum() / len(df)
) * 100

print(missing_percentage)
```

Expected idea:

```text
Age         ~19.9%
Cabin       ~77.1%
Embarked    ~0.2%
```

---

# Why Percentages Matter

Imagine two datasets.

Dataset A:

```text
10 missing values

Out of 100 rows
```

10%

Dataset B:

```text
10 missing values

Out of 10 million rows
```

Almost nothing.

Absolute counts can be misleading.

Percentages provide context.

---

# Engineering Thinking

Now ask:

If a column has:

```text
77% missing
```

Should we:

* Keep it?
* Remove it?
* Fill it?
* Investigate further?

Don't answer yet.

Just think.

We'll make that decision later.

---

# Step 3.4 – Check for Duplicates

Now investigate uniqueness.

Run:

```python
df.duplicated().sum()
```

Suppose the output is:

```text
0
```

Excellent.

That tells us:

No completely identical rows.

---

# Important Concept

Remember our discussion from Day 008.

No duplicates **does not mean**:

No repeated passengers.

It means:

No two rows are identical across **all columns**.

That's an important distinction.

---

# Step 3.5 – Verify Data Types

You've already seen:

```text
int64
float64
object
```

Let's classify them.

| Data Type | Meaning                      |
| --------- | ---------------------------- |
| int64     | Whole numbers                |
| float64   | Decimal numbers              |
| object    | Usually text or mixed values |

Now ask:

Does each column have a sensible type?

Examples:

* Age → float64 ✅ (because of missing values and possible decimals)
* Fare → float64 ✅
* Sex → object ✅
* Name → object ✅

No red flags yet.

---

# Step 3.6 – A Data Quality Summary

By this point, you should be able to write a short report like this:

> **Initial Data Quality Report**
>
> * Dataset contains **891 rows** and **12 columns**.
> * Most columns are complete.
> * `Age` has a moderate number of missing values.
> * `Cabin` has a very high number of missing values.
> * `Embarked` has very few missing values.
> * No duplicate rows were found.
> * Data types appear appropriate for the initial analysis.

Notice something.

This report contains **no code**.

It contains **understanding**.

---

# Architecture Perspective

Think back to backend engineering.

When a production issue occurs, do you immediately change the code?

No.

You first:

```text
Collect Logs
      ↓
Inspect Metrics
      ↓
Understand the Problem
      ↓
Only Then Fix It
```

Data quality assessment follows the same principle.

Observe before acting.

---

# Hands-On Exercise

Add these cells to your notebook:

```python
# Missing values
df.isnull().sum()
```

```python
# Missing percentages
missing_percentage = (df.isnull().sum() / len(df)) * 100
missing_percentage
```

```python
# Duplicate rows
df.duplicated().sum()
```

```python
# Data types
df.dtypes
```

Don't clean anything yet.

Just observe the outputs.

---

# 🎯 Mini Assignment

After running the code, answer these questions:

### Q1

Which column has the highest percentage of missing values?

Approximately what percentage is missing?

---

### Q2

Why is looking at **percentages** often more informative than just looking at the number of missing values?

---

### Q3

The `Cabin` column has about 77% missing values.

Without cleaning it yet, what possible options do you think an AI engineer might consider for handling such a column?

There isn't a single correct answer—I want your reasoning.

---

### Q4

The `Embarked` column has only 2 missing values.

Would you handle this differently from the `Cabin` column?

Why?

---

### Q5

Write a brief **Data Quality Report** (5–8 bullet points) summarizing the current health of the Titanic dataset.

---

# Mentor Insight

Today, we're deliberately resisting the temptation to "fix" things.

That restraint is important.

Many beginners see a missing value and immediately write:

```python
df.fillna(...)
```

An experienced AI engineer pauses first and asks:

> "Before I change the data, do I understand what I'm changing and why?"

That habit—**observe, assess, then act**—is going to stay with you throughout Machine Learning, Deep Learning, and even LLM engineering.

We're not just learning Pandas anymore.

We're learning how to make thoughtful engineering decisions.



----------------------------------

# Step 3.5 – Verify Data Types : Explanation

You've already seen:

```text
int64
float64
object
```

Let's classify them.

| Data Type | Meaning                      |
| --------- | ---------------------------- |
| int64     | Whole numbers                |
| float64   | Decimal numbers              |
| object    | Usually text or mixed values |

Now ask:

Does each column have a sensible type?

Examples:

* Age → float64 ✅ (because of missing values and possible decimals)
* Fare → float64 ✅
* Sex → object ✅
* Name → object ✅

Excellent question.

This is exactly the kind of curiosity I want you to have.

You're no longer asking:

> **"What is the answer?"**

You're asking:

> **"How do I verify it myself?"**

That's the mindset of an engineer.

---

# Let's understand this from first principles.

When I said:

```text
Age → float64 ✅
Fare → float64 ✅
Sex → object ✅
Name → object ✅
```

I didn't memorize it.

I **verified** it from the dataset.

There are several ways to do this.

---

# Method 1 (Most Common)

## `df.info()`

You've already used it.

```python
df.info()
```

Output:

```text
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 891 entries, 0 to 890

Data columns (total 12 columns):

PassengerId    int64
Survived       int64
Pclass         int64
Name           object
Sex            object
Age            float64
SibSp          int64
Parch          int64
Ticket         object
Fare           float64
Cabin          object
Embarked       object
```

This is usually the **first command** an AI engineer runs.

---

# Method 2

## `df.dtypes`

```python
df.dtypes
```

Output:

```text
PassengerId      int64
Survived         int64
Pclass           int64
Name            object
Sex             object
Age            float64
SibSp            int64
Parch            int64
Ticket          object
Fare           float64
Cabin           object
Embarked        object
dtype: object
```

This is shorter than `info()` and focuses only on column data types.

---

# Method 3

Check a single column.

Suppose you're interested only in Age.

```python
df["Age"].dtype
```

Output:

```python
float64
```

Now check Fare.

```python
df["Fare"].dtype
```

Output:

```python
float64
```

Check Name.

```python
df["Name"].dtype
```

Output:

```python
object
```

---

# But Here's the Interesting Question...

You asked:

> **How do we know Age is float64 because of missing values?**

Excellent question.

Let's investigate.

---

## Create a Simple Example

```python
import pandas as pd

ages = pd.Series([20, 25, 30])

print(ages)
print(ages.dtype)
```

Output:

```text
0    20
1    25
2    30

dtype: int64
```

Everything is an integer.

So Pandas stores:

```text
int64
```

---

## Now Add a Missing Value

```python
import numpy as np

ages = pd.Series([20, 25, np.nan])

print(ages)
print(ages.dtype)
```

Output:

```text
0    20.0
1    25.0
2     NaN

dtype: float64
```

Notice something surprising?

The integers became:

```text
20.0

25.0
```

Why?

---

# Internal Reason

Let's think about how computers store numbers.

There is **no special integer value that represents NaN**.

But floating-point numbers **do** have a special representation for NaN, defined by the IEEE 754 standard.

So when Pandas sees:

```python
20
25
NaN
```

it silently converts the whole column to:

```python
20.0
25.0
NaN
```

because `float64` can represent both regular numbers and `NaN`.

That's why:

```python
df["Age"].dtype
```

is:

```text
float64
```

---

# Why Isn't Fare int64?

Look at the Titanic dataset.

Try this:

```python
df["Fare"].head(10)
```

You'll see values like:

```text
7.25
71.2833
8.05
53.1
```

These are already decimal numbers.

So even without missing values, Fare would still be:

```text
float64
```

---

# Let's Verify This

Run:

```python
df["Fare"].head(10)
```

Ask yourself:

> Do I see decimal values?

If yes...

Then:

```text
float64
```

makes perfect sense.

---

# Why is Sex an object?

Run:

```python
df["Sex"].unique()
```

Output:

```text
array(['male', 'female'])
```

These are strings.

Strings are stored as:

```text
object
```

---

# Why is Name an object?

Run:

```python
df["Name"].head()
```

Output:

```text
Braund, Mr. Owen Harris

Cumings, Mrs. John Bradley

...
```

Again...

These are strings.

Hence:

```text
object
```

---

# Small Exercise (Before Moving Ahead)

I want you to verify these yourself.

Run:

```python
df.dtypes
```

Then run:

```python
df["Age"].dtype

df["Fare"].dtype

df["Name"].dtype

df["Sex"].dtype
```

Finally, run:

```python
df["Fare"].head()

df["Age"].head(10)

df["Sex"].unique()
```

Now answer these three questions **without Googling**:

1. Why is **Fare** stored as `float64`?
2. Why is **Age** stored as `float64` instead of `int64`?
3. Why are **Name** and **Sex** stored as `object`?

---

## Mentor Note

This may seem like a small detail, but it's actually an important lesson.

As backend engineers, we're used to thinking about **database types**:

* `INTEGER`
* `VARCHAR`
* `FLOAT`
* `DATE`

In AI, you'll build the same habit for DataFrames.

Before you analyze any dataset, you should naturally ask:

* What is the type of each column?
* Does that type make sense?
* Could an incorrect type cause problems later?

That habit will save you from countless bugs when we start building machine learning pipelines.

🚀 Now We Reach One of the Most Important Decisions

Up until now, we've gathered evidence.

Now we're going to answer a question that every AI engineer faces:

Which columns are actually useful?

This is the beginning of Feature Selection Thinking.

Notice I didn't say "Feature Selection" yet—we'll study that formally in Machine Learning.

Right now, I want you to develop the intuition.

Before We Write Any Code

Let's play a game.

Imagine I remove the Survived column and ask you:

"Predict whether a passenger survived."

You can use any of these columns:

PassengerId
Pclass
Name
Sex
Age
SibSp
Parch
Ticket
Fare
Cabin
Embarked

Now ask yourself:

Which columns would probably help?

For example:

Sex

Maybe.

Why?

We don't know yet.

Age

Maybe.

PassengerId

Probably not.

Fare

Maybe.

Name

Maybe...

because of titles like:

Mr.
Mrs.
Master.
Dr.

Notice what's happening?

We're no longer asking:

What type is this column?

We're asking:

Could this column help predict survival?

That is a completely different level of thinking.

🎯 Next Step (Project Step 4)

Tomorrow (or in our next session), we'll start investigating each feature one by one.

Not with machine learning.

With curiosity.

We'll ask questions like:

Does passenger class affect survival?
Does age affect survival?
Does sex affect survival?
Does fare tell us something?
Is cabin useful despite having many missing values?
Should we keep PassengerId?

We'll use Pandas + Matplotlib together to answer those questions with evidence, not assumptions.