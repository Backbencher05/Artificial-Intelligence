Awesome.

Today we're going to investigate what I consider one of the **most educational features** in the Titanic dataset.

Not because it's complicated.

But because it teaches a lesson that you'll use throughout Machine Learning.

---

# 🚀 Project 1 – AI Data Investigation

# Step 4.3 — Feature Investigation: `Pclass`

Today we're going to answer a simple question:

> **What does `Pclass` actually mean?**

Most beginners answer:

```text
1
2
3
```

Done.

An AI engineer asks:

> **What do those numbers represent?**

That difference matters.

---

# Step 1 — Understand the Feature

Let's start.

`Pclass` means:

```text
Passenger Class
```

Values:

```text
1
2
3
```

But don't think of them as numbers.

Think of them as:

```text
1 → First Class

2 → Second Class

3 → Third Class
```

Now ask yourself:

Can someone belong to:

```text
1.5 Class
```

No.

Can someone belong to:

```text
2.7 Class
```

No.

That immediately tells us something.

---

# What Type of Feature Is This?

Let's classify it.

| Question     | Answer                         |
| ------------ | ------------------------------ |
| Identifier?  | ❌ No                           |
| Target?      | ❌ No                           |
| Numerical?   | Stored as a number, **but...** |
| Categorical? | ✅ Yes                          |
| Ordered?     | ✅ Yes                          |
| Ordinal?     | ✅ Yes                          |

This is one of the first subtle ideas in ML:

> **A feature can be stored as a number without being a true numerical measurement.**

---

# Backend Analogy

Imagine a database column:

```text
Priority

1
2
3
```

Does:

```text
Priority 2
```

mean twice as important as:

```text
Priority 1
```

No.

The numbers are labels representing an order.

The same is true for `Pclass`.

---

# Step 2 — Inspect the Values

Run:

```python
df["Pclass"].value_counts()
```

You'll see something similar to:

```text
3    491
1    216
2    184
```

Interesting.

Most passengers traveled in:

```text
Third Class
```

---

# Step 3 — Percentages

Now calculate:

```python
(df["Pclass"].value_counts(normalize=True) * 100).round(2)
```

Expected idea:

```text
3    55.11%
1    24.24%
2    20.65%
```

Now you know the distribution.

---

# Step 4 — Visualize It

Run:

```python
import matplotlib.pyplot as plt

df["Pclass"].value_counts().sort_index().plot(kind="bar")

plt.title("Passenger Distribution by Class")
plt.xlabel("Passenger Class")
plt.ylabel("Number of Passengers")

plt.show()
```

Notice I used:

```python
.sort_index()
```

Why?

Without it, `value_counts()` sorts by frequency:

```text
3
1
2
```

But passenger class has a natural order:

```text
1
2
3
```

Sorting by index preserves that order and makes the chart easier to interpret.

This is a small detail, but it's an example of thoughtful analysis.

---

# Step 5 — Ask Questions

Now become an investigator.

Don't rush to conclusions.

Ask:

* Why are there so many third-class passengers?
* Does this reflect the social structure of the time?
* Could passenger class influence survival?
* Could passenger class influence cabin assignment?
* Could passenger class influence ticket fare?

Again, these are **questions**, not answers.

---

# Step 6 — Think About Machine Learning

Imagine you later train a model.

Will `Pclass` be useful?

Possibly.

But remember:

Although it is stored as:

```text
1
2
3
```

it is **not** like:

```text
Age

22
23
24
```

The numbers represent **ordered categories**, not continuous quantities.

That distinction affects preprocessing.

---

# Architecture Perspective

Think about API status codes.

```text
200
404
500
```

They're numbers.

But you don't average them.

You don't say:

```text
500

is 2.5× bigger than

200
```

The numbers are identifiers with meaning.

`Pclass` is similar.

The numeric value encodes an ordered category.

---

# Hands-On Exercise

Create a new notebook section:

```text
Feature Investigation – Pclass
```

Run:

```python
# Counts
df["Pclass"].value_counts()
```

```python
# Percentages
(df["Pclass"].value_counts(normalize=True) * 100).round(2)
```

```python
# Visualization
import matplotlib.pyplot as plt

df["Pclass"].value_counts().sort_index().plot(kind="bar")

plt.title("Passenger Distribution by Class")
plt.xlabel("Passenger Class")
plt.ylabel("Count")

plt.show()
```

Save the chart in your `screenshots/` folder.

---

# 🎯 Mini Assignment

## Q1

How many passengers traveled in each class?

What percentage of the dataset does each class represent?

---

## Q2

Why is `Pclass` considered an **ordinal categorical feature** instead of a continuous numerical feature?

Explain in your own words.

---

## Q3

Suppose the CSV stored:

```text
First Class
Second Class
Third Class
```

instead of:

```text
1
2
3
```

Would the meaning of the feature change?

Why or why not?

---

## Q4

List three hypotheses about how `Pclass` *might* relate to survival.

Remember:

These are hypotheses—not conclusions.

---

## Q5

Write a short **Feature Investigation Report** for the `Pclass` column.

Include:

* Feature type
* Distribution
* Missing values
* Possible importance for machine learning

---

# 🌟 Mentor Insight

Today's lesson is bigger than `Pclass`.

You're learning an important distinction:

* **Representation**: How the data is stored.
* **Meaning**: What the data actually represents.

A computer only sees:

```text
1
2
3
```

But an AI engineer sees:

```text
First Class
Second Class
Third Class
```

That ability to look beyond the raw values and understand their semantics is one of the reasons experienced engineers make better preprocessing decisions.

As we continue through the remaining features, keep asking yourself:

> "Am I looking at the numbers, or am I understanding what those numbers mean?"

That question will stay valuable long after we've finished the Titanic project.
