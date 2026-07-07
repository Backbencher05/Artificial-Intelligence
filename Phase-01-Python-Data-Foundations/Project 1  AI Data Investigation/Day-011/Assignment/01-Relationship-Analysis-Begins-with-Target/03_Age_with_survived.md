# Day 011 Mini Assignment – Relationship Analysis: Age ↔ Survived

This is your **first relationship analysis involving a numerical feature**.

Notice the difference:

* **Sex ↔ Survived** → Categorical vs Categorical → `crosstab()`
* **Pclass ↔ Survived** → Categorical vs Categorical → `crosstab()`
* **Age ↔ Survived** → Numerical vs Categorical → `groupby()` + histograms

The analysis technique changes depending on the type of feature.

---

# Q1. Explain the output of:

```python
df.groupby("Survived")["Age"].mean()
```

and

```python
df.groupby("Survived")["Age"].median()
```

### What do the groups represent?

`groupby("Survived")` divides the dataset into **two groups**:

```text
Survived = 0
```

Passengers who **did not survive**

and

```text
Survived = 1
```

Passengers who **survived**

Instead of analyzing everyone together, we analyze each group separately.

---

### What does the mean tell you?

```text
Survived = 0 → Mean Age = 30.63

Survived = 1 → Mean Age = 28.34
```

The mean tells us the **average age** of passengers in each survival group.

It answers questions like:

> "What was the average age of passengers who survived?"

and

> "What was the average age of passengers who did not survive?"

---

### What does the median tell you?

```text
Survived = 0 → Median = 28

Survived = 1 → Median = 28
```

The median tells us the **middle age** in each group after sorting the passengers by age.

It is less affected by unusually young or old passengers than the mean.

---

# Q2. Compare the average and median ages.

### Observations

* The average age of **non-survivors** is approximately **30.63 years**.
* The average age of **survivors** is approximately **28.34 years**.
* The average age of non-survivors is slightly higher than that of survivors.
* The median age is **28 years** for both groups.
* Although the means differ slightly, the medians are identical.

These are observations only. We are not yet explaining why.

---

# Q3. Histogram Observations

From the histogram, I observe:

### Observation 1

Both survivors and non-survivors are spread across a wide range of ages.

---

### Observation 2

Most passengers in both groups appear to be between **20 and 40 years old**.

---

### Observation 3

There are survivors and non-survivors in almost every age group.

---

### Observation 4

The distributions of the two groups overlap considerably.

---

### Observation 5

There are relatively few passengers at very high ages (above approximately 70 years) in either group.

These are direct observations from the visualization without interpreting the reasons.

---

# Q4. Does the data support your earlier hypotheses?

### Hypothesis 1

> **Children may survive more.**

**Partially supported, but requires further investigation.**

The histogram suggests that young children are present among survivors, but the averages alone are not sufficient to confirm this.

A more detailed age-group analysis would be needed.

---

### Hypothesis 2

> **Elderly passengers may survive less.**

**Requires further investigation.**

There are relatively few elderly passengers overall, making it difficult to draw conclusions based only on the histogram and summary statistics.

---

### Hypothesis 3

> **Age alone may not explain survival.**

**Supported.**

The mean ages differ only slightly:

```text
30.63 vs 28.34
```

and both groups have the same median:

```text
28 years
```

The large overlap in the histogram also suggests that age by itself does not fully explain survival.

---

# Q5. Relationship Investigation Report – Age ↔ Survived

### Relationship Observed

There is a relationship between **Age** and **Survival**, but it appears to be much weaker than the relationships observed for **Sex** or **Pclass**.

The average age of survivors is slightly lower than that of non-survivors, while the median age is identical for both groups.

---

### Does Age appear useful for prediction?

Yes, but probably not as a standalone feature.

Age may contribute useful information when combined with other features such as:

* Sex
* Passenger Class
* Fare

Its predictive value should be evaluated together with these variables rather than independently.

---

### Limitations of Using Only Averages

Averages summarize an entire group into a single number.

This can hide important patterns.

For example:

* Two groups may have the same average but very different distributions.
* The histogram shows substantial overlap between survivors and non-survivors, which the averages alone do not reveal.
* The identical median indicates that the center of both distributions is the same, despite the difference in means.

Therefore, averages should always be interpreted alongside visualizations and other statistics.

---

### New Questions Raised

This analysis raises several questions:

* Do children have higher survival rates than adults?
* Does the relationship between age and survival differ across passenger classes?
* Is age more important for males than females?
* Would grouping passengers into age categories reveal clearer patterns?
* Does combining **Age**, **Sex**, and **Pclass** improve prediction accuracy?

These questions can be explored in future EDA.

---

# 🌟 Mentor Feedback

Today you discovered something very important about data analysis:

Not every feature has an **obvious** relationship with the target.

Compare what you've learned so far:

| Feature    | Relationship with Survival |
| ---------- | -------------------------- |
| **Sex**    | Very Strong                |
| **Pclass** | Strong                     |
| **Age**    | Moderate / Less Obvious    |

This teaches an important lesson:

> **Some features reveal their predictive power immediately, while others require deeper analysis.**

---

## 🧠 One More Important Concept

Notice what happened when you looked only at the averages:

```text
Mean Age

Did Not Survive → 30.63

Survived → 28.34
```

The difference seems small.

Now look at the medians:

```text
Median Age

Did Not Survive → 28

Survived → 28
```

They are identical.

If you stopped here, you might conclude:

> **"Age doesn't matter."**

But then you plotted the histogram.

The histogram shows **how the ages are distributed**, not just the center.

This is why experienced AI engineers **never rely on a single statistic**.

Their thought process is:

```text
Summary Statistics
        ↓
Visualizations
        ↓
Relationships
        ↓
Conclusions
```

Each step adds more evidence, leading to better and more reliable insights.
