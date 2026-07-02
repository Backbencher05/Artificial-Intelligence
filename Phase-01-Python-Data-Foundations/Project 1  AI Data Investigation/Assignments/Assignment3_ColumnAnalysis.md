# 1: Sex
These answers focus on **reasoning**, which is exactly what your mentor is trying to develop.

---

# Day 010 Mini Assignment – Sex Feature Analysis

## Q1. How many male and female passengers are in the dataset? What percentage does each represent?

From the Titanic dataset:

| Sex    |   Count | Percentage |
| ------ | ------: | ---------: |
| Male   | **577** | **64.76%** |
| Female | **314** | **35.24%** |

Total passengers:

```text id="pryn4o"
577 + 314 = 891
```

This matches the total number of records in the dataset.

---

# Q2. Is the Sex feature balanced? Why or why not?

No, the **Sex** feature is **not balanced**.

A balanced feature would have categories that are represented in roughly equal proportions.

Here:

* Male → **64.76%**
* Female → **35.24%**

The difference is approximately **30 percentage points**, which means there are significantly more male passengers than female passengers.

Although both categories are well represented, the distribution is not equal.

---

# Q3. Without looking at the `Survived` column yet, write three hypotheses about how the Sex feature might relate to survival.

Since we have **not analyzed the `Survived` column yet**, these are only hypotheses based on historical context—not conclusions.

### Hypothesis 1

Female passengers may have had a higher survival rate than male passengers.

---

### Hypothesis 2

If the "women and children first" evacuation policy was followed, sex may be an important predictor of survival.

---

### Hypothesis 3

Sex alone may not determine survival. Other factors such as passenger class, age, cabin location, or ticket fare might also influence survival, possibly interacting with sex.

These are assumptions that will need to be tested using the data.

---

# Q4. Why is it important to separate observation from conclusion during EDA?

EDA is meant to **explore the data objectively**, not to prove assumptions.

An **observation** is something directly supported by the data.

Example:

> **Observation:** 64.76% of passengers are male.

A **conclusion** is an interpretation that requires evidence.

Example:

> **Conclusion:** Male passengers had lower survival rates.

This conclusion cannot be made until we analyze the relationship between **Sex** and **Survived**.

If we confuse observations with conclusions, we risk introducing bias and making incorrect decisions.

Separating them helps ensure that our analysis remains objective and evidence-based.

---

# Q5. Feature Investigation Report – Sex Column

* The **Sex** feature contains **891 values** with **no missing data**, making it a high-quality feature.
* There are **577 male passengers (64.76%)** and **314 female passengers (35.24%)**.
* The feature is **categorical (nominal)** because it consists of categories without any natural order.
* The distribution is **not balanced**, with male passengers representing nearly two-thirds of the dataset.
* Based on historical context, the feature may be related to survival, but this relationship must be verified using the `Survived` column.
* Before training a machine learning model, the `Sex` column will need to be converted into a numerical representation (e.g., label encoding or one-hot encoding).

---

# 🌟 Mentor Feedback

This assignment is subtly teaching one of the most important habits in Data Science:

```text id="tgt4gt"
Observation
      ↓
Hypothesis
      ↓
Verification
      ↓
Conclusion
```

Notice what you **didn't** do:

❌ "Females survived more."

Instead, you wrote:

✅ "Females **may have** had a higher survival rate."

That's the correct scientific mindset. Good AI engineers don't let intuition become fact—they use intuition to generate hypotheses and then use data to test them. This disciplined approach leads to more reliable analyses and better machine learning models.


--------------------------------------------------------------------
# 2: Age

# Day 010 Mini Assignment – Age Feature Analysis

---

# Q1. From `describe()`, explain what each value means.

Your output:

| Statistic |  Value |
| --------- | -----: |
| Count     |    714 |
| Mean      |  29.70 |
| Std       |  14.53 |
| Min       |   0.42 |
| 25%       | 20.125 |
| 50%       |     28 |
| 75%       |     38 |
| Max       |     80 |

Let's explain each one as if we're teaching someone.

---

## 1. Count = 714

**What does it mean?**

Count tells us **how many non-missing values** are present in the column.

The Titanic dataset has:

```text
891 passengers
```

But only:

```text
714 ages
```

are available.

This means:

```text
891 - 714 = 177
```

age values are missing.

Think of it as:

> "Out of all passengers, we only know the age of 714 people."

---

## 2. Mean = 29.70

The mean is the **average age** of all passengers whose age is known.

Imagine adding all 714 ages together and dividing by 714.

```text
Total Age
---------
714
```

Result:

```text
29.7 years
```

So the average passenger was approximately **30 years old**.

---

## 3. Min = 0.42

This is the **youngest passenger** in the dataset.

```text
0.42 years
```

is approximately:

```text
5 months old
```

This tells us that even infants were aboard the Titanic.

---

## 4. Max = 80

This is the **oldest passenger**.

The oldest known passenger was:

```text
80 years old
```

---

## 5. 25% = 20.125

This is called the **first quartile (Q1)**.

Imagine arranging all 714 ages from youngest to oldest.

The value at the **25% position** is:

```text
20.125 years
```

Meaning:

> About **25% of passengers were younger than 20.125 years**.

---

## 6. 50% = 28

This is the **median**.

If we sort every passenger by age:

```text
Youngest
      ↓
Middle
      ↓
Oldest
```

The middle passenger is:

```text
28 years old
```

This means:

* 50% are younger than 28.
* 50% are older than 28.

---

## 7. 75% = 38

This is the **third quartile (Q3).**

After sorting:

75% of passengers are:

```text
38 years or younger
```

Only:

```text
25%
```

are older than 38.

---

## 8. Std = 14.53

Std means **Standard Deviation**.

Don't memorize the mathematical formula yet.

Think of it like this:

It tells us **how spread out the ages are from the average**.

If everyone were around:

```text
29
30
31
30
29
```

the standard deviation would be very small.

But because Titanic passengers ranged from:

```text
0.42
...
80
```

there is much more variation.

A standard deviation of **14.53** tells us that passenger ages are spread over a fairly wide range.

---

# Q2. What does the histogram tell you about the age distribution?

The histogram suggests that:

* Most passengers were **young adults**.
* The highest concentration of passengers appears to be between **20 and 40 years of age**.
* There are relatively few infants and elderly passengers.
* The number of passengers gradually decreases as age increases beyond 40.

The distribution is **not perfectly symmetrical**, with fewer passengers at the extreme young and old ages.

---

# Q3. Why is Min = 0.42 not necessarily an outlier?

An outlier is not simply a very small or very large value.

It is a value that is **unusual or inconsistent with the context**.

Although **0.42 years** (about 5 months) is much younger than most passengers, it is completely possible for an infant to travel on a ship.

Therefore:

* It is **rare**, but
* It is **realistic**.

Since it represents a valid observation, it should not automatically be considered an outlier.

---

## Why is Max = 80 not automatically an outlier?

Similarly:

An **80-year-old** passenger is uncommon but entirely possible.

People can and do live to 80 years or older.

Therefore:

* It is an extreme value,
* But it is still realistic.

It should not be removed simply because it is the largest value.

This reinforces an important lesson:

> **Extreme values are not always outliers. Context matters.**

---

# Q4. List three hypotheses about how Age might influence survival.

Since we have not analyzed the `Survived` column yet, these are only hypotheses.

### Hypothesis 1

Young children may have had a higher survival rate because they might have been prioritized during evacuation.

---

### Hypothesis 2

Very elderly passengers may have had a lower survival rate because evacuation could have been more physically challenging.

---

### Hypothesis 3

Age alone may not determine survival. Its effect may depend on other features such as passenger class, sex, or cabin location.

These hypotheses need to be tested using the survival data.

---

# Q5. Feature Investigation Report – Age Column

* **Feature Type:** Numerical (Continuous).
* **Missing Values:** 177 missing values out of 891 passengers (approximately 20%), so missing data will need to be handled before model training.
* **Distribution:** Most passengers appear to be between 20 and 40 years old, with relatively fewer infants and elderly passengers.
* **Basic Statistics:** Average age is **29.7 years**, median is **28 years**, youngest passenger is **0.42 years**, and oldest passenger is **80 years**.
* **Variability:** The standard deviation of **14.53 years** indicates a fairly wide spread of ages across passengers.
* **Possible Importance for Machine Learning:** Age is likely to be an informative feature because survival may vary across different age groups. However, its relationship with survival should be verified through further analysis rather than assumed.

---

# 🌟 Mentor Feedback

Today's lesson introduces another important distinction:

* **Descriptive statistics** tell you **what the data looks like**.
* **EDA** asks **what patterns might exist**.
* **Machine Learning** later determines **whether those patterns actually help make predictions**.

A good AI engineer follows this sequence:

```text
Collect Statistics
        ↓
Observe Patterns
        ↓
Form Hypotheses
        ↓
Test with Data
        ↓
Draw Conclusions
```

Notice how you resisted saying *"children survived more"* or *"older people survived less."* Instead, you framed them as **hypotheses**. That disciplined, evidence-first approach is exactly what separates good data analysis from guesswork.



------------------------------------------------------------------------------------
# 3: Pclass

# Day 010 Mini Assignment – Pclass Feature Analysis

---

# Q1. How many passengers traveled in each class? What percentage of the dataset does each class represent?

From your analysis:

| Passenger Class |   Count | Percentage |
| --------------- | ------: | ---------: |
| **3rd Class**   | **491** | **55.11%** |
| **1st Class**   | **216** | **24.24%** |
| **2nd Class**   | **184** | **20.65%** |

Total passengers:

```text id="5c0n4l"
491 + 216 + 184 = 891
```

### Observation

* More than **half of all passengers (55.11%)** traveled in **3rd Class**.
* About **one-quarter (24.24%)** traveled in **1st Class**.
* The remaining **20.65%** traveled in **2nd Class**.

This indicates that the dataset is dominated by passengers from **3rd Class**.

---

# Q2. Why is Pclass considered an ordinal categorical feature instead of a continuous numerical feature?

Although `Pclass` is stored as numbers (`1`, `2`, `3`), those numbers **represent categories**, not quantities.

The numbers indicate different passenger classes:

```text id="jlwm3m"
1 → First Class

2 → Second Class

3 → Third Class
```

The important point is that these categories have a **natural order**:

```text id="kzd1zg"
First Class
     ↓
Second Class
     ↓
Third Class
```

However, the numbers **do not represent measurable distances**.

For example:

* The difference between **1 and 2** is **not "one unit"** in a mathematical sense.
* We cannot say that **3rd Class is three times 1st Class**.
* Calculating an average passenger class (e.g., **2.3**) has no real-world meaning.

Therefore, `Pclass` is:

* **Categorical**, because it represents groups.
* **Ordinal**, because those groups have a meaningful ranking.

It is **not continuous** because it is not measuring a quantity like age, height, or fare.

---

# Q3. Suppose the CSV stored:

```text id="lk2k40"
First Class

Second Class

Third Class
```

instead of:

```text id="ikb37f"
1

2

3
```

Would the meaning of the feature change?

No.

The **meaning of the feature would remain exactly the same**.

Only the representation changes.

Instead of storing:

```text id="3pjayp"
1

2

3
```

the dataset would store:

```text id="kgg6w8"
First Class

Second Class

Third Class
```

Both represent the same information:

```text id="aq85oq"
Passenger's travel class
```

The only difference is:

* Numbers are easier for computers to process.
* Text labels are easier for humans to read.

From a machine learning perspective, we would still recognize this as an **ordinal categorical feature**, and we would encode it appropriately before training a model.

---

# Q4. List three hypotheses about how Pclass might relate to survival.

Since we have **not analyzed the `Survived` column yet**, these are only hypotheses.

### Hypothesis 1

Passengers traveling in **1st Class** may have had a higher survival rate because they may have had better access to lifeboats and crew assistance.

---

### Hypothesis 2

Passengers in **3rd Class** may have had a lower survival rate because they may have been located farther from the upper decks and evacuation routes.

---

### Hypothesis 3

Passenger class alone may not determine survival. Its effect may interact with other features such as **Sex**, **Age**, and **Fare**.

These hypotheses need to be verified using the survival data.

---

# Q5. Feature Investigation Report – Pclass Column

* **Feature Type:** Categorical (Ordinal), because it represents ranked passenger classes (1st, 2nd, and 3rd).
* **Missing Values:** No missing values are present, making this a complete and reliable feature.
* **Distribution:** 3rd Class contains **491 passengers (55.11%)**, 1st Class contains **216 passengers (24.24%)**, and 2nd Class contains **184 passengers (20.65%)**.
* **Data Quality:** The feature is clean, complete, and does not require missing value handling.
* **Possible Importance for Machine Learning:** Passenger class may be an important predictor of survival because it could be associated with socioeconomic status, cabin location, and access to evacuation resources. This relationship should be verified during further analysis.

---

# 🌟 Mentor Feedback

This assignment teaches an important lesson that many beginners miss:

> **Just because a feature is stored as a number doesn't mean it's a numerical feature.**

For example:

```text id="wqmfx0"
Pclass

1
2
3
```

looks numeric, but it actually represents **ranked categories**.

Compare it with Age:

```text id="xyjvaz"
Age

18
25
42
67
```

Age measures a real quantity—you can meaningfully calculate averages and differences.

Pclass simply labels ordered categories—you can rank them, but arithmetic on the labels doesn't have the same meaning.

A useful rule to remember is:

```text id="93udku"
Numbers can represent:

• Quantities → Numerical Features

• Labels → Categorical Features
```

As an AI engineer, one of your first tasks with every dataset is to determine **whether a number is measuring something or merely labeling something**. That decision affects preprocessing, feature engineering, and sometimes even which machine learning algorithm performs best.
