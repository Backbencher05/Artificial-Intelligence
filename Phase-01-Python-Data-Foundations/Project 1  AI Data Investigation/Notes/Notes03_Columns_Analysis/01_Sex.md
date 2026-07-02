# All Columns
- 




Excellent.

Now we enter what I consider **the heart of EDA**.

Until now we've been asking:

> **Is the data healthy?**

Now we ask:

> **What story is the data trying to tell us?**

This is where you stop being a programmer and start becoming an investigator.

---

# 🚀 Project 1 – AI Data Investigation

# Step 4 — Feature Investigation (The Story Behind Every Column)

Today, we're going to investigate **one feature at a time**.

Not because we don't know Pandas.

Because **every feature deserves its own investigation**.

---

# Before Writing Any Code...

I want to ask you a question.

Imagine you work at a company.

Your manager asks:

> **"Can you tell me which factors influenced survival?"**

What would you do?

Many beginners immediately jump to:

```python
df.corr()
```

But a professional first asks:

> **"Let's understand each feature individually."**

---

# Today's Investigation Strategy

We're going to use the same process for every important feature.

```text
Choose One Feature
        ↓
Understand What It Represents
        ↓
Inspect Its Values
        ↓
Visualize It
        ↓
Ask Business Questions
        ↓
Document Findings
```

Notice something.

We're not just generating graphs.

We're asking questions.

---

# Which Feature Should We Start With?

Let's start with:

```text
# Sex
```

Why not Age?

Why not Fare?

Because **Sex is simple**, and it will teach us the process.

---

# Step 4.1 – Understand the Feature

Question:

What does `Sex` represent?

Answer:

The biological sex of the passenger.

Possible values:

```text
male
female
```

Question:

Is it:

* Numerical?

No.

* Categorical?

Yes.

* Nominal?

Yes.

Good.

---

# Step 4.2 – Inspect the Values

Run:

```python
df["Sex"].value_counts()
```

You'll get something similar to:

```text
male      577
female    314
```

Stop.

Don't move on.

Think.

---

# Investigator Mindset

Ask:

Is the dataset balanced?

No.

More males than females.

Interesting.

---

# Step 4.3 – Convert Counts into Percentages

Run:

```python
(df["Sex"].value_counts(normalize=True) * 100).round(2)
```

Example output:

```text
male      64.76
female    35.24
```

Now you have context.

Again, percentages matter.

---

# Why Do We Care?

Imagine a dataset with:

```text
99% Male
1% Female
```

Would that affect a machine learning model?

Absolutely.

Class imbalance in features can influence how models learn patterns and how we interpret results.

---

# Step 4.4 – Visualize the Feature

Now create a simple bar chart.

```python
import matplotlib.pyplot as plt

df["Sex"].value_counts().plot(kind="bar")

plt.title("Passenger Distribution by Sex")
plt.xlabel("Sex")
plt.ylabel("Number of Passengers")

plt.show()
```

---

# Don't Just Look at the Graph

Ask questions.

For example:

* Which category is larger?
* By how much?
* Is anything surprising?

The graph is evidence.

Your observations are the investigation.

---

# Step 4.5 – Connect It to the Business Problem

Remember our goal.

We're not studying passengers.

We're studying:

```text
Survival
```

Now ask:

> Could Sex influence survival?

Don't answer from history.

Answer like an investigator.

You don't know yet.

But it **might**.

That's a hypothesis.

We'll test it later.

---

# Engineering Thinking

Notice what we're doing.

We are separating:

### Observation

```text
More males than females.
```

from

### Conclusion

```text
Therefore males survived less.
```

We **cannot** conclude that yet.

That would be a mistake.

EDA is about avoiding premature conclusions.

---

# The Scientific Method

This is exactly how AI engineers think.

```text
Observation
        ↓
Hypothesis
        ↓
Evidence
        ↓
Conclusion
```

Right now we only have:

Observation.

---

# Let's Compare With Backend Engineering

Suppose your API latency increases.

Do you immediately conclude:

> Database is slow.

No.

You first observe:

* Logs
* Metrics
* CPU
* Memory

Only then conclude.

EDA follows the same principle.

---

# Hands-On Exercise

In your notebook, create a new section:

```text
Feature Investigation – Sex
```

Run:

```python
# Count values
df["Sex"].value_counts()
```

```python
# Percentage distribution
(df["Sex"].value_counts(normalize=True) * 100).round(2)
```

```python
# Visualization
import matplotlib.pyplot as plt

df["Sex"].value_counts().plot(kind="bar")

plt.title("Passenger Distribution by Sex")
plt.xlabel("Sex")
plt.ylabel("Count")

plt.show()
```

Take a screenshot of the chart and save it in your `screenshots/` folder.

This is part of documenting your investigation.

---

# 🎯 Mini Assignment

Answer these questions after running the code.

### Q1

How many male and female passengers are in the dataset?

What percentage does each represent?

---

### Q2

Is the `Sex` feature balanced?

Why or why not?

---

### Q3

Without looking at the `Survived` column yet, write **three hypotheses** about how the `Sex` feature *might* relate to survival.

These are hypotheses, not conclusions.

Example:

> "Female passengers may have had a higher survival rate."

Don't worry about being right—we'll verify later.

---

### Q4

Why is it important to separate **observation** from **conclusion** during EDA?

---

### Q5

Write a short **Feature Investigation Report** for the `Sex` column (4–6 bullet points).

Imagine another AI engineer will read your report without opening the dataset.

---

# 🌟 Mentor Insight

I want to explain why we're investigating **one feature at a time** instead of jumping into complex analysis.

Many beginners open a dataset and immediately run dozens of commands:

```python
df.describe()
df.corr()
plt.hist(...)
sns.pairplot(...)
```

They generate a lot of output, but they don't build understanding.

We're doing the opposite.

We're slowing down and asking:

* What does this feature represent?
* What do its values look like?
* Could it be useful?
* What questions does it raise?

By the time we finish investigating the major features (`Sex`, `Age`, `Pclass`, `Fare`, `Embarked`), you'll have a mental model of the dataset—not just a notebook full of charts.

And that mental model is what will make Phase 2 (Machine Learning) much more intuitive, because you'll already understand the data before asking a model to learn from it.

