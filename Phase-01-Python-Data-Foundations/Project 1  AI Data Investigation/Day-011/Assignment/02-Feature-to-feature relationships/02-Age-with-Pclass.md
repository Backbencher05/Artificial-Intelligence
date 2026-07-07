# Day 011 Mini Assignment – Relationship Analysis: Age ↔ Pclass

This is another **feature-to-feature relationship analysis**.

Here we're asking:

> **"Is the age of a passenger associated with the passenger class?"**

We'll answer this using both **summary statistics** and a **box plot**.

---

# Q1. Explain the output of:

```python
df.groupby("Pclass")["Age"].mean()
```

and

```python
df.groupby("Pclass")["Age"].median()
```

### What do the groups represent?

`groupby("Pclass")` divides all passengers into **three groups** based on their travel class:

```text
Pclass = 1 → First Class

Pclass = 2 → Second Class

Pclass = 3 → Third Class
```

For each group, Pandas calculates statistics for the **Age** column separately.

---

### What does the mean tell you?

The mean tells us the **average age** of passengers in each class.

Your output:

| Passenger Class | Mean Age |
| --------------- | -------: |
| First Class     |    38.23 |
| Second Class    |    29.88 |
| Third Class     |    25.14 |

This represents the average age of passengers traveling in each class.

---

### What does the median tell you?

The median tells us the **middle age** of passengers within each class after sorting them by age.

Your output:

| Passenger Class | Median Age |
| --------------- | ---------: |
| First Class     |         37 |
| Second Class    |         29 |
| Third Class     |         24 |

The median is less affected by unusually young or old passengers than the mean.

---

# Q2. Compare the average and median ages across the three passenger classes.

### Observations

* **First Class** passengers have the highest average age (**38.23 years**).
* **Second Class** passengers have an average age of approximately **29.88 years**.
* **Third Class** passengers have the lowest average age (**25.14 years**).
* The median ages follow the same pattern: **37 → 29 → 24**.
* Both the mean and median decrease consistently from **First Class** to **Third Class**.

These are observations only. We are not explaining the reasons.

---

# Q3. Study the box plot carefully.

### Observation 1

The median age is highest for **First Class**, lower for **Second Class**, and lowest for **Third Class**.

---

### Observation 2

The age ranges of all three passenger classes overlap.

Passengers of similar ages appear in multiple classes.

---

### Observation 3

Each passenger class contains both younger and older passengers.

No class is limited to a narrow age range.

---

### Observation 4

There are outliers in one or more classes, indicating a few passengers whose ages are much higher or lower than the majority of that class.

---

### Observation 5

The spread of ages appears fairly similar across the three classes, although the center of the distribution shifts downward from First Class to Third Class.

---

### Observation 6

The distributions are not completely separated; instead, they overlap while having different central values (medians).

---

# Q4. Based on today's investigation, does Age appear to be related to Pclass?

Yes.

The data suggests an **association** between **Age** and **Passenger Class**.

Evidence from the summary statistics:

| Pclass | Mean Age | Median Age |
| -----: | -------: | ---------: |
|      1 |    38.23 |         37 |
|      2 |    29.88 |         29 |
|      3 |    25.14 |         24 |

Both the mean and median decrease consistently from **First Class** to **Third Class**.

The box plot supports this observation by showing that the center of the age distribution is higher for First Class than for the other two classes.

However, the box plot also shows substantial overlap between the classes, meaning passengers of similar ages can be found in all three groups.

Therefore, **Age is associated with Passenger Class**, but the relationship is not absolute.

---

# Q5. Relationship Investigation Report – Age ↔ Pclass

### Relationship Observed

There is a noticeable relationship between **Age** and **Passenger Class**.

Passengers in higher classes tend to be older on average, while passengers in lower classes tend to be younger.

This trend is visible in both the summary statistics and the box plot.

---

### Does the relationship appear strong or weak?

The relationship appears **moderate** rather than strong.

Although the average and median ages differ across classes, the box plot shows considerable overlap between the age distributions.

This indicates that age alone cannot reliably determine a passenger's class.

---

### Do both features provide different kinds of information?

Yes.

* **Age** describes a passenger's biological characteristic.
* **Pclass** describes the passenger's travel category.

Although they are associated, they represent different aspects of the passenger and are likely to provide complementary information to a machine learning model.

---

### New Questions Raised

This analysis raises several interesting questions:

* Are younger passengers more likely to travel in Third Class?
* Does the relationship between Age and Passenger Class affect survival?
* Within each passenger class, do younger passengers have higher survival rates?
* Does combining **Age**, **Pclass**, and **Sex** improve prediction accuracy?
* Are the age distributions similar for males and females within each passenger class?

These questions can be explored in future EDA.

---

# 🌟 Mentor Feedback

Today's analysis teaches an important lesson about **association strength**.

Compare the relationships you've studied:

| Relationship          | Strength    |
| --------------------- | ----------- |
| **Sex ↔ Survived**    | Very Strong |
| **Pclass ↔ Survived** | Strong      |
| **Fare ↔ Pclass**     | Strong      |
| **Age ↔ Pclass**      | Moderate    |

Notice why **Age ↔ Pclass** is only moderate:

* The **means and medians** clearly differ.
* But the **box plots overlap**.

That overlap is important.

Imagine two passengers:

| Passenger | Age | Pclass |
| --------- | --: | :----: |
| A         |  30 |    1   |
| B         |  30 |    3   |

They are the **same age** but belong to different passenger classes.

This tells us that **age influences the distribution of passenger class**, but it **does not uniquely determine it**.

---

## 🧠 Key EDA Principle

When analyzing relationships, don't rely on just one statistic.

Follow this sequence:

```text
Summary Statistics
        ↓
Means & Medians
        ↓
Visualization (Box Plot)
        ↓
Observe Overlap
        ↓
Judge Relationship Strength
```

A difference in averages tells you that groups are different **on average**.

A box plot tells you **how much the groups actually overlap**.

Using both together leads to much more reliable conclusions than relying on either one alone.
