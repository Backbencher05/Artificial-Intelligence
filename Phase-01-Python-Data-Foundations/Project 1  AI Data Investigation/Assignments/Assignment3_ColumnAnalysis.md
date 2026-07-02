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


---------------------------------------------------------------------------------------------------

# Fare

# Day 010 Mini Assignment – Fare Feature Analysis

---

# Q1. Explain each value from `df["Fare"].describe()` in your own words.

Your output:

| Statistic |  Value |
| --------- | -----: |
| Count     |    891 |
| Mean      |  32.20 |
| Std       |  49.69 |
| Min       |   0.00 |
| 25%       |   7.91 |
| 50%       |  14.45 |
| 75%       |  31.00 |
| Max       | 512.33 |

Let's understand each one.

---

## 1. Count = 891

This tells us that **all 891 passengers have a recorded fare**.

Unlike the `Age` column, there are **no missing values** in the Fare column.

---

## 2. Mean = 32.20

The mean is the **average ticket fare**.

Imagine adding the fare paid by every passenger and dividing by 891.

```text
Total Fare Paid
----------------
891 Passengers
```

The average comes out to approximately:

```text
32.20
```

However, as we'll see in Q2, this average is influenced by a few passengers who paid very high fares.

---

## 3. Min = 0.00

The lowest recorded fare is **0**.

This means at least one passenger did not pay any fare.

Possible reasons could include:

* Complimentary travel
* Employee or crew-related ticket
* Recording issue

At this stage, we simply observe the value—we don't conclude whether it is correct or incorrect.

---

## 4. 25% = 7.91

If we arrange all fares from lowest to highest:

The first **25%** of passengers paid **₹7.91 or less** (technically, fare units used in the dataset).

This shows that many passengers paid relatively low fares.

---

## 5. 50% = 14.45 (Median)

The median represents the **middle fare**.

If every passenger is arranged from the cheapest ticket to the most expensive:

The passenger exactly in the middle paid approximately:

```text
14.45
```

This means:

* Half the passengers paid **less than 14.45**.
* Half paid **more than 14.45**.

Unlike the mean, the median is **not heavily affected by extremely expensive tickets**.

---

## 6. 75% = 31.00

About **75% of passengers paid ₹31 or less**.

Only the remaining **25%** paid more than ₹31.

This suggests that very expensive tickets were relatively uncommon.

---

## 7. Max = 512.33

The most expensive ticket cost:

```text
512.33
```

This is dramatically higher than both the median (14.45) and the average (32.20).

It indicates that a small number of passengers paid exceptionally high fares.

---

## 8. Std = 49.69

The standard deviation measures **how spread out the fares are**.

A value of **49.69** is quite large compared to the mean (32.20), suggesting that ticket prices varied widely—from free tickets to very expensive ones.

---

# Q2. Compare the Mean (≈32.2) and Median (≈14.45).

## Why is the mean much larger than the median?

The mean is much larger because a **small number of passengers paid extremely expensive fares**.

Most passengers paid relatively low fares, but a few passengers paid hundreds of fare units.

These high values **pull the average upward**.

The median, however, depends only on the middle value and is therefore much less affected by these expensive tickets.

---

## What does this suggest about the Fare distribution?

It suggests that the Fare distribution is **positively skewed (right-skewed)**.

In other words:

* Most passengers paid lower fares.
* A few passengers paid very high fares.
* Those high fares stretch the distribution toward the right.

A common sign of a right-skewed distribution is:

```text
Mean > Median
```

Which is exactly what we observe:

```text
Mean = 32.20

Median = 14.45
```

---

# Q3. What does the Fare histogram tell you?

From the histogram, I observe the following:

### 1. Most passengers paid relatively low fares.

The majority of passengers are concentrated in the lower fare ranges.

---

### 2. The distribution is not symmetric.

Instead of looking like a bell-shaped curve, the histogram has a long tail extending toward higher fares.

This indicates a **right-skewed distribution**.

---

### 3. There are a few unusually expensive tickets.

Only a small number of passengers paid very high fares (approaching the maximum of 512.33).

These observations suggest the presence of **high-value observations**, which influence the mean.

At this stage, however, I would not automatically label them as outliers. They may represent genuine first-class passengers.

---

# Q4. List three hypotheses about how Fare might relate to survival.

Since we have not yet analyzed the `Survived` column, these are only hypotheses.

### Hypothesis 1

Passengers who paid higher fares may have had higher survival rates because they may have traveled in better locations on the ship.

---

### Hypothesis 2

Passengers paying very low fares may have belonged mainly to lower passenger classes and may have experienced lower survival rates.

---

### Hypothesis 3

Fare alone may not determine survival. Its relationship with survival may depend on other features such as **Pclass**, **Sex**, and **Age**.

These hypotheses should be tested using the survival data before drawing conclusions.

---

# Q5. Feature Investigation Report – Fare Column

* **Feature Type:** Numerical (Continuous), because fare represents a measurable monetary value and can contain decimal values.
* **Missing Values:** No missing values are present, making this a complete and reliable feature.
* **Distribution:** The distribution is **positively (right) skewed**, with most passengers paying relatively low fares and a small number paying very high fares.
* **Basic Statistics:** The average fare is **32.20**, the median fare is **14.45**, the minimum fare is **0**, and the maximum fare is **512.33**. The standard deviation (**49.69**) indicates considerable variation in ticket prices.
* **Possible Importance for Machine Learning:** Fare may be an important predictive feature because it could reflect passenger wealth, ticket class, or cabin location, all of which might influence survival. Its predictive value should be evaluated together with other features rather than in isolation.

---

# 🌟 Mentor Feedback

This feature introduces one of the most important concepts in Exploratory Data Analysis:

> **The mean doesn't always tell the full story.**

Imagine these five fares:

```text
7
8
9
10
500
```

The average is:

```text
106.8
```

Does **106.8** represent what most passengers paid?

**Not at all.**

Four out of five passengers paid **10 or less**.

That's why AI engineers always look at:

* **Mean**
* **Median**
* **Histogram**

**together**, not individually.

A good habit to develop is:

```text
If Mean ≈ Median
        ↓
Distribution is often fairly symmetric.

If Mean >> Median
        ↓
Suspect a right-skewed distribution.

If Mean << Median
        ↓
Suspect a left-skewed distribution.
```

This habit will become extremely valuable when you begin **feature engineering**, because skewed numerical features often require special preprocessing before training machine learning models.


-----------------------------------------------------------------------------------------

# Embarked Feature Analysis

# Day 010 Mini Assignment – Embarked Feature Analysis

---

# Q1. How many passengers boarded from each port? What percentage does each port represent?

From the Titanic dataset:

| Port  | Full Name   |   Count | Percentage |
| ----- | ----------- | ------: | ---------: |
| **S** | Southampton | **644** | **72.44%** |
| **C** | Cherbourg   | **168** | **18.90%** |
| **Q** | Queenstown  |  **77** |  **8.66%** |

> **Note:** These percentages are calculated from the **889 non-missing values** (because 2 `Embarked` values are missing), which is exactly what `value_counts(normalize=True)` does by default.

### Observation

* Most passengers (**72.44%**) boarded at **Southampton**.
* Nearly one-fifth (**18.90%**) boarded at **Cherbourg**.
* Only **8.66%** boarded at **Queenstown**.

---

# Q2. Why is Embarked considered a nominal categorical feature?

The `Embarked` feature is **categorical** because it represents **categories (boarding ports)** rather than numerical measurements.

The possible values are:

```text id="6l5u5z"
S → Southampton

C → Cherbourg

Q → Queenstown
```

It is specifically **nominal** because these categories **do not have any natural order or ranking**.

For example:

* Southampton is not "greater than" Cherbourg.
* Queenstown is not "less than" Southampton.

These are simply names of locations.

Unlike `Pclass`, where **1st Class > 2nd Class > 3rd Class**, the `Embarked` values cannot be meaningfully ordered.

Therefore, `Embarked` is a **nominal categorical feature**.

---

# Q3. Only 2 values are missing. How is this different from the Cabin column? Why might we handle these two columns differently?

The difference lies in **how much information is missing**.

| Column   | Missing Values | Approximate Percentage |
| -------- | -------------: | ---------------------: |
| Cabin    |            687 |                   ~77% |
| Embarked |              2 |                  ~0.2% |

The **Cabin** column has a very large amount of missing data. Removing every row with a missing cabin would discard most of the dataset, so we need to carefully evaluate options such as feature engineering, creating a "Cabin Available" indicator, or dropping the column if it adds little value.

The **Embarked** column has only two missing values. Because the missing percentage is extremely small, simple solutions are reasonable, such as:

* Filling the missing values with the mode (most common port), or
* Removing those two rows if appropriate.

The key lesson is that **the percentage of missing data influences the cleaning strategy**. A solution suitable for 0.2% missing data is not necessarily appropriate for 77% missing data.

---

# Q4. What is the mode? Why is the mode commonly used to fill missing values in categorical features?

The **mode** is the value that appears **most frequently** in a dataset.

Example:

```text id="lhyqct"
IT
HR
IT
Sales
IT
```

The mode is:

```text id="h6v9l5"
IT
```

because it occurs most often.

For the Titanic dataset, the `Embarked` column has:

```text id="h5qbse"
S → 644

C → 168

Q → 77
```

So the mode is:

```text id="rbtol7"
S (Southampton)
```

### Why is the mode used for categorical features?

Categorical features cannot be averaged.

For example, calculating the mean of:

```text id="3w7qpm"
Southampton

Cherbourg

Queenstown
```

does not make sense.

Instead, we fill missing values with the **most common category**, because it is the most likely value based on the existing data and preserves the categorical nature of the feature.

---

# Q5. Feature Investigation Report – Embarked Column

* **Feature Type:** Categorical (Nominal), representing the port where each passenger boarded the Titanic.
* **Missing Values:** The column contains only **2 missing values** (approximately **0.2%** of the dataset), indicating excellent data quality.
* **Distribution:** Most passengers boarded at **Southampton (644, 72.44%)**, followed by **Cherbourg (168, 18.90%)** and **Queenstown (77, 8.66%)**.
* **Most Common Category:** The mode is **Southampton (`S`)**, making it the most appropriate candidate if simple imputation is required.
* **Possible Importance for Machine Learning:** The boarding port may capture differences in passenger demographics, ticket class, fare, or travel patterns. Although it may not directly determine survival, it could contribute useful information when combined with other features such as **Pclass**, **Fare**, and **Sex**.

---

# 🌟 Mentor Feedback

This assignment introduces an important principle in data cleaning:

> **Choose the imputation method based on the feature type.**

A simple guideline is:

| Feature Type    | Common Imputation |
| --------------- | ----------------- |
| **Numerical**   | Mean or Median    |
| **Categorical** | Mode              |

Why?

* **Numerical features** represent quantities, so statistics like the mean or median are meaningful.
* **Categorical features** represent labels, so the most frequent category (mode) is usually the most sensible replacement.

As you progress into machine learning, you'll learn more advanced imputation techniques. However, before applying any method, always ask:

1. **What type of feature is this?**
2. **How much data is missing?**
3. **Why might the data be missing?**

Those three questions lead to better preprocessing decisions than simply filling every missing value the same way.

-----------------------------------------------------
# Name Feature Analysis 
-----------------------------------------------------

# Day 010 Mini Assignment – Name Feature Analysis

---

# Q1. What is the Name column? Why is it considered a text feature?

The **Name** column contains the **full name of each passenger**.

Example values:

```text
Braund, Mr. Owen Harris
Cumings, Mrs. John Bradley
Heikkinen, Miss. Laina
Allen, Master. William Henry
```

It is considered a **text feature** because each value is a string of characters rather than a numerical measurement or a predefined category.

Unlike columns such as:

* `Age` → numerical
* `Fare` → numerical
* `Pclass` → categorical

the `Name` column contains free-form text.

---

### Why is it a text feature?

Because names are made up of words and characters.

For example:

```text
Braund
Mr.
Owen
Harris
```

These are pieces of text.

A machine learning model cannot directly perform mathematical operations on names.

---

# Q2. From the first 20–30 names you inspect, list all the different titles you notice.

From the first few rows of the Titanic dataset, the common titles include:

```text
Mr.
Mrs.
Miss.
Master.
```

As you inspect more names, you may also encounter:

```text
Dr.
Rev.
Col.
Major.
Capt.
Sir.
Lady.
Don.
Mme.
Mlle.
Ms.
Jonkheer.
Countess.
```

The exact list depends on how many rows you inspect, but the first four (`Mr.`, `Mrs.`, `Miss.`, `Master.`) are the most common.

---

# Q3. Why might the raw Name column be difficult for a machine learning model to use directly?

The raw `Name` column is difficult for a machine learning model because every passenger's full name is almost unique.

For example:

```text
Braund, Mr. Owen Harris

Cumings, Mrs. John Bradley

Heikkinen, Miss. Laina
```

A machine learning model works with patterns that repeat across many records.

If every value is unique, the model cannot easily learn meaningful relationships.

Another challenge is that names are stored as text, while most machine learning algorithms require numerical input.

However, although the full names are not directly useful, they contain hidden information such as:

* Title (`Mr.`, `Mrs.`, `Miss.`)
* Family name
* Gender clues
* Social status

These hidden patterns can be extracted and converted into useful features.

---

# Q4. Explain Feature Engineering in your own words.

### What is Feature Engineering?

Feature Engineering is the process of **creating better features from the existing data so that a machine learning model can learn more useful patterns**.

Instead of using the raw data exactly as it appears, we transform or extract information that better represents the problem.

In simple words:

> **Feature Engineering means improving the data before giving it to the machine learning model.**

---

### Why is extracting the Title from Name an example of Feature Engineering?

The raw `Name` column contains a lot of information mixed together.

Example:

```text
Braund, Mr. Owen Harris
```

Instead of giving the entire name to the model, we can extract only:

```text
Mr.
```

Now the model receives a much simpler and more meaningful feature.

Similarly:

```text
Mrs.

Miss.

Master.

Dr.
```

These titles may indicate:

* Gender
* Age group
* Marital status
* Social status

All of these could potentially influence survival.

So we transformed one complex text column into a simpler categorical feature.

That transformation is **feature engineering**.

---

# Q5. Feature Investigation Report – Name Column

* **Feature Type:** Text feature containing the full names of passengers.
* **Missing Values:** No missing values are present, indicating complete data quality.
* **Why Raw Names Are Difficult for ML:** Most names are unique and stored as text, making them unsuitable for direct use by most machine learning algorithms. They also cannot be used directly in mathematical computations.
* **Hidden Information Inside the Names:** The names contain valuable information such as titles (`Mr.`, `Mrs.`, `Miss.`, `Master.`), family names, and possible indicators of gender or social status.
* **Possible Engineered Features:** Useful features that could be extracted include the passenger's title, surname, family size (combined with other columns), name length, and whether a passenger belongs to a shared family group.

---

# 🌟 Mentor Feedback

This assignment marks an important shift in your AI journey.

Until now, you've been **analyzing existing features**.

Now you're learning how to **create new features**.

Think about this transformation:

```text
Raw Feature
        ↓
Name
        ↓
Feature Engineering
        ↓
Title
        ↓
Machine Learning Model
```

Notice that the model doesn't become smarter by itself—you make the **input data smarter**.

As a backend engineer, you can think of feature engineering like building a better API response:

* The database may store raw, detailed information.
* Before sending it to the frontend, you transform it into a cleaner, more useful format.

Feature engineering follows the same idea: **transform raw data into features that are easier and more meaningful for a machine learning model to learn from**. This is one of the highest-impact skills in practical AI because better features often improve model performance more than simply choosing a more complex algorithm.


