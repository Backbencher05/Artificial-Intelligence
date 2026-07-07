Perfect. 😄

We're entering what I consider the **most exciting part of EDA**.

Until now, every investigation answered:

> **"What is this feature?"**

Now we'll answer:

> **"Does this feature help predict the target?"**

And just like before, we'll go **slow**, think like investigators, and not rush to machine learning.

---

# 🚢 Day 011 – Relationship Analysis (Part 2)

## Topic

# Pclass ↔ Survived

---

## Step 1 – Start with the Business Question

Again, before writing any code, ask yourself:

> **Does the passenger's ticket class have any relationship with survival?**

Remember:

`Pclass` represents:

```text
1 → First Class
2 → Second Class
3 → Third Class
```

Before touching Pandas, let's think.

---

## Step 2 – Form Hypotheses

Based on everything you've learned so far (and only that), write your hypotheses.

For example:

* Do you think First Class passengers survived more?
* Do you think Third Class passengers survived less?
* Could this simply be because wealthier passengers had better cabins?
* Or could there be no relationship at all?

There are no right or wrong answers yet.

These are just hypotheses.

---

# Step 3 – Use Crosstab Again

Now run:

```python
pd.crosstab(df["Pclass"], df["Survived"])
```

Don't interpret it immediately.

Just observe.

Ask yourself:

* What do the rows represent?
* What do the columns represent?
* What do the numbers represent?

Exactly the same questions we asked with `Sex`.

---

# Step 4 – Convert to Percentages

Now normalize the table:

```python
(
    pd.crosstab(
        df["Pclass"],
        df["Survived"],
        normalize="index"
    ) * 100
).round(2)
```

This tells us:

> **Within each passenger class, what percentage survived?**

Notice why `normalize="index"` is important.

It answers:

```text
Among First Class passengers...

How many survived?
```

instead of:

```text
Among all survivors...

How many were First Class?
```

That's a very important distinction.

---

# Step 5 – Visualize

Now create a stacked bar chart.

```python
pd.crosstab(
    df["Pclass"],
    df["Survived"]
).plot(
    kind="bar",
    stacked=True,
    figsize=(6,4)
)

plt.title("Survival by Passenger Class")
plt.xlabel("Passenger Class")
plt.ylabel("Number of Passengers")

plt.show()
```

Look carefully.

Sometimes the graph reveals patterns even before you calculate percentages.

---

# Step 6 – Think Like an AI Engineer

Don't stop after reading the percentages.

Ask deeper questions.

For example:

### If First Class has the highest survival...

Why?

Possible explanations (not conclusions):

* Better cabin location?
* Closer to lifeboats?
* More crew assistance?
* Higher fares?
* More women and children?

Notice:

We're generating hypotheses.

Not claiming facts.

---

# Architecture Perspective

Let's connect this to machine learning.

Suppose you're training a model.

The model sees:

```text
Passenger

↓

Pclass = 1
```

It also knows the historical outcomes.

If First Class passengers consistently survived more often...

the model begins to associate:

```text
Pclass

↓

Higher probability of survival
```

That's exactly what we're trying to discover through EDA.

---

# One New Thinking Habit

Today I want to introduce a habit that professional data scientists use.

Instead of saying:

> "Pclass affects survival."

Say:

> **"Pclass appears to be associated with survival in this dataset."**

Why?

Because EDA shows **patterns in data**.

It doesn't automatically prove cause and effect.

This wording keeps your analysis scientifically accurate.

---

# 🎯 Day 011 Mini Assignment – Relationship Analysis: Pclass ↔ Survived

---

## Q1.

What does the crosstab table tell you?

Explain:

* Rows
* Columns
* Values

in your own words.

---

## Q2.

Using the percentage table:

Compare the survival rates of:

* First Class
* Second Class
* Third Class

Write only observations.

Do **not** explain why yet.

---

## Q3.

Does the data support your earlier hypotheses?

If yes:

Explain how.

If not:

Explain what surprised you.

---

## Q4.

Why do we use `normalize="index"` instead of only looking at raw counts?

(Hint: Think back to `Sex ↔ Survived` and percentages.)

---

## Q5.

Write a **Relationship Investigation Report**

for:

```text
Pclass ↔ Survived
```

Include:

* Relationship observed
* Strength of the relationship
* Whether Pclass appears useful for prediction
* New questions raised by this analysis

---

# 📘 Notes for Your GitHub (`Notes.md`)

After completing today's assignment, add these key learnings:

### **Relationship Analysis – Pclass vs Survived**

* `pd.crosstab()` can compare any two categorical features.
* `normalize="index"` answers: *"Within each category, what percentage belongs to each outcome?"*
* Raw counts can be misleading when category sizes differ.
* Relationship analysis identifies features that may have predictive value.
* During EDA, describe relationships as **associations**, not proof of causation.
* Good EDA naturally leads to new questions that can be explored with other features.

---

## 🌟 Mentor Insight

Did you notice something?

Yesterday we asked:

```text
Sex
      ↓
Survived
```

Today:

```text
Pclass
        ↓
Survived
```

Tomorrow, we'll continue building this puzzle.

Eventually, we'll combine them:

```text
        Sex
          │
          ▼
Pclass ─► Survived ◄─ Age
          ▲
          │
        Fare
```

At that point, you'll stop seeing individual columns and start seeing the **entire dataset as an interconnected system**.

And that shift—from isolated features to interconnected relationships—is one of the biggest milestones in becoming an AI engineer.


# Assignment Feedback

Aditya...

I smiled while reading this assignment.

Not because the answers are correct (they are), but because I can **see your thinking evolving**.

A month ago, you would have written:

> "First Class survived more."

Now you write:

> "The data shows an association, not causation."

That is a huge difference.

---

# Mentor Review

## Q1 — Crosstab Interpretation

⭐⭐⭐⭐⭐ **10/10**

Perfect.

You no longer describe the function.

You describe **what the table is telling you**.

That's an important difference.

---

## Q2 — Observations

⭐⭐⭐⭐⭐ **10/10**

One sentence stood out:

> **"The survival rate decreases as passenger class changes from 1st → 2nd → 3rd."**

Excellent observation.

Notice this is much stronger than saying:

> "First Class survived more."

You're identifying a **trend**, not just comparing numbers.

This is what analysts do.

---

## Q3 — Hypothesis Verification

⭐⭐⭐⭐⭐ **10/10**

Again...

You wrote:

> "However, this shows association, not causation."

👏👏👏

You're beginning to sound like someone who has studied statistics.

---

## Q4 — normalize="index"

⭐⭐⭐⭐⭐ **10/10**

Beautiful explanation.

Especially this:

> **"normalize='index' converts each row into percentages, so every row totals 100%."**

That tells me you don't just know **how** to use it.

You know **what it mathematically means**.

That's much deeper understanding.

---

## Q5 — Relationship Report

Excellent.

But the last section impressed me the most.

Look at the questions you generated:

* Did females in Third Class survive at the same rate as females in First Class?
* Does Fare explain some of this?
* Are cabins related to class?
* Does combining features improve prediction?

Do you notice something?

---

# You're Starting to Think Like This

Initially your thinking looked like:

```text
Feature

↓

Analyze
```

Now it looks like:

```text
Feature A

↓

Relationship

↓

Raises Question

↓

Investigate Another Relationship
```

That's exactly how EDA grows.

One answer creates three new questions.

---

# Let Me Show You Something Interesting

Look at what we've discovered so far.

### Sex

```text
Female

↓

74%

Survival
```

### Pclass

```text
First Class

↓

63%

Survival
```

Now imagine someone asks:

> **Which feature is more important?**

Can we answer that yet?

No.

Why?

Because maybe...

```text
Female

+

First Class
```

is driving the result.

Or maybe...

```text
Female

+

Third Class
```

still survived at high rates.

We don't know yet.

---

# This Leads to One of the Biggest Ideas in Machine Learning

Individual features are useful.

But...

Sometimes **combinations** of features are even more informative.

Example:

Instead of

```text
Sex
```

Use

```text
Sex + Pclass
```

Instead of

```text
Age
```

Use

```text
Age + Pclass
```

Instead of

```text
Fare
```

Use

```text
Fare + Pclass
```

That's called **feature interaction**.

We'll study it properly later.

---

# A Small Correction (Very Minor)

You wrote:

> "Passengers traveling in higher classes had higher survival rates."

Technically correct.

But I would phrase it like this:

> **Passengers traveling in higher passenger classes (First and Second Class) had higher observed survival rates than passengers traveling in Third Class.**

Why?

Because it's a little more precise.

As you grow, you'll notice data scientists choose words very carefully.

---

# Here's Something I Want to Teach You Today

Until now we've answered:

```text
Sex

↓

Survived
```

and

```text
Pclass

↓

Survived
```

But imagine you're the machine learning model.

Would you rather know:

```text
Passenger

↓

Male
```

or

```text
Passenger

↓

Male

↓

Third Class
```

The second description gives more context.

That's why models often become more powerful when they learn from **multiple features together** rather than isolated ones.

---

# Where We Are in the Project

Let's zoom out.

```text
Project 1
│
├── Dataset Loaded ✅
├── Data Quality ✅
├── Individual Feature Investigation ✅
│
├── Relationship Investigation
│      │
│      ├── Sex ↔ Survived ✅
│      ├── Pclass ↔ Survived ✅
│      ├── Age ↔ Survived ← Next
│      ├── Fare ↔ Survived
│      └── ...
│
├── Feature Engineering
├── Final Insights
└── Project Report
```

Notice something beautiful?

You're no longer "learning Pandas."

You're conducting an **investigation**.

And that's exactly what I wanted this project to feel like.

---

# 🌟 Tomorrow's Investigation

Now we're moving to one of the most interesting relationships in the Titanic dataset:

```text
Age
      ↓
Survived
```

Unlike `Sex` and `Pclass`, `Age` is **continuous**, not categorical.

That means we'll introduce a **new style of analysis**.

You'll discover why continuous variables require different techniques than categorical ones.

This is another important step because, from now on, you'll learn that **the type of feature determines how we analyze it**. A good AI engineer doesn't apply the same method everywhere—they choose the right tool based on the nature of the data.

And that's exactly the kind of intuition we're building, one investigation at a time.
