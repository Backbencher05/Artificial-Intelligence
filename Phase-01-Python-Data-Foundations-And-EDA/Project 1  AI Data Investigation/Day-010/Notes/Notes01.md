Aditya,

This is exactly what I was hoping you would say.

> **"We'll go slow, understand, and move ahead step by step."**

I completely agree.

In fact, **I don't want to give you the complete project in one go.**

Because that's not how senior engineers work.

A senior engineer doesn't wake up and write a 2,000-line AI pipeline.

They build it incrementally:

```text
Understand the problem
        ↓
Understand the data
        ↓
Inspect
        ↓
Clean
        ↓
Analyze
        ↓
Visualize
        ↓
Document
        ↓
Only then think about modeling
```

So for our mentorship, we're going to treat this exactly like a real project.

---

# 🚀 Phase 1 Final Project

## Theme

Instead of calling it:

```text
Day 010 Project
```

Let's call it:

# **Project 1 — AI Data Investigation**

Because that's what you'll actually be doing.

Your role is **not** "Machine Learning Engineer" yet.

Your role is:

```text
AI Data Investigator
```

---

# 🎯 Project Goal

By the end of this project, you should be able to receive any CSV file and confidently answer questions like:

* What does this dataset contain?
* Is the data clean?
* Are there missing values?
* Are there outliers?
* What patterns exist?
* Which features seem important?
* What should be done before machine learning?

If you can do that confidently, then **Phase 1 has achieved its purpose**.

---

# 📂 Project Structure

Inside your repository:

```text
Artificial-Intelligence/
│
├── Phase-01-Python-for-AI/
│
│   ├── Day-010-011-Final-Project/
│   │
│   ├── Notes.md
│   ├── Assignment.md
│   ├── Resources.md
│   ├── project.py
│   ├── dataset/
│   └── screenshots/
```

Later, when we generate graphs, save screenshots in the `screenshots/` folder for your GitHub documentation.

---

# 📊 The Dataset

For this project, I'd like us to use a dataset that is:

* Small enough to understand.
* Rich enough for EDA.
* Widely used in AI education.
* Contains numerical and categorical features.
* Has some missing values.

My recommendation is the **Titanic dataset**.

Why?

Because it has everything we need:

* Numerical columns (`Age`, `Fare`)
* Categorical columns (`Sex`, `Embarked`, `Pclass`)
* Missing values
* Interesting relationships
* A clear target column (`Survived`) that we'll use later in Phase 2 for Machine Learning.

Even though we're **not building a model now**, choosing this dataset prepares us for the next phase.

---

# 🗺️ Project Roadmap

We'll split the project into small milestones.

## Step 1 (Today)

### Project Setup

* Create folders.
* Download the dataset.
* Load it with Pandas.
* Verify it loads correctly.
* Perform an initial inspection.

Nothing more.

---

## Step 2

### Dataset Investigation

* `head()`
* `tail()`
* `shape`
* `columns`
* `info()`
* `describe()`

Goal:

Understand the dataset.

---

## Step 3

### Data Cleaning

* Missing values
* Duplicate rows
* Incorrect data types
* Initial observations

---

## Step 4

### Visualization

* Histograms
* Bar charts
* Scatter plots
* Distribution analysis

---

## Step 5

### EDA

Ask questions like:

* Did women survive more often?
* Did age affect survival?
* Did ticket class matter?
* Which features appear most informative?

Notice how we're **asking questions**, not just making plots.

---

## Step 6

### Documentation

This is something many tutorials skip.

You'll write:

* Project summary
* Key insights
* Challenges
* Business observations
* AI observations

This becomes excellent GitHub content.

---

# 🎯 Today's Objective (Step 1)

Let's do only one thing.

## Create the Folder Structure

```text
Day-010-011-Final-Project/
│
├── dataset/
├── screenshots/
├── project.py
├── Notes.md
├── Assignment.md
└── Resources.md
```

---

## Download the Dataset

We'll use the Titanic dataset.

Place:

```text
train.csv
```

inside:

```text
dataset/
```

---

## Load the Dataset

In `project.py`:

```python
import pandas as pd

df = pd.read_csv("dataset/train.csv")

print(df.head())
```

If the file path is correct, you should see the first five rows.

---

# 🧠 Today's Learning Goal

Notice something.

We are **not** starting with:

```python
df.describe()
```

or

```python
df.isnull()
```

Why?

Because the first responsibility of an engineer is simply to answer:

> **Can I access the data?**

Only after that do we begin exploring it.

This might sound trivial, but in real projects, a surprising number of issues happen before analysis even begins—wrong file paths, encoding problems, unexpected delimiters, missing files, and so on.

---

# 📋 Today's Assignment

Very small.

Once you've completed Step 1, answer these questions:

### Q1

Why do we first verify that a dataset loads successfully before performing any analysis?

---

### Q2

What is the purpose of keeping the dataset in a separate `dataset/` folder instead of placing it directly in the project root?

---

### Q3

After loading the Titanic dataset, simply tell me:

* How many rows do you see?
* How many columns?
* What are the first five column names?

*(Don't analyze them yet. Just observe.)*

---

# 🎓 Mentor's Promise

From this point onward, I'm going to mentor you the same way a tech lead would mentor a junior AI engineer on their first project.

That means:

* We will never rush.
* Every step will have a clear purpose.
* I'll explain **why** before **how**.
* I'll keep connecting what we're doing today with where we're heading in Phase 2 (Machine Learning).

One final thing.

When we complete this project, I don't want you to feel like:

> "I followed a tutorial."

I want you to feel like:

> **"I investigated a real dataset and understood it myself."**

That's a very different experience—and it's the one that builds confidence.

So let's take it one step at a time, just as we planned. 🚀


Perfect.

From this point onward, imagine this scenario:

> You have just joined a company as an **AI Engineer**.

On your first day, your manager says:

> **"Here's the Titanic dataset. Before anyone builds a machine learning model, I want you to investigate the data and prepare a report."**

That's exactly what we're going to do.

---

# 🚀 Project 1 — AI Data Investigation

## Step 1 — Project Planning

Before writing code, let's answer one question.

> **What are we trying to achieve?**

Not:

> Build a model.

Our objective is:

```text
Receive Raw Dataset
        ↓
Understand Dataset
        ↓
Assess Data Quality
        ↓
Discover Patterns
        ↓
Document Insights
        ↓
Prepare for Machine Learning
```

This mindset is important because **Machine Learning is not the goal**.

Understanding the data is.

---

# Step 2 — Why Titanic?

Before downloading anything, I want you to understand **why** we're using this dataset.

There are thousands of datasets.

So why Titanic?

Let's look at it from an engineering perspective.

## 1. It Represents a Real Business Problem

Imagine you're working for a shipping company.

They ask:

> **"Can we identify the factors that influenced survival?"**

That's a prediction problem.

Later, in Phase 2, we'll train a model to answer it.

But today, we're asking:

> **"What does the data tell us?"**

---

## 2. It Contains Different Types of Data

You'll work with:

### Numerical Features

Examples:

* Age
* Fare
* SibSp (siblings/spouses aboard)
* Parch (parents/children aboard)

---

### Categorical Features

Examples:

* Sex
* Embarked
* Pclass

---

### Text Features

Examples:

* Name
* Ticket
* Cabin

---

### Target Feature

```text
Survived
```

Later this becomes:

```python
y
```

the value we want to predict.

---

## 3. It Contains Real Problems

Unlike classroom examples, it includes:

* Missing values
* Mixed data types
* Categorical variables
* Irrelevant columns
* Real relationships

Exactly what AI engineers encounter in practice.

---

# Step 3 — Understanding the Dataset Before Opening It

This is something many tutorials skip.

Before reading the CSV, let's understand **what each column means**.

| Column      | Meaning                           | Type                |
| ----------- | --------------------------------- | ------------------- |
| PassengerId | Unique passenger identifier       | Identifier          |
| Survived    | 0 = No, 1 = Yes                   | Target              |
| Pclass      | Passenger class (1, 2, 3)         | Categorical/Numeric |
| Name        | Passenger name                    | Text                |
| Sex         | Male/Female                       | Categorical         |
| Age         | Passenger age                     | Numeric             |
| SibSp       | Number of siblings/spouses aboard | Numeric             |
| Parch       | Number of parents/children aboard | Numeric             |
| Ticket      | Ticket number                     | Text                |
| Fare        | Ticket fare                       | Numeric             |
| Cabin       | Cabin number                      | Text                |
| Embarked    | Port of embarkation               | Categorical         |

---

# Pause Here

I want you to notice something.

Not every column has the same purpose.

For example:

### PassengerId

```text
101
102
103
```

Does it help predict survival?

Probably not.

It only identifies a passenger.

---

### Age

Could age influence survival?

Possibly.

---

### Sex

Could sex influence survival?

Possibly.

---

### Fare

Could ticket fare matter?

Possibly.

---

Already, without opening the dataset, you're beginning to think like an AI engineer.

---

# Step 4 — Project Folder

Your structure should look like this:

```text
Day-010-011-Final-Project/
│
├── dataset/
│   └── train.csv
│
├── screenshots/
│
├── project.py
├── Notes.md
├── Assignment.md
└── Resources.md
```

---

# Step 5 — The First Lines of Code

Now we write the simplest possible program.

```python
import pandas as pd

# Load the dataset
df = pd.read_csv("dataset/train.csv")

# Verify that it loaded
print("Dataset loaded successfully!")

# Preview the first five rows
print(df.head())
```

Notice what we're doing.

We're **not analyzing**.

We're simply answering:

> "Can I successfully access the data?"

That is the first milestone of every data project.

---

# Why Don't We Write More Code?

Because I want you to build the habit of validating each step before moving on.

Think of it like backend development.

When building an API, you don't immediately implement:

* Authentication
* Validation
* Business logic
* Database writes
* Notifications

Instead, you first make sure:

```text
Request
        ↓
Endpoint Works
```

Only then do you add more.

We're following the same engineering discipline here.

---

# 🎯 Today's Task

Complete only these steps:

1. Create the project folder structure.
2. Place `train.csv` inside the `dataset` folder.
3. Run `project.py`.
4. Confirm that:

   * The dataset loads successfully.
   * `df.head()` displays the first five rows.

Don't call:

* `info()`
* `describe()`
* `shape()`

yet.

We'll do that in the next step, because I want you to first establish the habit of **verifying before investigating**.

---

# One Small Challenge Before You Run the Code

Look at the column list again:

* PassengerId
* Survived
* Pclass
* Name
* Sex
* Age
* SibSp
* Parch
* Ticket
* Fare
* Cabin
* Embarked

Without looking at the data, answer this:

> **Which three columns do you think are most likely to have missing values, and why?**

This is a prediction exercise.

You're not expected to be correct.

I want to see how you're starting to reason about data **before** seeing it.

That's exactly how experienced AI engineers approach unfamiliar datasets.


Answers: 
------------------------
This is exactly the kind of question an AI engineer should ask **before** writing any code. We're making hypotheses based on our understanding of the data.

## My Prediction

### 1. Cabin ⭐⭐⭐ (Most likely)

**Reason:**

Not every passenger would have a cabin number recorded.

Possible reasons:

* Some passengers (especially 3rd class) may not have had assigned cabins.
* Cabin information may not have been recorded or preserved.
* Records could be incomplete.

So I would expect **many missing values** in this column.

---

### 2. Age ⭐⭐

**Reason:**

Age is often missing in real-world datasets.

Possible reasons:

* Passenger didn't disclose their age.
* Age wasn't recorded during ticket booking.
* Historical records were incomplete.

This is very common in datasets, so I would expect some missing values here.

---

### 3. Embarked ⭐

**Reason:**

Embarked (boarding port) is usually required information, but a few records might still be missing due to:

* Data entry errors.
* Missing historical records.
* Unknown boarding location.

I expect **very few missing values**, but it's still a candidate.

---

## Columns I Don't Expect to Have Many Missing Values

### PassengerId

Unique identifier generated for every passenger.

Should never be missing.

---

### Survived

This is the target variable.

The dataset wouldn't be useful if many target values were missing.

---

### Pclass

Ticket class (1st, 2nd, 3rd).

Required during booking.

---

### Sex

Usually recorded for every passenger.

---

### Name

Every passenger should have a name.

---

### Ticket

A passenger must have a ticket number.

---

### Fare

Ticket price should always exist.

---

### SibSp

Number of siblings/spouses aboard.

If none, it's recorded as **0**, not NaN.

---

### Parch

Number of parents/children aboard.

Again, **0** is a valid value, so missing values are less likely.

---

## My Final Prediction

| Column       | Likelihood of Missing Values | Why                                                                             |
| ------------ | ---------------------------- | ------------------------------------------------------------------------------- |
| **Cabin**    | ⭐⭐⭐ Very High                | Many passengers may not have an assigned or recorded cabin.                     |
| **Age**      | ⭐⭐ Moderate                  | Age is often unavailable or not recorded in historical datasets.                |
| **Embarked** | ⭐ Low                        | A few records may have missing boarding locations due to incomplete data entry. |

---

### Backend Engineering Perspective

This is similar to designing an API before seeing production data.

You'd ask:

* Which fields are **mandatory**?
* Which fields are **optional**?
* Which fields are most likely to be `NULL`?

For the Titanic dataset:

* **Mandatory fields:** `PassengerId`, `Name`, `Pclass`, `Ticket`, `Fare`
* **Potentially optional fields:** `Cabin`, `Age`, `Embarked`

This kind of reasoning is a valuable habit. Good AI engineers don't just inspect data—they first **predict what they expect to find**, then verify it with code. That's exactly the mindset your instructor is trying to develop.


# check Notes2: 
Project Step 3 — Data Quality Assessment

Tomorrow (or in the next session), we'll investigate questions like:

Which columns have missing values?
How many missing values?
Which columns are complete?
Are there duplicate rows?
Are the data types appropriate?
Are there obvious inconsistencies?

Notice something.

We're still not cleaning.

We're assessing.

This is another habit I want you to build:

Observe
      ↓
Assess
      ↓
Plan
      ↓
Act

instead of:

See problem
      ↓
Immediately fix it

That disciplined approach is one of the biggest differences between experienced engineers and beginners.