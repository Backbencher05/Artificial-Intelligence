# Day 011 Mini Assignment – Relationship Analysis: Fare ↔ Survived

This is another example of analyzing a **numerical feature** against the target variable.

Just like **Age ↔ Survived**, we use:

* `groupby()` → Summary statistics
* Histogram → Distribution comparison

---

# Q1. Explain the output of:

```python
df.groupby("Survived")["Fare"].mean()
```

and

```python
df.groupby("Survived")["Fare"].median()
```

### What do the groups represent?

`groupby("Survived")` divides the dataset into two groups:

```text
Survived = 0
```

Passengers who **did not survive**

and

```text
Survived = 1
```

Passengers who **survived**

Each group's fare statistics are then calculated separately.

---

### What does the mean tell you?

The mean tells us the **average fare paid** by passengers in each survival group.

Your output:

| Survived | Mean Fare |
| -------- | --------: |
| 0        |     22.12 |
| 1        |     48.40 |

This means:

* Passengers who **did not survive** paid an average fare of approximately **22.12**.
* Passengers who **survived** paid an average fare of approximately **48.40**.

---

### What does the median tell you?

The median tells us the **middle fare** in each survival group after sorting all fares from lowest to highest.

Your output:

| Survived | Median Fare |
| -------- | ----------: |
| 0        |       10.50 |
| 1        |       26.00 |

This means:

* Half of the non-survivors paid **₹10.50 or less**.
* Half of the survivors paid **₹26.00 or less**.

The median is less affected by extremely expensive tickets than the mean.

---

# Q2. Compare the average and median fares.

### Observations

* The average fare of **survivors (48.40)** is much higher than that of **non-survivors (22.12)**.
* The median fare of **survivors (26.00)** is also higher than that of **non-survivors (10.50)**.
* Both the mean and median indicate that survivors generally paid higher fares.
* The difference between the survivor and non-survivor groups is noticeable in both statistics.
* The mean is larger than the median in both groups, suggesting that both fare distributions are right-skewed.

These are observations only—we are not explaining the reasons yet.

---

# Q3. Histogram Observations

From the histogram, I observe:

### Observation 1

Most passengers in both groups paid relatively low fares.

---

### Observation 2

Both survivor and non-survivor fare distributions are right-skewed, with a long tail extending toward higher fares.

---

### Observation 3

There is considerable overlap between the two distributions, especially in the lower fare ranges.

---

### Observation 4

Survivors appear more frequently in the higher fare ranges than non-survivors.

---

### Observation 5

Only a small number of passengers paid extremely high fares, indicating that such tickets were relatively rare.

Again, these are observations from the graph without interpreting the causes.

---

# Q4. Does the data support your earlier hypotheses?

### Hypothesis 1

> **Passengers who paid higher fares may have had higher survival rates.**

**Supported.**

Both the mean and median fares are substantially higher for survivors than for non-survivors.

---

### Hypothesis 2

> **Passengers who paid lower fares may have had lower survival rates.**

**Partially supported.**

Non-survivors have both a lower average fare and a lower median fare.

However, additional analysis is needed to determine whether fare itself is responsible or whether it is related to other features such as passenger class.

---

### Hypothesis 3

> **Fare alone may not explain survival.**

**Supported.**

Although there is a clear difference in fares, the histogram shows substantial overlap between survivors and non-survivors.

This suggests that fare is useful but is unlikely to explain survival by itself.

---

# Q5. Relationship Investigation Report – Fare ↔ Survived

### Relationship Observed

There is a clear relationship between **Fare** and **Survival**.

Passengers who survived generally paid higher fares than those who did not survive.

This pattern is visible in both the mean and median fare values.

---

### Does Fare appear useful for prediction?

Yes.

Fare appears to be an informative feature because both the average and median fares differ considerably between survivors and non-survivors.

However, it is likely to be most effective when combined with other features such as **Pclass**, **Sex**, and **Age**.

---

### Why should both the mean and median be considered?

The Fare distribution is **right-skewed**, meaning a small number of very expensive tickets increase the average.

The mean captures the overall average but is sensitive to extreme values.

The median represents the middle passenger and is much less affected by unusually expensive fares.

Looking at both statistics provides a more complete understanding of the distribution.

---

### New Questions Raised

This analysis raises several interesting questions:

* Is the relationship between fare and survival mainly due to passenger class?
* Did males and females paying similar fares have similar survival rates?
* Do high fares correspond to specific cabin decks?
* Does combining **Fare** with **Pclass** improve prediction accuracy?
* Would transforming the highly skewed Fare feature improve machine learning performance?

These questions can be explored in later stages of EDA.

---

# 🌟 Mentor Feedback

You've now analyzed four important relationships with the target variable:

| Feature    | Relationship with Survival |
| ---------- | -------------------------- |
| **Sex**    | Very Strong                |
| **Pclass** | Strong                     |
| **Fare**   | Strong                     |
| **Age**    | Moderate                   |

Notice something interesting:

* **Pclass** and **Fare** both seem strongly related to survival.
* This raises a new question:

> **Are Fare and Pclass related to each other?**

Think about it:

* First Class passengers usually paid **higher fares**.
* Third Class passengers usually paid **lower fares**.

So perhaps:

```text
Higher Fare
      ↓
Often means
      ↓
Higher Passenger Class
      ↓
Higher Survival
```

This is why experienced AI engineers don't stop after analyzing one feature at a time. They start asking how **features interact with one another**.

That curiosity leads naturally into the next stage of EDA, where you'll study relationships **between features themselves**, not just between a feature and the target. This is where deeper insights and better feature engineering opportunities begin to emerge.
