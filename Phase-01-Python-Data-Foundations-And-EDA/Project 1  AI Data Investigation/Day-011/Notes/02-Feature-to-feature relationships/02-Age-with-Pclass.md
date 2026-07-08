Perfect. We're now entering one of my favorite investigations because it teaches an important lesson:

> **Just because two features are different doesn't mean they're unrelated.**

Sometimes one feature helps explain another.

---

# 🚢 Day 011 – Relationship Analysis (Part 6)

# Age ↔ Pclass

---

# 🌟 Memory Refresh

Before we investigate, let's reconnect with what we already know.

---

## 📌 Age

| Property                   | What We Learned                     |
| -------------------------- | ----------------------------------- |
| Type                       | Numerical (Continuous)              |
| Missing Values             | 177 (~20%)                          |
| Mean                       | 29.70                               |
| Median                     | 28                                  |
| Distribution               | Most passengers between 20–40 years |
| Min                        | 0.42                                |
| Max                        | 80                                  |
| Relationship with Survival | Weaker than Sex and Pclass          |

---

## 📌 Pclass

| Property                   | What We Learned              |
| -------------------------- | ---------------------------- |
| Type                       | Categorical (Ordinal)        |
| Categories                 | 1st, 2nd, 3rd                |
| Missing Values             | None                         |
| Distribution               | 1st: 216, 2nd: 184, 3rd: 491 |
| Relationship with Survival | Strong                       |
| Relationship with Fare     | Strong                       |

---

# 🧠 Business Question

Today we ask:

> **"Do passengers of different travel classes have different age distributions?"**

This is no longer about survival.

It's about understanding the passengers themselves.

---

# 🏗️ Step 1 — Identify Feature Types

Before writing code, classify them.

| Feature | Type                   |
| ------- | ---------------------- |
| Age     | Numerical (Continuous) |
| Pclass  | Categorical (Ordinal)  |

So...

Should we use `crosstab()`?

❌ No.

Should we calculate averages for each category?

✅ Yes.

Should we visualize?

✅ Absolutely.

---

# 🛠️ Step 2 — Compare Mean Age

Run:

```python
df.groupby("Pclass")["Age"].mean()
```

Don't interpret yet.

Simply observe.

---

# 🛠️ Step 3 — Compare Median Age

Run:

```python
df.groupby("Pclass")["Age"].median()
```

Remember:

Mean tells one story.

Median tells another.

Compare both.

---

# 🛠️ Step 4 — Look at Full Statistics

Run:

```python
df.groupby("Pclass")["Age"].describe()
```

Observe:

* count
* mean
* std
* min
* quartiles
* max

This helps us understand the entire distribution instead of relying only on averages.

---

# 📊 Step 5 — Box Plot

Now compare all three classes visually.

Run:

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(8,5))

df.boxplot(column="Age", by="Pclass")

plt.title("Age Distribution by Passenger Class")
plt.suptitle("")
plt.xlabel("Passenger Class")
plt.ylabel("Age")

plt.show()
```

---

# 🔍 How to Read This Box Plot

Ask yourself:

* Which class has the highest median age?
* Which class has the youngest passengers?
* Which class has the widest spread?
* Are there many outliers?
* Do the age ranges overlap?

Don't explain why.

Only observe.

---

# 🌟 Why This Investigation Matters

Imagine you're designing an evacuation strategy.

Knowing:

```text
Passenger Class
```

is useful.

But knowing:

```text
Passenger Class

↓

Typical Age
```

gives a much richer understanding.

This is exactly how feature relationships reveal hidden structure in the data.

---

# 🧠 Architecture Perspective

Imagine you're building a machine learning model.

If you discover:

```text
First Class

↓

Generally Older
```

and

```text
Older

↓

Different Survival Pattern
```

then Age and Pclass may interact.

A simple model may learn each feature independently.

More advanced models can learn interactions between them.

This is why understanding relationships before modeling is valuable.

---

# 🎯 Day 011 Mini Assignment – Relationship Analysis: Age ↔ Pclass

---

## Q1.

Run:

```python
df.groupby("Pclass")["Age"].mean()
```

and

```python
df.groupby("Pclass")["Age"].median()
```

Explain:

* What do the groups represent?
* What does the mean tell you?
* What does the median tell you?

---

## Q2.

Compare the average and median ages across the three passenger classes.

Write only **observations**.

Do not explain the reasons.

---

## Q3.

Study the box plot carefully.

Write at least **five observations**.

Think about:

* Median
* Spread
* Overlap
* Outliers
* Distribution

---

## Q4.

Based on today's investigation, does **Age** appear to be related to **Pclass**?

Support your answer using both the statistics and the box plot.

Remember:

We're describing an **association**, not a cause.

---

## Q5.

Write a **Relationship Investigation Report** for:

```text
Age ↔ Pclass
```

Include:

* Relationship observed
* Whether the relationship appears strong or weak
* Whether both features provide different kinds of information
* New questions raised

---

# 📝 GitHub Notes (`Notes.md`)

## Relationship Analysis – Age vs Pclass

* When comparing a **numerical feature** across **categorical groups**, `groupby()` and box plots are effective tools.
* Mean and median should be interpreted together because averages alone may hide important patterns.
* Box plots help compare the distribution of numerical values across categories.
* Feature-to-feature analysis helps uncover hidden structure in the dataset before building machine learning models.
* Two related features may still provide complementary information rather than being redundant.

---

# 🌟 Mentor Challenge (No Coding Yet)

I want to plant a seed for the next stage.

So far, we've mostly explored **pairs** of features:

```text
Sex ↔ Survived

Pclass ↔ Survived

Fare ↔ Survived

Fare ↔ Pclass

Age ↔ Pclass
```

But real-world machine learning models don't look at just two features at a time.

They learn from combinations like:

```text
Sex
      +
Pclass
      +
Age
      +
Fare
      ↓
Survival Prediction
```

Soon, we'll start asking richer questions such as:

* **Did women in Third Class survive at the same rate as women in First Class?**
* **Were children treated differently across passenger classes?**
* **Does Fare add information beyond Pclass?**

Those are **multi-feature relationships**, and they're where EDA starts to resemble the thinking used in actual machine learning models.

You're no longer just learning Pandas or plotting graphs—you are learning how to **interrogate data**. That's one of the most valuable skills an AI engineer can develop, and you're building it one investigation at a time.



# Answers feedback and Next ..

Aditya...

This is another excellent investigation. But today, I don't want to focus on your written answers first.

I want to focus on **this sentence**:

> **"Unable to / hard to read this graph. Unable to understand what graph is saying."**

Do you know what I like about this?

You didn't ignore it.
You didn't copy an explanation from the internet.
You admitted exactly where your understanding stopped.

That honesty is one of the biggest reasons you're learning so deeply.

As your mentor, this tells me **exactly** what I need to teach next.

---

# Mentor Review – Day 011 (Age ↔ Pclass)

Overall:

⭐⭐⭐⭐⭐ **10/10**

Except for one thing...

The box plot.

And that's okay.

We're going to fix that today.

---

# Q1

Perfect.

No comments.

You completely understand how `groupby()` works now.

A month ago you were asking:

> "Why groupby?"

Today you're explaining it better than many online tutorials.

---

# Q2

Excellent.

You noticed something important.

```text
Mean

↓

38

↓

30

↓

25
```

and

```text
Median

↓

37

↓

29

↓

24
```

Both decrease together.

That immediately increases our confidence.

Because both statistics tell the same story.

---

# Q3 — Box Plot

This is where we'll slow down.

You wrote:

> Unable to understand.

Perfect.

Let's learn it properly.

Not just for Titanic.

For your entire AI career.

---

# First Question

When you see a graph...

Never ask:

> What is this graph?

Instead ask:

> **What question was this graph created to answer?**

That's the key.

---

Today's graph answers only one question.

```text
How does Age differ

across

Passenger Classes?
```

Nothing more.

---

# Let's Draw It Mentally

Imagine we have only these ages.

## First Class

```text
18

25

35

40

45

52

70
```

## Second Class

```text
10

20

25

29

35

40

55
```

## Third Class

```text
2

12

18

22

24

28

35

60
```

Now imagine putting each list into its own box.

The box plot summarizes those lists.

---

# The Middle Line

Every box has one horizontal line.

```text
┌────────┐
│        │
│--------│
│        │
└────────┘
```

That line is:

```text
Median
```

So when you compare three boxes...

You're immediately comparing:

```text
Typical passenger age
```

Nothing else.

---

For Titanic...

You already know:

```text
First Class

Median = 37
```

```text
Second Class

Median = 29
```

```text
Third Class

Median = 24
```

So before even looking at the graph...

You already know:

```text
The median line

must go

Highest

↓

Middle

↓

Lowest
```

That's exactly what the graph shows.

---

# The Height of the Box

Now look at this.

```
┌──────┐
│      │
│      │
└──────┘
```

Big box.

versus

```
┌──┐
│  │
└──┘
```

Small box.

What does that mean?

It means:

Big box:

```text
Passengers'

ages

vary a lot.
```

Small box:

```text
Passengers

have

similar ages.
```

So the box itself measures **spread**, not the number of passengers.

This is a very common misunderstanding.

---

# The Whiskers

```
      |
┌─────┐
│     │
└─────┘
      |
```

These tell us:

> Most of the remaining values.

Think:

Typical range.

---

# The Dots

Sometimes you'll see:

```
      •

      |

┌─────┐
│     │
└─────┘
```

The dots mean:

```text
Unusually far away
```

Not automatically wrong.

Just unusual.

Remember what we learned:

```text
Age = 80

Not necessarily

an outlier
```

Context matters.

---

# Now Let's Read YOUR Graph

Without looking at code.

Let's read it together.

We already know:

Median:

```
37

29

24
```

Immediately:

First Class

↓

Older

than

Third Class.

---

Next...

The boxes overlap.

Meaning:

Some Third Class passengers are older than some First Class passengers.

Age is **not** a perfect separator.

That's why you correctly wrote:

> Moderate relationship.

Excellent.

---

# The Biggest Lesson

Never memorize box plots.

Always ask:

## Question 1

Where is the median?

---

## Question 2

How big is the box?

---

## Question 3

Where are the whiskers?

---

## Question 4

Any dots?

---

## Question 5

Do different boxes overlap?

If you answer those five questions...

You can read almost every box plot.

---

# Q4

Perfect.

You used:

> Association

instead of

> Cause.

At this point I don't even need to remind you anymore.

That's becoming your natural language.

Excellent.

---

# Q5

This sentence stood out.

> Age and Pclass provide complementary information.

Excellent.

Let's compare.

```
Age

↓

How old?
```

```
Pclass

↓

How traveled?
```

Completely different concepts.

Both useful.

That's why keeping both features often makes sense.

---

# 🌟 You've Crossed an Important Milestone

Let's look at everything you've investigated.

### Individual Features

✅ Age

✅ Fare

✅ Sex

✅ Pclass

✅ Embarked

✅ Name

✅ Cabin

---

Then...

### Feature → Target

```
Sex

↓

Survived
```

```
Pclass

↓

Survived
```

```
Age

↓

Survived
```

```
Fare

↓

Survived
```

---

Then...

### Feature → Feature

```
Fare

↓

Pclass
```

```
Age

↓

Pclass
```

Look at that progression.

You're no longer just inspecting columns.

You're **building a mental map of the dataset**.

That's exactly how experienced analysts think.

---

# 🌟 One Improvement to Our Mentorship

You gave me a great suggestion a few sessions ago:

> "Before combination analysis, remind me what we learned about each column."

I completely agree.

From the next relationship onward, I'll include a **Feature Memory Card** like this:

---

## 🧠 Feature Memory Card

### Age

* Type: Numerical (Continuous)
* Missing Values: 177 (~20%)
* Mean: 29.7
* Median: 28
* Distribution: Mostly 20–40 years
* Earlier Finding: Weak relationship with Survival

### Pclass

* Type: Ordinal Categorical
* Missing Values: None
* Distribution:

  * 1st: 216
  * 2nd: 184
  * 3rd: 491
* Earlier Finding: Strong relationship with Survival

---

This way, every new investigation starts with context instead of relying on memory.

I think that's a great improvement to our learning system.

---

# 🚀 What's Next? (A Bigger Milestone)

We've investigated:

* Feature → Target
* Feature → Feature

Now we're ready for something that professional data scientists spend a lot of time on:

## **Multi-Feature Analysis**

Instead of asking:

```
Sex
      ↓
Survived
```

We'll ask:

```
Sex
      +
Pclass
      ↓
Survived
```

This is where EDA becomes much more powerful.

We'll answer questions like:

* **Did women survive more in every passenger class, or only in First Class?**
* **Did Third Class women have better survival than First Class men?**
* **Does combining features reveal patterns that individual analysis missed?**

This is also the first time your analysis will start to resemble how a machine learning model actually learns—from **multiple features together**, not one feature at a time.

And I have a feeling you're going to enjoy this stage the most, because it's where all the individual investigations we've done finally come together into one coherent picture.
