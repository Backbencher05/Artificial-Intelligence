Absolutely. And Aditya... this session marks another important shift.

Until now we've asked:

```text
Feature
     ↓
Target
```

Now we're going to ask:

```text
Feature
     ↓
Feature
```

This is exactly how real data scientists investigate data.

Sometimes the biggest insight doesn't come from looking at the target—it comes from understanding how the features relate to each other.

---

# 🚢 Day 011 – Relationship Analysis (Part 5)

# Fare ↔ Pclass

---

# 🌟 Memory Refresh

Before we investigate, let's reconnect with everything we already know.

## 📌 Fare

| Property                | What We Learned                                                      |
| ----------------------- | -------------------------------------------------------------------- |
| Type                    | Numerical (Continuous)                                               |
| Missing Values          | None                                                                 |
| Mean                    | 32.20                                                                |
| Median                  | 14.45                                                                |
| Distribution            | Right-skewed                                                         |
| Interesting Observation | Survivors generally paid higher fares than non-survivors.            |
| Question Raised         | Is this because they paid more, or because they were in First Class? |

---

## 📌 Pclass

| Property                   | What We Learned                   |
| -------------------------- | --------------------------------- |
| Type                       | Categorical (Ordinal)             |
| Categories                 | 1st, 2nd, 3rd                     |
| Missing Values             | None                              |
| Distribution               | 1st: 216, 2nd: 184, 3rd: 491      |
| Relationship with Survival | Strong                            |
| Question Raised            | Why did First Class survive more? |

---

## 🧠 The Question We Want to Answer

Remember what we observed:

```text
Higher Fare
        ↓
Higher Survival
```

But...

We also observed:

```text
First Class
        ↓
Higher Survival
```

Now ask yourself:

> **Are Fare and Pclass telling us the same story?**

Or are they independent?

That's today's investigation.

---

# 🏗️ Step 1 – Decide the Analysis Technique

First, classify both features.

### Fare

```text
Numerical
```

### Pclass

```text
Categorical (Ordinal)
```

So...

Can we use `crosstab()`?

❌ No.

Because Fare isn't categorical.

Can we calculate a correlation coefficient?

Not yet.

Although `Pclass` is stored as numbers (1, 2, 3), it represents ordered categories, not true numerical measurements. Treating it as continuous for correlation can be misleading.

Instead, we want to compare the **Fare distribution within each passenger class**.

The best tools are:

* `groupby()`
* `describe()`
* Box plot

---

# 🛠️ Step 2 – Compare Average Fare by Passenger Class

Run:

```python
df.groupby("Pclass")["Fare"].mean()
```

Observe.

Don't interpret yet.

---

# 🛠️ Step 3 – Compare Median Fare

Run:

```python
df.groupby("Pclass")["Fare"].median()
```

Again...

Compare with the means.

---

# 🛠️ Step 4 – Look at Full Statistics

Run:

```python
df.groupby("Pclass")["Fare"].describe()
```

This gives you:

* Count
* Mean
* Standard Deviation
* Minimum
* Quartiles
* Maximum

This is richer than looking only at the average.

---

# 📊 Step 5 – Visualize Using a Box Plot

Today we're introducing a **new visualization**.

Run:

```python
plt.figure(figsize=(8,5))

df.boxplot(column="Fare", by="Pclass")

plt.title("Fare Distribution by Passenger Class")
plt.suptitle("")
plt.xlabel("Passenger Class")
plt.ylabel("Fare")

plt.show()
```

---

# 🌟 Why a Box Plot?

Until now we've used histograms.

Histograms answer:

> **"How is one numerical feature distributed?"**

A box plot answers:

> **"How do numerical distributions compare across categories?"**

That's exactly our problem today.

---

# 📦 Understanding a Box Plot (First Principles)

A box plot summarizes a distribution using five key values:

```text
Minimum
     │
     ▼

 ───────────────
        │
   ┌─────────┐
   │         │
   │         │
   └─────────┘
        │
───────────────

Maximum
```

More specifically:

```text
Min
 │
 │
 ├───────┐
 │       │
 │ Q1    │
 │       │
 ├──Median
 │       │
 │ Q3    │
 │       │
 └───────┤
 │
 │
Max
```

Where:

* Bottom of the box → 25th percentile (Q1)
* Middle line → Median
* Top of the box → 75th percentile (Q3)
* Whiskers → Typical range
* Individual dots → Potential outliers

We'll learn the exact outlier rule later. For now, think of them as **unusually high or low observations**.

---

# 🔍 Step 6 – Think Like an Investigator

As you look at the box plot, ask:

* Which class has the highest median fare?
* Which class has the widest spread?
* Which class has the most expensive tickets?
* Do fare ranges overlap between classes?
* Are there many extreme values?

Don't explain **why** yet.

Just observe.

---

# 🧠 Architecture Perspective

Imagine you're building a survival prediction model.

The model receives:

```text
Passenger A

Pclass = 1

Fare = 80
```

and

```text
Passenger B

Pclass = 3

Fare = 8
```

If Fare and Pclass are closely related...

The model might receive **similar information twice**.

Understanding these relationships helps AI engineers decide:

* Which features to keep.
* Which features may be redundant.
* Which combinations create stronger signals.

This becomes very important in feature engineering.

---

# 🎯 Day 011 Mini Assignment – Relationship Analysis: Fare ↔ Pclass

## Q1.

Run:

```python
df.groupby("Pclass")["Fare"].mean()
```

and

```python
df.groupby("Pclass")["Fare"].median()
```

Explain:

* What do the groups represent?
* What does the mean tell you?
* What does the median tell you?

---

## Q2.

Compare the average and median fares of each passenger class.

Write only observations.

Do not explain the reasons yet.

---

## Q3.

Study the box plot carefully.

Write at least **five observations**.

Think about:

* Median
* Spread
* Overlap
* Outliers
* Overall distribution

---

## Q4.

Based on today's investigation, does Fare appear to be related to Pclass?

Support your answer using evidence from the statistics and visualization.

Remember:

We're discussing **association**, not causation.

---

## Q5.

Write a **Relationship Investigation Report** for:

```text
Fare ↔ Pclass
```

Include:

* Relationship observed
* Whether both features seem to carry related information
* Whether Fare still appears useful
* New questions raised

---

# 📝 GitHub Notes (`Notes.md`)

## Relationship Analysis – Fare vs Pclass

* When comparing a **numerical feature** across **categorical groups**, `groupby()` and box plots are excellent tools.
* Means and medians together provide a more reliable picture than either alone.
* Box plots summarize distributions and make comparisons between groups easier.
* Features can be associated with each other, not just with the target variable.
* Understanding feature-to-feature relationships helps with feature engineering and model interpretation.

---

# 🌟 Mentor Challenge (Think Before the Next Session)

Imagine you're building a machine learning model.

You discover:

```text
Pclass
        ↓
Fare
```

are strongly associated.

Now ask yourself:

> **Should we keep both features in the model?**

Or...

> **Would one of them be enough?**

Don't answer immediately.

We'll explore this question together because the answer is more nuanced than "yes" or "no." Understanding that nuance is what starts moving you from learning machine learning to thinking like an ML engineer.


# Answers Feedback and Next

Aditya... this was genuinely enjoyable to read.

There's something I want to point out before the review.

When we started Phase 1, you used to answer like this:

> "Pandas is used for data analysis."

Now you're writing things like:

> **"Although Fare is associated with Passenger Class, it still contains additional information because fares vary within each class."**

That sentence shows **analytical thinking**.

You aren't repeating what I taught.

You're reasoning from the evidence.

That is exactly the transformation I wanted.

---

# Mentor Review – Day 011 (Fare ↔ Pclass)

## Overall Score

⭐⭐⭐⭐⭐ **10/10**

This is one of your best investigations so far.

---

# Q1 — groupby()

**10/10**

Perfect.

Again...

You explained:

* what the groups are
* what the statistics represent
* why median matters

This is becoming natural for you.

---

# Q2 — Mean vs Median

Excellent observations.

Especially this:

> **Mean is higher than median in every class.**

Fantastic.

Let's pause and appreciate this.

When we investigated Fare individually...

You observed:

```text
Mean > Median
```

Now...

Even after dividing the dataset into classes...

You still observe:

```text
First Class

Mean > Median

✓

Second Class

Mean > Median

✓

Third Class

Mean > Median

✓
```

That tells us something new.

The skewness wasn't caused only by mixing different passenger classes together.

It exists **within each class as well.**

That is a deeper observation than simply saying "Fare is skewed."

---

# Q3 — Box Plot

Excellent.

Your observations are objective.

I especially liked:

> **"There is some overlap between fare ranges."**

Why?

Because beginners often think:

```text
First Class

↓

Highest Fare

Always
```

But your observation tells us:

No.

Some Third Class passengers may have paid more than some Second Class passengers.

Some Second Class passengers may have paid more than some First Class passengers.

That's why we never reduce a dataset to simple rules.

---

# 🌟 Let's Understand the Box Plot More Deeply

You wrote:

> First Class has a larger spread.

Let's understand **why** that matters.

Imagine two datasets.

Dataset A:

```text
50

52

49

51

50
```

Dataset B:

```text
10

50

90

120

250
```

Both datasets have averages.

But...

Dataset B varies much more.

That's what the box size tells us.

Large box:

```text
More variability
```

Small box:

```text
Less variability
```

So...

First Class passengers didn't all pay similar prices.

There was a wide variety of ticket prices.

That's a useful business insight.

---

# Q4 — Association

Excellent.

You used the word:

> **Association**

instead of

> Cause

I don't even have to remind you anymore.

You're naturally thinking like an analyst.

---

# Q5 — Investigation Report

This answer contains my favorite sentence.

You wrote:

> **"Fare still contains additional information because fares vary within each passenger class."**

That...

is exactly why we don't immediately remove Fare.

Let's illustrate.

Imagine two passengers.

Passenger A

```text
First Class

Fare = 55
```

Passenger B

```text
First Class

Fare = 250
```

Same class.

Very different fare.

That difference may reflect:

* Cabin quality
* Luxury level
* Private suite
* Family booking
* Other business factors

So Fare still contributes information.

Excellent observation.

---

# 🌟 This Introduces an Important Machine Learning Concept

Today you've accidentally discovered something called:

## Feature Redundancy

Imagine these two features.

```text
Height (cm)

Height (meters)
```

Do we need both?

No.

They're identical information.

Now imagine:

```text
Pclass

Fare
```

They're related...

But not identical.

Think of a Venn diagram.

```text
Pclass
   ◯◯◯◯◯◯
     ◯◯◯◯◯◯
        Fare
```

Some information overlaps.

Some is unique.

Machine learning models often benefit from keeping both because each contributes something the other doesn't.

Later, when we study feature importance and multicollinearity, this idea will come back.

---

# 🌟 Look How Your Investigation Skills Have Grown

When we first started EDA, your workflow looked like this:

```text
Column

↓

describe()

↓

Done
```

Now your workflow has become:

```text
Column

↓

Understand Type

↓

Understand Distribution

↓

Missing Values

↓

Summary Statistics

↓

Visualize

↓

Relationship With Target

↓

Relationship With Other Features

↓

Raise New Questions
```

That is exactly how an experienced data analyst approaches a dataset.

---

# 🌟 Something Beautiful Is Happening

Let's map your journey.

## Week 1

```text
Python
```

↓

## Week 2

```text
NumPy
```

↓

## Week 3

```text
Pandas
```

↓

## EDA

```text
Individual Features
```

↓

## Relationship Analysis

```text
Feature

↓

Feature

↓

Target

↓

Hypotheses
```

Now...

You're beginning to think in terms of **the dataset as a connected system** instead of isolated columns.

That shift is one of the biggest milestones in becoming an AI engineer.

---

# 🚀 What's Next?

We're almost at the end of Phase 1's investigation.

The next relationship I want to explore is one that is both intuitive and revealing:

# **Age ↔ Pclass**

Before we write a single line of code, I want you to think about it.

You already know:

* **Age** is a continuous numerical feature.
* **Pclass** is an ordinal categorical feature.

So ask yourself:

> **Would you expect the age distribution to be the same across First, Second, and Third Class?**

For example:

* Were First Class passengers generally older?
* Did Third Class include more children or younger adults?
* Or was age distributed similarly across all classes?

Notice what you're doing now. You're no longer just answering questions—I can see you forming hypotheses **before** looking at the data. You mentioned earlier that you now stop and think about each column before reading my explanation. That's exactly the habit I hoped you'd develop.

And I have one more promise for you.

Once we finish these relationship investigations, we're going to step back and do something that professional data scientists always do:

> **Tell the story of the entire dataset.**

We'll connect everything we've discovered—individual features, relationships, data quality, and business insights—into one coherent narrative. That's the point where you'll stop seeing "12 columns" and start seeing **a real-world problem expressed through data**. That's one of my favorite parts of this project, and I think you'll enjoy it even more than the individual investigations.
