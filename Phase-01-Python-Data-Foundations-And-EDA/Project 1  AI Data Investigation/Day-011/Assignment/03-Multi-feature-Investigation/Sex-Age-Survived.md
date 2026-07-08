# Day 011 Mini Assignment – Multi-Feature Analysis: Sex + Pclass ↔ Survived

This is a very important step in EDA.

Until now, you analyzed **one feature at a time**:

```text
Sex → Survived
Pclass → Survived
Age → Survived
Fare → Survived
```

Now you're asking:

> **"What happens when we combine two features?"**

This is closer to how machine learning models actually work.

---

# Q1. Explain the crosstab.

```python
pd.crosstab(
    [df["Sex"], df["Pclass"]],
    df["Survived"]
)
```

### What do the rows represent?

The rows represent **every combination of Sex and Passenger Class**.

Instead of grouping only by `Sex` or only by `Pclass`, we group by both.

For example:

| Row       | Meaning                           |
| --------- | --------------------------------- |
| Female, 1 | Female passengers in First Class  |
| Female, 2 | Female passengers in Second Class |
| Female, 3 | Female passengers in Third Class  |
| Male, 1   | Male passengers in First Class    |
| Male, 2   | Male passengers in Second Class   |
| Male, 3   | Male passengers in Third Class    |

---

### What do the columns represent?

The columns represent the survival outcome.

| Column | Meaning         |
| -----: | --------------- |
|      0 | Did not survive |
|      1 | Survived        |

---

### What do the values represent?

The values are the **number of passengers** in each combination.

Example:

```text
Female, First Class

0 → 3

1 → 91
```

Meaning:

* **3 First Class females did not survive.**
* **91 First Class females survived.**

Similarly:

```text
Male, Third Class

0 → 300

1 → 47
```

Meaning:

* **300 Third Class males did not survive.**
* **47 Third Class males survived.**

---

# Q2. Compare the survival rates.

### Female passengers

| Class        | Survival Rate |
| ------------ | ------------: |
| First Class  |    **96.81%** |
| Second Class |    **92.11%** |
| Third Class  |    **50.00%** |

### Observations

* Female passengers have high survival rates in all classes.
* **First Class females** have the highest survival rate (**96.81%**).
* **Second Class females** also have a very high survival rate (**92.11%**).
* **Third Class females** have a noticeably lower survival rate (**50%**) compared with females in the other two classes.

---

### Male passengers

| Class        | Survival Rate |
| ------------ | ------------: |
| First Class  |    **36.89%** |
| Second Class |    **15.74%** |
| Third Class  |    **13.54%** |

### Observations

* Male passengers have lower survival rates than female passengers in every class.
* **First Class males** have the highest survival rate among males (**36.89%**).
* **Second Class males** survive less frequently (**15.74%**).
* **Third Class males** have the lowest survival rate (**13.54%**).

These are observations only.

---

# Q3. Study the bar chart.

### Observation 1

The highest survival rate belongs to **First Class females**.

---

### Observation 2

The lowest survival rate belongs to **Third Class males**.

---

### Observation 3

Within both males and females, survival decreases as passenger class changes from **First → Second → Third**.

---

### Observation 4

Within every passenger class, females have a higher survival rate than males.

---

### Observation 5

The difference between males and females is especially large in **Second** and **Third Class**.

---

### Observation 6

No male group has a survival rate higher than any female group in the same passenger class.

---

# Q4. Which appears to have the stronger influence on survival?

The analysis suggests that **both Sex and Passenger Class work together** to influence survival.

Evidence:

* Within **every passenger class**, females survive at much higher rates than males.

For example:

| Class  | Female |   Male |
| ------ | -----: | -----: |
| First  | 96.81% | 36.89% |
| Second | 92.11% | 15.74% |
| Third  | 50.00% | 13.54% |

This shows that **Sex** has a very strong association with survival.

At the same time:

* Within females, survival decreases from First to Third Class.
* Within males, survival also decreases from First to Third Class.

This shows that **Passenger Class** also has a clear association with survival.

Therefore, the evidence suggests that **Sex and Passenger Class together provide a much better understanding of survival than either feature alone**.

---

# Q5. Relationship Investigation Report – Sex + Pclass ↔ Survived

### Relationship Observed

Survival is associated with both **Sex** and **Passenger Class**.

Female passengers consistently have higher survival rates than male passengers.

Within each sex, survival rates decrease as passenger class changes from First to Third.

This indicates that both features contribute to explaining survival.

---

### Why does analyzing both features together provide more insight?

When we analyzed **Sex** alone, we learned that females survived more often.

When we analyzed **Pclass** alone, we learned that First Class passengers survived more often.

By combining the two features, we discover a more detailed pattern:

* First Class females have exceptionally high survival rates.
* Third Class females survive much less often than First or Second Class females.
* First Class males survive more often than other male groups, but still much less than females.

These insights cannot be seen by analyzing either feature independently.

---

### Does this combination appear valuable for machine learning?

Yes.

The combination of **Sex** and **Passenger Class** appears highly valuable for prediction because it captures more detailed patterns than either feature alone.

A machine learning model can use both features together to make more accurate predictions.

---

### New Questions Raised

This analysis raises several interesting questions:

* How does **Age** interact with Sex and Passenger Class?
* Did children in Third Class survive more often than adults?
* Does Fare provide additional information beyond Passenger Class?
* Would adding Cabin information further improve prediction?
* Which combination of features provides the best prediction of survival?

These questions can be explored in later stages of EDA.

---

# 🌟 Mentor Feedback

Today's analysis is a major milestone.

Until now, your thinking looked like this:

```text
One Feature
      ↓
Target
```

Now it has evolved to:

```text
Multiple Features
        ↓
Target
```

This is much closer to how real machine learning works.

A model doesn't usually make decisions based on just one feature.

Instead, it combines information from many features simultaneously.

Think about these two passengers:

| Passenger | Sex    | Pclass |
| --------- | ------ | :----: |
| A         | Female |    3   |
| B         | Male   |    1   |

If you looked only at **Sex**, you might predict Passenger A is more likely to survive.

If you looked only at **Pclass**, you might predict Passenger B is more likely to survive.

But when you analyze **both features together**, you get a much richer picture of survival probabilities.

---

## 🧠 The Biggest Lesson of Day 11

Your journey over today's analyses can be summarized like this:

```text
Single Feature Analysis
        ↓
"What does this feature look like?"

Relationship Analysis
        ↓
"How does this feature relate to survival?"

Multi-Feature Analysis
        ↓
"How do multiple features work together?"
```

That final step is the foundation of machine learning.

Algorithms such as Logistic Regression, Decision Trees, Random Forests, and Neural Networks don't rely on one feature at a time—they learn patterns from **many features together**.

You're now beginning to think the way a machine learning model "sees" the data: not as isolated columns, but as combinations of information that together help predict the target.
