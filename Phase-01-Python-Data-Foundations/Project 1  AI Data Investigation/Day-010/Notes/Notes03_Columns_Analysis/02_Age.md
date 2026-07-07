Excellent.

This is where the project starts getting really interesting.

We've investigated a **categorical feature (`Sex`)**.

Now we're moving to our **first numerical feature**.

And this changes everything.

---

# 🚀 Project 1 – AI Data Investigation

# Step 4.2 — Feature Investigation: Age

Before opening Jupyter...

Let's do something.

I want you to forget that this is the Titanic dataset.

Imagine you're an AI engineer working in a hospital.

You receive this column:

```text
Age
```

Would your first question be:

> What's the average age?

No.

A professional AI engineer first asks:

> **"What kind of feature is Age?"**

---

# Step 1 — Understand the Feature

Let's investigate it.

## What is Age?

Age represents:

```text
The passenger's age (in years)
```

Good.

Now classify it.

| Question                       | Answer                          |
| ------------------------------ | ------------------------------- |
| Identifier?                    | ❌ No                            |
| Target?                        | ❌ No                            |
| Numerical?                     | ✅ Yes                           |
| Continuous?                    | ✅ Yes                           |
| Can it contain missing values? | ✅ Yes (we already know it does) |
| Could it influence survival?   | Possibly                        |

---

# Why is Age Continuous?

Suppose two passengers are:

```text
25 years

25.5 years
```

Half years are possible.

Babies may even be:

```text
0.5 years
```

So Age is treated as a **continuous numerical feature**.

---

# Step 2 — Look at the Data

Now run:

```python
df["Age"].head(10)
```

You'll see something similar to:

```text
22.0
38.0
26.0
35.0
NaN
35.0
54.0
2.0
27.0
14.0
```

---

# Don't Rush

Look carefully.

What immediately catches your attention?

Not:

```text
22

38

26
```

Those are normal.

What stands out?

```text
NaN
```

Exactly.

---

# First Observation

Write this down.

> **Age contains missing values.**

Not:

> Age is a bad feature.

Just an observation.

---

# Step 3 — Basic Statistics

Now run:

```python
df["Age"].describe()
```

You should see something similar to:

| Statistic | Value |
| --------- | ----: |
| Count     |   714 |
| Mean      |  29.7 |
| Std       |  14.5 |
| Min       |  0.42 |
| 25%       |  20.1 |
| 50%       |    28 |
| 75%       |    38 |
| Max       |    80 |

---

# Let's Understand Every Number

Many people memorize `describe()`.

We're not going to do that.

We're going to understand it.

---

## Count

```text
714
```

Question:

Shouldn't there be:

```text
891
```

Yes.

Why isn't there?

Because:

```text
177 Ages

↓

Missing
```

---

## Mean

```text
29.7
```

This means:

The average passenger age is about:

```text
30 years
```

---

## Min

```text
0.42
```

Question:

Is this an error?

No.

Think.

A baby can absolutely be around:

```text
0.42 years
```

which is roughly 5 months old.

That's a great example of why context matters.

---

## Max

```text
80
```

Question:

Is 80 unrealistic?

No.

It's high, but entirely possible.

So we don't automatically label it as an outlier.

---

# Step 4 — Visualize the Distribution

Now let's stop reading numbers.

Let's see the data.

Run:

```python
import matplotlib.pyplot as plt

plt.hist(df["Age"], bins=20)

plt.title("Age Distribution")
plt.xlabel("Age")
plt.ylabel("Number of Passengers")

plt.show()
```

---

# Don't Look at the Graph...

Investigate it.

Ask:

### Question 1

Where are most passengers?

Children?

Young adults?

Middle-aged?

Older adults?

---

### Question 2

Is the distribution symmetric?

Or skewed?

---

### Question 3

Do you notice any unusual ages?

---

# Step 5 — Think Like an AI Engineer

Suppose later we train a model.

Will the model learn from:

```text
Average Age
```

No.

It learns from **individual ages**.

But understanding the distribution helps us answer:

* Is this feature useful?
* Does it require cleaning?
* Should we normalize it later?
* Are there unusual values?

---

# Step 6 — Connect to the Business Problem

Our goal isn't to study age.

Our goal is to study:

```text
Survival
```

So ask:

> Could age influence survival?

Again...

Don't answer.

Just form hypotheses.

Examples:

* Children may have had higher survival rates.
* Elderly passengers may have had lower survival rates.
* Maybe age has no effect.

We don't know yet.

And that's okay.

---

# Architecture Perspective

Think about monitoring an API.

You might see:

```text
Average latency = 120 ms
```

That's useful.

But it doesn't tell you:

* Whether some requests take 2 seconds.
* Whether latency spikes at certain times.

Similarly:

The mean age alone doesn't describe the entire population.

That's why we visualize distributions.

---

# Hands-On Exercise

In your notebook, create a new section:

```text
Feature Investigation – Age
```

Run these commands one by one.

```python
# First 10 values
df["Age"].head(10)
```

```python
# Summary statistics
df["Age"].describe()
```

```python
# Missing values
df["Age"].isnull().sum()
```

```python
# Histogram
import matplotlib.pyplot as plt

plt.hist(df["Age"], bins=20)

plt.title("Age Distribution")
plt.xlabel("Age")
plt.ylabel("Count")

plt.show()
```

Save the histogram screenshot.

We'll use it in your GitHub documentation.

---

# 🎯 Mini Assignment

Answer these after running the code.

## Q1

From `describe()`:

Explain in your own words what each of these means:

* Count
* Mean
* Min
* Max
* 25%
* 50%
* 75%
* Std

Don't define them from memory.

Explain them as if you're teaching someone.

---

## Q2

What does the histogram tell you about the age distribution?

Where do most passengers appear to fall?

---

## Q3

Why is `Min = 0.42` **not** necessarily an outlier?

Why is `Max = 80` **not** automatically considered an outlier?

---

## Q4

List **three hypotheses** about how Age *might* influence survival.

Remember:

These are hypotheses.

Not conclusions.

---

## Q5

Write a short **Feature Investigation Report** for the `Age` column.

Include:

* Feature type
* Missing values
* Distribution
* Basic statistics
* Possible importance for machine learning

---

# 🌟 Mentor Insight

Today you're learning something much bigger than the `Age` column.

You're learning how to investigate **any numerical feature**.

The exact same process we'll use today can later be applied to:

* Salary
* House Price
* Temperature
* Blood Pressure
* Credit Score
* Transaction Amount
* Model Confidence Scores

That's why I'm intentionally slowing us down.

I don't want you to memorize the Titanic dataset.

I want you to internalize a reusable investigation framework that you'll carry into every AI project you work on in the future.

And one last request: when you look at the histogram, resist the temptation to immediately interpret everything. Spend a minute simply observing it. Good investigators learn to see before they explain. That habit will serve you well throughout your AI career.
