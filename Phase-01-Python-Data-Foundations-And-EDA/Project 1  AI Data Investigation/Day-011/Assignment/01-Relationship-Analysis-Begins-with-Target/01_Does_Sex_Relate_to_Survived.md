# Day 011 Mini Assignment – Relationship Analysis: Sex ↔ Survived

This is an important milestone.

Until now, we've been analyzing **individual features** (Age, Fare, Pclass, etc.).

Now we're asking:

> **"How does one feature relate to the target variable?"**

This is one of the most important goals of EDA.

---

# Q1. What does `pd.crosstab(df["Sex"], df["Survived"])` show?

`pd.crosstab()` creates a **cross-tabulation table** that shows how two categorical variables are related.

In this case, it compares:

* **Sex** (Male/Female)
* **Survived** (0 = No, 1 = Yes)

Your table:

| Sex    | Did Not Survive (0) | Survived (1) |
| ------ | ------------------: | -----------: |
| Female |                  81 |          233 |
| Male   |                 468 |          109 |

---

## What do the Rows represent?

Each row represents one category of the **Sex** feature.

```text
Female

Male
```

We're grouping passengers based on their gender.

---

## What do the Columns represent?

Each column represents one category of the **Survived** feature.

```text
0 → Did Not Survive

1 → Survived
```

---

## What do the Values represent?

The values are simply **counts**.

For example:

```text
Female → 233
```

means:

> **233 female passengers survived.**

Similarly,

```text
Male → 468
```

means:

> **468 male passengers did not survive.**

So `crosstab()` answers:

> **"How many passengers from each sex belong to each survival category?"**

---

# Q2. Using the percentage table, compare the survival rates of male and female passengers.

From your normalized table:

| Sex    | Did Not Survive | Survived |
| ------ | --------------: | -------: |
| Female |          25.80% |   74.20% |
| Male   |          81.11% |   18.89% |

### Observations

* Approximately **74.20% of female passengers survived**.
* Approximately **25.80% of female passengers did not survive**.
* Approximately **18.89% of male passengers survived**.
* Approximately **81.11% of male passengers did not survive**.
* The survival rate for female passengers is much higher than the survival rate for male passengers.

These are **observations only**. We are not yet explaining *why* this pattern exists.

---

# Q3. Does the data support your earlier hypothesis?

Yes.

Earlier, I proposed the hypothesis:

> **"Female passengers may have had a higher survival rate than male passengers."**

The data supports this hypothesis.

The percentage table shows:

```text
Female Survival Rate = 74.20%

Male Survival Rate = 18.89%
```

This is a large difference, indicating that female passengers survived at a much higher rate than male passengers.

However, this confirms **only the observed relationship**.

It does **not** prove that being female was the direct cause of survival. Other factors such as passenger class, age, or evacuation policies may also have contributed.

---

# Q4. Why are percentages often more useful than raw counts when comparing groups of different sizes?

Raw counts can be misleading when the groups being compared are different sizes.

For example:

| Sex    | Total Passengers |
| ------ | ---------------: |
| Male   |              577 |
| Female |              314 |

Since there are far more male passengers than female passengers, comparing only counts doesn't tell the whole story.

Example:

```text
Female Survivors = 233

Male Survivors = 109
```

At first glance, it looks like more females survived.

But percentages tell us the true survival rates:

```text
Female

233 / 314 = 74.20%

Male

109 / 577 = 18.89%
```

Percentages allow us to compare groups fairly, regardless of how many observations each group contains.

This is the same reason we preferred percentages over raw counts when analyzing missing values.

---

# Q5. Relationship Investigation Report – Sex ↔ Survived

### Relationship Observed

There is a clear relationship between **Sex** and **Survived**. Female passengers had a much higher survival rate than male passengers.

---

### Strength of the Relationship

The relationship appears to be **strong**.

* Female survival rate: **74.20%**
* Male survival rate: **18.89%**

The difference between the two groups is substantial.

---

### Does Sex appear to be an important feature?

Yes.

Based on this analysis, **Sex appears to be one of the strongest candidate features** for predicting survival because the survival rates differ significantly between males and females.

However, additional analysis is needed to determine whether this relationship remains strong after considering other variables.

---

### Further Questions Raised

This relationship raises several questions:

* Does passenger class influence this relationship?
* Did survival rates differ for males and females within each passenger class?
* Did age interact with sex (e.g., were boys treated differently from adult men)?
* Is the relationship consistent across different fare ranges?
* Would combining **Sex** with **Pclass** or **Age** improve prediction accuracy?

These questions can be explored in future EDA.

---

# 🌟 Mentor Feedback

Today's lesson introduces one of the biggest ideas in Exploratory Data Analysis:

```text
Single Feature Analysis
        ↓
"What does this feature look like?"

Relationship Analysis
        ↓
"How does this feature relate to the target?"
```

For example:

```text
Sex
      ↓
Distribution
```

tells you:

> "How many males and females are in the dataset?"

But:

```text
Sex
      ↓
Survived
```

tells you:

> "Does survival differ between males and females?"

That's a much more valuable question for machine learning because you're evaluating whether a feature helps predict the target.

---

## 🧠 One More Important Concept

Notice the difference between these two `normalize` options:

```python
pd.crosstab(df["Sex"], df["Survived"], normalize="index")
```

This calculates **row-wise percentages**.

For females:

```text
81 + 233 = 314
```

Then:

```text
81 / 314 = 25.80%
233 / 314 = 74.20%
```

For males:

```text
468 + 109 = 577
```

Then:

```text
468 / 577 = 81.11%
109 / 577 = 18.89%
```

Each **row adds up to 100%**, making it perfect for answering:

> **"Out of all female passengers, what percentage survived?"**

or

> **"Out of all male passengers, what percentage survived?"**

This is why `normalize="index"` is commonly used when comparing survival rates across different groups. It allows you to compare groups fairly even when the number of observations in each group is different.
