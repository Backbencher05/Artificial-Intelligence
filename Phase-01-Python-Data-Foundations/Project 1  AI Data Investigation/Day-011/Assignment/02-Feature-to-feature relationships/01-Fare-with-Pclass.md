# Day 011 Mini Assignment – Relationship Analysis: Fare ↔ Pclass

This is your **first feature-to-feature relationship analysis**.

Until now, you compared features with the **target (`Survived`)**.

Now you're asking:

> **"Are two input features related to each other?"**

This is an important part of EDA because related features can influence how we build machine learning models.

---

# Q1. Explain the output of:

```python
df.groupby("Pclass")["Fare"].mean()
```

and

```python
df.groupby("Pclass")["Fare"].median()
```

### What do the groups represent?

`groupby("Pclass")` divides the passengers into **three groups** based on their travel class:

```text
Pclass = 1 → First Class
Pclass = 2 → Second Class
Pclass = 3 → Third Class
```

Then, for each class, Pandas calculates statistics for the **Fare** column.

---

### What does the mean tell you?

The mean tells us the **average fare paid** by passengers in each class.

Your output:

| Passenger Class | Mean Fare |
| --------------- | --------: |
| First Class     |     84.15 |
| Second Class    |     20.66 |
| Third Class     |     13.68 |

This represents the average ticket price for passengers traveling in each class.

---

### What does the median tell you?

The median tells us the **middle fare** paid within each passenger class.

Your output:

| Passenger Class | Median Fare |
| --------------- | ----------: |
| First Class     |       60.29 |
| Second Class    |       14.25 |
| Third Class     |        8.05 |

The median represents the fare of the middle passenger after sorting fares within each class.

Unlike the mean, it is less affected by extremely expensive tickets.

---

# Q2. Compare the average and median fares of each passenger class.

### Observations

* **First Class** has the highest average fare (**84.15**).
* **Second Class** has a much lower average fare (**20.66**) than First Class.
* **Third Class** has the lowest average fare (**13.68**).
* The median fares also decrease from **First Class (60.29)** to **Second Class (14.25)** to **Third Class (8.05)**.
* In every passenger class, the **mean is higher than the median**, suggesting that fare distributions within each class are right-skewed.

These are observations only.

---

# Q3. Study the box plot carefully.

### Observation 1

The median fare is highest for **First Class**, lower for **Second Class**, and lowest for **Third Class**.

---

### Observation 2

The spread of fares is much larger in **First Class** than in the other two classes.

---

### Observation 3

Second Class fares are more concentrated, showing less variation than First Class.

---

### Observation 4

Third Class has the lowest fare range, with most passengers paying relatively low fares.

---

### Observation 5

The box plot shows several **outliers**, especially in First Class, indicating that some passengers paid exceptionally high fares compared to others in the same class.

---

### Observation 6

Although there is some overlap between the fare ranges of different classes, the typical fare (median) clearly decreases from First to Third Class.

---

# Q4. Based on today's investigation, does Fare appear to be related to Pclass?

Yes.

The data suggests a **strong association** between **Fare** and **Pclass**.

Evidence from the statistics:

| Pclass | Mean Fare | Median Fare |
| -----: | --------: | ----------: |
|      1 |     84.15 |       60.29 |
|      2 |     20.66 |       14.25 |
|      3 |     13.68 |        8.05 |

Both the mean and median decrease consistently from **First Class** to **Third Class**.

The box plot also supports this observation:

* First Class has the highest fare distribution.
* Second Class lies in the middle.
* Third Class has the lowest fare distribution.

This indicates a clear **association** between passenger class and fare.

However, this does **not** mean that one feature causes the other. It simply shows that they vary together in the dataset.

---

# Q5. Relationship Investigation Report – Fare ↔ Pclass

### Relationship Observed

There is a strong relationship between **Fare** and **Passenger Class**.

Passengers traveling in higher classes generally paid higher fares, while passengers in lower classes generally paid lower fares.

This trend is consistently visible in both the summary statistics and the box plot.

---

### Do both features seem to carry related information?

Yes.

Both features appear to describe aspects of a passenger's travel status.

Since higher passenger classes generally correspond to higher fares, the two features contain related information.

However, they are **not identical** because fares still vary within each passenger class.

---

### Does Fare still appear useful?

Yes.

Although Fare is associated with Passenger Class, it still contains additional information.

For example:

* Two First Class passengers may pay different fares.
* Two Third Class passengers may also pay different fares.

This variation suggests that Fare may still contribute useful predictive information beyond Passenger Class alone.

---

### New Questions Raised

This analysis raises several interesting questions:

* If Fare and Pclass are strongly related, should both features be included in the machine learning model?
* Does Fare provide additional predictive value after accounting for Passenger Class?
* Why do some passengers within the same class pay much higher fares than others?
* Are the very high fare values associated with larger cabins or family bookings?
* Would combining Fare with Cabin or Embarked reveal additional patterns?

These questions can be explored in later stages of feature engineering and model building.

---

# 🌟 Mentor Feedback

Today's lesson introduces a key concept in machine learning:

## Features can be related to each other.

So far, you've explored:

```text
Feature
      ↓
Target
```

Now you've explored:

```text
Feature A
      ↓
Feature B
```

This is important because highly related features may contain **overlapping information**.

For example:

```text
First Class
        ↓
Usually
Higher Fare
```

That doesn't mean the features are duplicates—it means they are **associated**.

---

## 🧠 A Machine Learning Insight

Think about these two passengers:

| Passenger | Pclass | Fare |
| --------- | :----: | ---: |
| A         |    1   |   60 |
| B         |    1   |  120 |

Both traveled in **First Class**, but they paid very different fares.

This tells us:

* **Pclass** gives a broad category.
* **Fare** provides finer detail within that category.

That's why both features can still be valuable. A machine learning model can often learn more from **multiple related features** than from either feature alone, provided each contributes some unique information.
