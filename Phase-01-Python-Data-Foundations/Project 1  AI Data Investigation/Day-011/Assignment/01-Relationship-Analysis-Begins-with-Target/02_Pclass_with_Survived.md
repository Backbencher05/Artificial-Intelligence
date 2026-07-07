# Day 011 Mini Assignment – Relationship Analysis: Pclass ↔ Survived

This analysis helps us answer:

> **"Does a passenger's travel class influence their survival?"**

Remember, **Pclass is a feature**, and **Survived is the target variable**.

---

# Q1. What does the crosstab table tell you?

Your crosstab:

| Pclass | Did Not Survive (0) | Survived (1) |
| -----: | ------------------: | -----------: |
|      1 |                  80 |          136 |
|      2 |                  97 |           87 |
|      3 |                 372 |          119 |

---

## What do the Rows represent?

Each row represents a **passenger class**.

```text
1 → First Class
2 → Second Class
3 → Third Class
```

Passengers are grouped according to the class in which they traveled.

---

## What do the Columns represent?

The columns represent the two possible values of the **Survived** feature.

```text
0 → Did Not Survive

1 → Survived
```

---

## What do the Values represent?

The values are the **number of passengers** belonging to each combination of passenger class and survival status.

Examples:

```text
First Class → 136
```

means:

> **136 First Class passengers survived.**

Similarly,

```text
Third Class → 372
```

means:

> **372 Third Class passengers did not survive.**

So the crosstab answers:

> **"How many passengers from each passenger class survived or did not survive?"**

---

# Q2. Using the percentage table, compare the survival rates of each class.

Your normalized table:

| Pclass | Did Not Survive | Survived |
| -----: | --------------: | -------: |
|    1st |          37.04% |   62.96% |
|    2nd |          52.72% |   47.28% |
|    3rd |          75.76% |   24.24% |

### Observations

* **First Class** passengers had the highest survival rate (**62.96%**).
* **Second Class** passengers had a survival rate of **47.28%**.
* **Third Class** passengers had the lowest survival rate (**24.24%**).
* The survival rate decreases as passenger class changes from **1st → 2nd → 3rd**.
* The percentage of passengers who did not survive increases from **37.04%** in First Class to **75.76%** in Third Class.

These are observations only—we are not explaining the reasons yet.

---

# Q3. Does the data support your earlier hypotheses?

Yes.

Earlier, I proposed the following hypotheses:

* First Class passengers may have had higher survival rates.
* Third Class passengers may have had lower survival rates.
* Passenger class might be an important predictor of survival.

The data supports these hypotheses.

The survival rates are:

```text
First Class  → 62.96%

Second Class → 47.28%

Third Class  → 24.24%
```

This shows a clear pattern:

* First Class passengers survived at the highest rate.
* Third Class passengers survived at the lowest rate.
* Second Class passengers fall between the two.

However, this shows **association**, not causation. Other factors such as **Sex**, **Age**, or **Fare** may also contribute to this relationship.

---

# Q4. Why do we use `normalize="index"` instead of only looking at raw counts?

Raw counts can be misleading because **each passenger class contains a different number of passengers**.

For example:

| Pclass | Total Passengers |
| -----: | ---------------: |
|      1 |              216 |
|      2 |              184 |
|      3 |              491 |

Third Class has **491 passengers**, while First Class has only **216**.

If we only compare survivor counts:

```text
First Class Survivors = 136

Third Class Survivors = 119
```

It appears that First Class had only slightly more survivors.

But percentages tell the real story:

```text
First Class

136 / 216 = 62.96%

Third Class

119 / 491 = 24.24%
```

Now we can compare the classes fairly.

`normalize="index"` converts each row into percentages, so every row totals **100%**.

This allows us to answer questions such as:

> **"Out of all First Class passengers, what percentage survived?"**

instead of simply counting passengers.

---

# Q5. Relationship Investigation Report – Pclass ↔ Survived

### Relationship Observed

There is a clear relationship between **Passenger Class** and **Survival**.

Passengers traveling in higher classes had higher survival rates, while passengers in lower classes had lower survival rates.

---

### Strength of the Relationship

The relationship appears to be **strong**.

Survival rates differ substantially:

* **First Class:** 62.96%
* **Second Class:** 47.28%
* **Third Class:** 24.24%

This consistent trend suggests that passenger class is closely associated with survival.

---

### Does Pclass appear useful for prediction?

Yes.

Based on this analysis, **Pclass appears to be an important predictive feature** because the survival probability changes significantly across the three passenger classes.

It is likely to contribute valuable information to a machine learning model.

---

### New Questions Raised

This analysis raises several interesting questions:

* Did females in Third Class survive at the same rate as females in First Class?
* Does **Fare** explain some of the relationship between passenger class and survival?
* Did **Age** influence survival differently within each passenger class?
* Are passengers with recorded cabins mostly from First Class?
* Does combining **Pclass** with **Sex** improve prediction accuracy compared to using either feature alone?

These questions can be explored in the next stages of EDA.

---

# 🌟 Mentor Feedback

Today's analysis reveals an important pattern that appears frequently in machine learning:

```text
One Feature
        ↓
Target Variable
        ↓
Strong Relationship
```

Earlier, you discovered:

```text
Sex
      ↓
Survival
```

Now you've discovered:

```text
Pclass
       ↓
Survival
```

This tells us something important:

**A good machine learning model is built by finding features that show meaningful relationships with the target variable.**

---

## 🧠 One More Important Insight

Notice the trend in the survival percentages:

```text
First Class   → 62.96%

Second Class  → 47.28%

Third Class   → 24.24%
```

This is not a random pattern.

It shows a **consistent decrease** in survival rate as passenger class decreases.

When you see this kind of ordered trend during EDA, it's a strong indication that the feature may contain useful predictive information.

As you continue your Titanic project, you'll begin combining features—for example:

```text
Sex
   +
Pclass
   +
Age
        ↓
Predict Survival
```

This is exactly how machine learning models work: they learn from the combined information provided by multiple features rather than relying on a single column.
