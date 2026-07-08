These answers are exactly how I would expect an AI engineer to reason **before writing any cleaning code**.

---

# Day 010 Mini Assignment

## Q1. Which column has the highest percentage of missing values?

The **Cabin** column has the highest percentage of missing values.

From the dataset:

* Total rows = **891**
* Missing Cabin values = **687**

Percentage:

```text
(687 / 891) × 100 ≈ 77%
```

Approximately **77%** of the Cabin data is missing.

The next highest is:

* **Age** → 177 missing values (~20%)
* **Embarked** → 2 missing values (~0.2%)

---

# Q2. Why is looking at percentages often more informative than just looking at the number of missing values?

The number of missing values alone does not tell the complete story because datasets can have very different sizes.

For example:

### Dataset A

```text
Rows = 100

Missing = 50
```

Missing Percentage:

```text
50%
```

---

### Dataset B

```text
Rows = 10,000

Missing = 50
```

Missing Percentage:

```text
0.5%
```

Both datasets have **50 missing values**, but the impact is completely different.

Percentages provide context by showing **how much of the dataset is affected**, making it easier to decide whether a column needs cleaning, imputation, or removal.

---

# Q3. The Cabin column has about 77% missing values. Without cleaning it yet, what possible options do you think an AI engineer might consider for handling such a column?

Since such a large portion of the data is missing, I would not immediately decide what to do. Instead, I would consider several options and evaluate them.

Possible approaches include:

* **Drop the column** if the missing values are too high and the remaining information is unlikely to improve the model.
* **Investigate whether missing Cabin values have meaning.** For example, passengers without recorded cabins might mostly belong to lower ticket classes, making "missing" itself informative.
* **Extract useful features** from the available cabin values, such as the deck letter (`A`, `B`, `C`, etc.), rather than using the full cabin number.
* **Create a new feature** indicating whether cabin information is available (`CabinAvailable = Yes/No`).
* **Consult domain knowledge** before making a decision, since historical context may explain why cabin information is missing.

I would choose the best approach only after understanding how important the Cabin column is for predicting survival.

---

# Q4. The Embarked column has only 2 missing values. Would you handle this differently from the Cabin column? Why?

Yes.

The **Embarked** column has only **2 missing values out of 891 rows**, which is approximately **0.2%** of the dataset.

Because the percentage is extremely small, simple approaches are reasonable, such as:

* Removing the two rows, or
* Filling the missing values with the most common boarding port (mode).

Unlike the Cabin column, there is very little information loss.

For the Cabin column, dropping rows would remove **77% of the dataset**, which would be unacceptable.

Therefore, the strategy depends on **how much data is missing**, not just whether data is missing.

---

# Q5. Data Quality Report (Titanic Dataset)

* The dataset contains **891 passenger records** and appears to have loaded successfully.
* Most columns have **no missing values**, indicating generally good data quality.
* The **Cabin** column has approximately **77% missing values**, making it the most significant data quality issue.
* The **Age** column has about **20% missing values**, which will require appropriate handling before model training.
* The **Embarked** column has only **2 missing values (~0.2%)**, making it a minor issue.
* Numerical features such as **Age** and **Fare** are available, while categorical features like **Sex**, **Pclass**, and **Embarked** can be used after encoding.
* Before training a machine learning model, missing values should be handled carefully, and feature engineering may be useful for columns such as **Cabin** and **Name**.

---

# 🌟 Mentor Feedback

This assignment is actually testing something deeper than Pandas.

Your mentor is teaching you to think like this:

```text
Load Data
      ↓
Inspect Data
      ↓
Measure Data Quality
      ↓
Think About Solutions
      ↓
Then Write Code
```

Notice that **Q3 intentionally says "Don't clean it yet."**

That's because experienced AI engineers don't immediately write:

```python
df.drop(...)
```

They first ask:

* **How much data is missing?**
* **Why is it missing?**
* **Is the missingness random or meaningful?**
* **Will dropping it hurt the model?**
* **Can I extract useful information instead?**

This habit of **reasoning before coding** is what separates someone who knows Pandas from someone who can build reliable AI systems.


These are fantastic questions! You're now moving beyond **using Pandas** to understanding **why Pandas chooses certain data types**. This understanding will help you a lot in AI and backend engineering.

Let's answer each one.

---

# Q1. Why is `Fare` stored as `float64`?

First, let's understand what `float64` means.

```text
float  → Decimal numbers
64     → Uses 64 bits (8 bytes) of memory
```

So `float64` stores **decimal (floating-point) numbers**.

---

## Look at the Fare column

The fare values look something like:

|     Fare |
| -------: |
|     7.25 |
|  71.2833 |
|     8.05 |
|    53.10 |
| 512.3292 |

Notice something?

They're **not whole numbers**.

For example:

```text
7.25
71.2833
53.10
```

These contain decimal values.

An `int64` cannot store decimals.

So Pandas automatically chooses:

```text
float64
```

---

## Backend Analogy

Imagine designing a database.

Would you use:

```sql
salary INT
```

or

```sql
salary DECIMAL(10,2)
```

For money, you'd choose **DECIMAL** because money can have fractional values.

Pandas makes the same decision.

---

# Q2. Why is `Age` stored as `float64` instead of `int64`?

This confuses almost everyone when they first learn Pandas.

Let's see why.

---

## If every age were present

Suppose the Age column looked like:

| Age |
| --: |
|  22 |
|  35 |
|  40 |
|  18 |

All are integers.

Pandas would happily use:

```text
int64
```

---

## But the Titanic dataset has missing values

Remember:

```text
Age → 177 missing values
```

Example:

| Age |
| --: |
|  22 |
|  35 |
| NaN |
|  18 |

Now we have a problem.

---

## Can an integer column store NaN?

No.

An `int64` column can only store integers.

It **cannot** store:

```text
NaN
```

---

## But float64 can

A floating-point column can store:

```text
22.0

35.0

NaN

18.0
```

So Pandas automatically converts the whole column to:

```text
float64
```

to accommodate the missing values.

---

### Example

If you create:

```python
import pandas as pd

ages = pd.Series([22, 35, None, 18])

print(ages.dtype)
```

Output:

```text
float64
```

Even though every real age is an integer!

---

## Why?

Because:

```text
None
↓

NaN

↓

Requires float64
```

---

## Modern Pandas

Newer versions also support nullable integers:

```text
Int64
```

(notice the capital **I**)

This allows:

```text
22

35

<NA>

18
```

But historically, Pandas used `float64` for this situation, and you'll still see it frequently.

---

# Q3. Why are `Name` and `Sex` stored as `object`?

This is another common question.

---

## What is `object`?

In Pandas, `object` traditionally means:

> "This column contains Python objects."

In practice, for most datasets:

```text
object ≈ strings (text)
```

---

## Name

Example:

| Name                       |
| -------------------------- |
| Braund, Mr. Owen Harris    |
| Cumings, Mrs. John Bradley |
| Heikkinen, Miss. Laina     |

These are text values.

Numbers don't make sense here.

So Pandas stores them as:

```text
object
```

---

## Sex

Values:

| Sex    |
| ------ |
| male   |
| female |
| male   |

Again,

these are strings.

Therefore:

```text
object
```

---

## Why not Boolean?

You might wonder:

```text
Male

Female
```

There are only two values.

Why not:

```text
True

False
```

Because the original CSV file contains the words:

```text
male

female
```

Pandas doesn't automatically convert text categories into booleans or numbers. It preserves the original data.

Later, during preprocessing, we usually encode them into numerical values because machine learning models work with numbers, not strings.

Example:

```text
male   → 0

female → 1
```

or use one-hot encoding, depending on the algorithm.

---

# Summary Table

| Column   | Data Type | Why?                                                                    |
| -------- | --------- | ----------------------------------------------------------------------- |
| **Fare** | `float64` | Ticket prices contain decimal values.                                   |
| **Age**  | `float64` | Missing values (`NaN`) require a floating-point type in classic Pandas. |
| **Name** | `object`  | Contains text (strings).                                                |
| **Sex**  | `object`  | Contains text categories (`male`, `female`).                            |

---

# 🧠 Mentor Tip: How Pandas Decides a Column's Data Type

When Pandas reads a CSV file, it **infers** the data type by looking at the values in each column.

Think of it like this:

```text
Read CSV
     ↓
Look at every value
     ↓
Can all values be integers?
     ↓
Yes → int64
No
     ↓
Can all values be numbers with decimals?
     ↓
Yes → float64
No
     ↓
Are they text?
     ↓
Yes → object (or string in newer Pandas)
```

For the Titanic dataset:

* **Fare** contains decimal numbers → `float64`
* **Age** contains integers *plus* missing values (`NaN`) → `float64`
* **Name** contains text → `object`
* **Sex** contains text categories → `object`

This inference step happens automatically every time you call `pd.read_csv()`, which is why checking `df.info()` is one of the first things every AI engineer does after loading a dataset.
