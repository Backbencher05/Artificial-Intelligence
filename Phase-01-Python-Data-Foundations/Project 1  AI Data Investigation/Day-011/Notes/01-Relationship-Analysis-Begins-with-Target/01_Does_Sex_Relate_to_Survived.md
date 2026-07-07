😂 Yes!!

You caught me.

You're absolutely right.

When we started Project 1, I **intentionally hid the bigger picture** from you.

If you remember, our journey looked like this:

```text
Load Dataset
      ↓
What are the columns?
      ↓
Classify the columns
      ↓
Investigate each column
      ↓
Data Quality
      ↓
Feature Engineering
```

I never started with:

> "Today we'll use `groupby()`."

or

> "Today we'll learn `crosstab()`."

Because that's **library-first learning**, and I don't want to mentor you that way.

Instead, I wanted you to experience how a real AI engineer approaches a dataset.

---

## Why I designed it this way

Imagine I had started like every online tutorial:

```python
df.groupby("Sex")["Survived"].mean()
```

You would have learned:

> **How to use `groupby()`.**

But you wouldn't know:

> **Why you're using it.**

Instead, our journey was:

```text
Question
      ↓
Hypothesis
      ↓
Need a tool
      ↓
Learn the tool
      ↓
Answer the question
```

Notice the difference?

The **question came first**.

---

# Here's something I haven't told you before...

This mentorship has actually been following the same process that senior data scientists use.

Every dataset goes through these stages:

```text
Stage 1
"What do I have?"

↓

Stage 2
"Can I trust it?"

↓

Stage 3
"What does each feature mean?"

↓

Stage 4
"What questions can I ask?"

↓

Stage 5
"What patterns exist?"

↓

Stage 6
"What features should I build?"

↓

Stage 7
"Now I'm ready for Machine Learning."
```

Without telling you, we've already completed the first **three** stages.

Today we're entering **Stage 4**.

---

# 🚀 Day 011 – Relationship Analysis Begins

## Topic

# Does `Sex` Relate to `Survived`?

This is our **first bivariate analysis**.

Remember:

```text
Univariate

One Feature
```

Today:

```text
Bivariate

Two Features
```

---

# Step 1 — Define the Question

Notice something important.

We are **not** starting with code.

We're starting with a business question.

Our question is:

> **"Is there a relationship between a passenger's sex and whether they survived?"**

That's our investigation.

---

# Step 2 — Observation vs Hypothesis

Before looking at the data, write your hypothesis.

You've actually done this already.

Your earlier hypothesis was:

> Females may have had a higher survival rate because of the "women and children first" policy.

Good.

Now we test it.

This is how science works.

```text
Observation
      ↓
Hypothesis
      ↓
Evidence
      ↓
Conclusion
```

---

# Step 3 — Meet `pd.crosstab()`

We're going to learn a new Pandas function.

```python
pd.crosstab()
```

What does it do?

Think of it as creating a **frequency table** between two categorical variables.

Run:

```python
import pandas as pd

pd.crosstab(df["Sex"], df["Survived"])
```

Don't worry about interpreting it yet.

Just look at the output.

You'll see something like:

```text
Survived    0     1
Sex
female     ...
male       ...
```

Ask yourself:

* What do the rows represent?
* What do the columns represent?
* What do the numbers represent?

Take a minute to think before moving on.

---

# Step 4 — Make It Easier to Read

Raw counts are useful, but percentages tell a clearer story.

Run:

```python
pd.crosstab(
    df["Sex"],
    df["Survived"],
    normalize="index"
) * 100
```

Then round it:

```python
(
    pd.crosstab(
        df["Sex"],
        df["Survived"],
        normalize="index"
    ) * 100
).round(2)
```

---

# Stop and Observe

Don't jump to conclusions.

Ask:

* For males, what percentage survived?
* For females, what percentage survived?
* Is the difference small or large?

Only after answering those questions should you write a conclusion.

---

# Step 5 — Visualize the Relationship

Create a stacked bar chart:

```python
pd.crosstab(df["Sex"], df["Survived"]).plot(
    kind="bar",
    stacked=True,
    figsize=(6,4)
)

plt.title("Survival by Sex")
plt.xlabel("Sex")
plt.ylabel("Number of Passengers")
plt.show()
```

Notice something:

We're **not** plotting one column anymore.

We're visualizing a **relationship**.

That's the key difference.

---

# A New Mental Model

When we investigated individual columns, our notebook looked like this:

```text
Age
 ↓
Histogram

Fare
 ↓
Histogram
```

Now it becomes:

```text
Sex
      +
Survived
        ↓
Crosstab
        ↓
Percentages
        ↓
Visualization
        ↓
Interpretation
```

This is a richer form of analysis.

---

# 🎯 Mini Assignment

## Q1

What does `pd.crosstab(df["Sex"], df["Survived"])` show?

Explain the meaning of:

* Rows
* Columns
* Values

in your own words.

---

## Q2

Using the percentage table, compare the survival rates of male and female passengers.

Write only **observations** first.

Do not explain **why** yet.

---

## Q3

Does the data support your earlier hypothesis?

If yes, explain how.

If not, explain why not.

---

## Q4

Why are percentages often more useful than raw counts when comparing groups of different sizes?

(Hint: Remember why we preferred percentages for missing values.)

---

## Q5

Write a **Relationship Investigation Report** for:

```text
Sex ↔ Survived
```

Include:

* What relationship you observed
* Strength of the relationship
* Whether Sex appears to be an important feature
* What further questions this relationship raises

---

# 🌟 Mentor Insight

Today is another milestone.

We're no longer asking:

> **"What is this feature?"**

We're asking:

> **"How does this feature relate to the outcome?"**

That shift is exactly what prepares us for machine learning.

A supervised machine learning model doesn't care only about what a feature is—it cares about **whether that feature helps predict the target**.

Relationship analysis is where we begin discovering those predictive signals, one question at a time.



# Assignment Report

Aditya...

I don't think you realize how much you've improved since Day 001.

When I compare your recent assignments with your first few days, I see a completely different way of thinking.

On Day 001, you were mainly explaining concepts.

Now you're doing something much closer to what a data scientist does:

```text
Observe
    ↓
Interpret
    ↓
Question
    ↓
Avoid jumping to conclusions
    ↓
Suggest further investigation
```

That is exactly the mindset I wanted to build.

---

# Mentor Review

## Q1 — Crosstab

⭐⭐⭐⭐⭐ (10/10)

I especially liked this sentence:

> "`crosstab()` answers: How many passengers from each sex belong to each survival category?"

Perfect.

You explained:

* Rows
* Columns
* Values

without simply repeating documentation.

That's exactly how I want you to learn.

---

## Q2 — Observations

⭐⭐⭐⭐⭐ (10/10)

This is probably my favorite sentence:

> "These are observations only. We are not yet explaining why this pattern exists."

👏👏👏

Do you remember a few days ago when I kept insisting:

> Observation ≠ Conclusion

Today you naturally wrote it yourself.

That means the habit is forming.

---

## Q3 — Hypothesis Verification

⭐⭐⭐⭐⭐ (10/10)

This sentence deserves appreciation:

> "It does not prove that being female was the direct cause of survival."

That one sentence shows you already understand one of the biggest ideas in statistics:

```text
Relationship

≠

Cause
```

Most beginners don't learn this until much later.

---

## Q4 — Percentages

Excellent.

You connected it back to missing-value percentages.

That tells me you aren't learning isolated topics anymore.

You're connecting concepts across days.

That's exactly how long-term understanding develops.

---

## Q5 — Investigation Report

This part impressed me the most:

> "Did survival rates differ for males and females within each passenger class?"

Did you notice what you just did?

You naturally proposed our **next investigation**.

That means you're beginning to drive the analysis instead of waiting for instructions.

---

# The Bigger Picture

Let's look at what happened today.

Initially we knew:

```text
Sex

↓

Male

Female
```

Now we know:

```text
Sex
      ↓
Relationship
      ↓
Survival
```

This is a completely different level of understanding.

---

# Something Very Important Happened Today

Today you unknowingly discovered what machine learning is trying to do.

Imagine a model asks:

> "Should I predict Survived = Yes?"

It doesn't know history.

It doesn't know Titanic.

It only knows data.

When it sees:

```text
Passenger

↓

Female
```

It notices:

```text
Historically

74%

Survived
```

When it sees:

```text
Passenger

↓

Male
```

It notices:

```text
Historically

19%

Survived
```

So the model thinks:

> "Sex seems useful."

That is exactly why we perform relationship analysis before model training.

We're identifying which features carry predictive information.

---

# One More Important Concept

Today we used:

```python
pd.crosstab()
```

You might think:

> "I learned another Pandas function."

I want you to think differently.

What we actually learned today was:

```text
Question

↓

Is there a relationship
between two categorical variables?
```

Then we found a tool to answer it.

The tool happened to be:

```python
pd.crosstab()
```

Always remember:

> **The question comes first. The function comes second.**

---

# A Small Enhancement (This is how senior data scientists think)

Let's make today's analysis even stronger.

Instead of stopping here:

```text
Sex
      ↓
Survived
```

Ask yourself:

> **"Could another variable be influencing this relationship?"**

For example:

```text
          Sex
            │
            ▼
      Survived
```

But maybe...

```text
        Pclass
          │
          ▼
Sex ───► Survived
```

Or:

```text
Age
 │
 ▼
Sex ───► Survived
```

Now you're thinking about **interactions** between features.

We'll study these in the coming days.

---

# Our Next Investigation

And this follows naturally from the question you wrote yourself.

Today we discovered:

```text
Sex

↓

Strong relationship with Survival
```

Tomorrow we'll investigate:

```text
Pclass
        ↓
Survived
```

We'll ask:

* Did first-class passengers survive more often?
* Was third class at a disadvantage?
* How strong is that relationship?
* Is `Pclass` another powerful predictor?

We'll again use:

* Counts
* Percentages
* Visualization
* Scientific reasoning

---

# 🌟 Mentor Reflection

I want to point out one more thing.

A few weeks ago, you asked me:

> "Why are we spending so much time on one column?"

Today, I don't think that question exists anymore.

Because now you can see that each column investigation wasn't just about learning Pandas—it was about building the intuition to ask good questions, interpret evidence carefully, and connect features into a coherent story.

That's exactly the skill you'll rely on later when working with much larger datasets, designing features for machine learning, or even evaluating outputs from LLM-based systems.

And I have to say, your pace has been excellent. You're not trying to "finish Phase 1." You're trying to **understand Phase 1**. In the long run, that's the approach that will make you a stronger AI engineer.
