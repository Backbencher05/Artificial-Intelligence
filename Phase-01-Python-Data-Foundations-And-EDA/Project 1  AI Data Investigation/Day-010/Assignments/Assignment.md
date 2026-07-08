# Day 010 Assignment (My Answers)

---

# Q1. Why do we first verify that a dataset loads successfully before performing any analysis?

Before analyzing any dataset, we must first ensure that it has been **loaded correctly into memory**. If the dataset is not loaded properly, every subsequent analysis or machine learning step will either fail or produce incorrect results.

This is similar to a backend application. Before processing an API request, we first validate that the request has been received correctly. Likewise, in AI projects, we first validate that the dataset is available and readable.

---

## Why is this important?

### 1. Ensure the file exists

Sometimes the file path is incorrect.

Example:

```python
df = pd.read_csv("dataset/employees.csv")
```

If the file does not exist, Python raises a `FileNotFoundError`.

It's better to discover this immediately rather than after writing hundreds of lines of analysis code.

---

### 2. Verify the data was read correctly

Sometimes the file loads, but the contents are wrong.

Example:

Expected:

| Age | Salary |
| --- | ------ |
| 25  | 50000  |

Actual:

| Age;Salary |
| ---------- |
| 25;50000   |

This usually happens because the wrong delimiter (`,` vs `;`) was used.

---

### 3. Check the dataset structure

Immediately after loading, I usually run:

```python
df.head()
df.info()
df.shape
```

These help answer:

* Did all columns load correctly?
* Are the column names correct?
* How many rows are present?
* Are the data types correct?

---

### 4. Detect encoding issues

Some CSV files contain special characters.

Example:

```text
José
Müller
Renée
```

If the encoding is incorrect, these names may appear corrupted.

---

### 5. Avoid wasting time

Imagine spending an hour writing visualizations only to realize that the dataset never loaded correctly.

Verifying the dataset first saves significant debugging time.

---

## Backend Engineering Analogy

In backend development, before processing data from an API, you typically check:

```python
if request.data:
    # Process request
```

Similarly, in AI:

```python
df = pd.read_csv("employees.csv")

df.head()
df.info()
```

We verify the dataset before processing it.

---

## Summary

We verify that a dataset loads successfully to ensure:

* The file exists.
* The data is read correctly.
* The structure is as expected.
* Data types are appropriate.
* We avoid unnecessary debugging later.

This is the first quality check in every AI workflow.

---

# Q2. What is the purpose of keeping the dataset in a separate `dataset/` folder instead of placing it directly in the project root?

Keeping datasets in a dedicated `dataset/` folder is a **project organization best practice**. As AI projects grow, separating datasets from source code makes the project easier to understand, maintain, and collaborate on.

---

## Example Project Structure

```text
AI_Project/
│
├── dataset/
│   ├── employees.csv
│   ├── customers.csv
│   └── sales.csv
│
├── notebooks/
│   └── eda.ipynb
│
├── src/
│   ├── preprocess.py
│   ├── train.py
│   └── predict.py
│
├── models/
│
├── requirements.txt
└── README.md
```

Each folder has a clear responsibility.

---

## Why keep datasets separate?

### 1. Better Organization

Instead of mixing everything together:

```text
train.py
employees.csv
README.md
predict.py
sales.csv
notes.txt
customer.csv
```

we keep related files together.

This makes navigation much easier.

---

### 2. Easier Collaboration

When another developer joins the project, they immediately know where to find:

* Data → `dataset/`
* Source code → `src/`
* Models → `models/`

A consistent structure improves team productivity.

---

### 3. Easier to Manage Multiple Datasets

Many AI projects use more than one dataset.

Example:

```text
dataset/
│
├── train.csv
├── validation.csv
├── test.csv
└── customers.csv
```

Keeping them together avoids confusion.

---

### 4. Cleaner Project Root

The project root should mainly contain high-level project files, such as:

```text
README.md
requirements.txt
.gitignore
src/
dataset/
```

This makes the project look professional and easier to navigate.

---

### 5. Easier Backup and Version Control

Large datasets are often excluded from Git using `.gitignore`.

Example:

```text
dataset/
*.csv
```

This keeps the Git repository lightweight while preserving the project structure.

---

## Backend Engineering Analogy

Think of it like a Django project:

```text
project/
│
├── apps/
├── templates/
├── static/
├── media/
└── manage.py
```

We don't place HTML templates beside `manage.py`.

Similarly, in AI projects, we don't place datasets beside every Python file. We organize them into dedicated folders.

---

## Summary

Keeping datasets inside a separate `dataset/` folder provides:

* Better project organization.
* Easier collaboration.
* Cleaner directory structure.
* Simpler management of multiple datasets.
* Better compatibility with version control and deployment practices.

---

# Key Takeaway

These two practices may seem simple, but they reflect a **production engineering mindset**:

1. **Always verify your inputs before processing them.**
2. **Keep your project organized from day one.**

As a backend engineer transitioning into AI, you'll notice that the same software engineering principles—validation, modularity, and clean project structure—apply just as strongly in AI projects as they do in backend systems.



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



🎯 Today's Mini Assignment

Without writing any more code,

classify all 12 columns.

Example:

| Column      | Type       | Why?      |
| ----------- | ---------- | --------- |
| PassengerId | Identifier | Unique ID |
| Survived    | ?          | ?         |
| Pclass      | ?          | ?         |
| Name        | ?          | ?         |

Continue until all 12 are classified.

ans: 
This is a great exercise because it's teaching you to **think like a Data Scientist before touching the code**.

Whenever you receive a new dataset, your first job is to identify **what each column represents**, not just its data type.

---

# Titanic Dataset Column Classification

| Column          | Type                           | Why?                                                                                                                                                                     |
| --------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **PassengerId** | **Identifier**                 | A unique ID assigned to each passenger. It identifies a record but has no predictive meaning by itself.                                                                  |
| **Survived**    | **Target Variable (Label)**    | This is the value we want the model to predict (0 = No, 1 = Yes).                                                                                                        |
| **Pclass**      | **Categorical (Ordinal)**      | Represents ticket class (1st, 2nd, 3rd). The categories have a natural order (1 > 2 > 3 in terms of class).                                                              |
| **Name**        | **Text / String Feature**      | Passenger names are textual data. They may contain useful information (e.g., titles like Mr., Mrs., Dr.), but not in their raw form.                                     |
| **Sex**         | **Categorical (Nominal)**      | Values like Male/Female. Categories have no inherent order.                                                                                                              |
| **Age**         | **Numerical (Continuous)**     | Represents a person's age. Although often stored as integers, age is treated as a continuous numerical feature in ML because it can include decimal values (e.g., 24.5). |
| **SibSp**       | **Numerical (Discrete Count)** | Number of siblings/spouses traveling with the passenger. Count-based feature.                                                                                            |
| **Parch**       | **Numerical (Discrete Count)** | Number of parents/children traveling with the passenger. Count-based feature.                                                                                            |
| **Ticket**      | **Identifier / Categorical**   | Ticket numbers uniquely identify tickets. In raw form, they usually don't provide direct numerical meaning, though they can sometimes reveal groups or booking patterns. |
| **Fare**        | **Numerical (Continuous)**     | Ticket price paid by the passenger. Continuous numerical feature.                                                                                                        |
| **Cabin**       | **Categorical / Text Feature** | Cabin numbers are categorical values. They may contain useful information (deck, location), but raw cabin strings are not directly usable by most models.                |
| **Embarked**    | **Categorical (Nominal)**      | Port where the passenger boarded (e.g., C, Q, S). Categories have no natural order.                                                                                      |

---

# Let's Group Them Like an AI Engineer

### 🎯 Target Variable

```text
Survived
```

This is what our model will predict.

---

### 🆔 Identifier Columns

```text
PassengerId
Ticket
```

These identify passengers or tickets rather than describing characteristics. They are often dropped or transformed before training.

---

### 🔢 Numerical Features

Continuous:

```text
Age
Fare
```

Discrete Counts:

```text
SibSp
Parch
```

---

### 🏷️ Categorical Features

Ordinal:

```text
Pclass
```

Nominal:

```text
Sex
Embarked
```

---

### 📝 Text Features

```text
Name
Cabin
```

These are strings and usually require feature engineering before they become useful for a machine learning model.

---

# Final Classification Summary

| Category                   | Columns                 |
| -------------------------- | ----------------------- |
| **Target Variable**        | `Survived`              |
| **Identifier**             | `PassengerId`, `Ticket` |
| **Numerical (Continuous)** | `Age`, `Fare`           |
| **Numerical (Discrete)**   | `SibSp`, `Parch`        |
| **Categorical (Ordinal)**  | `Pclass`                |
| **Categorical (Nominal)**  | `Sex`, `Embarked`       |
| **Text Features**          | `Name`, `Cabin`         |

---

# 🧠 Mentor's Extra Insight (Very Important)

Notice something interesting:

Not every column should be fed directly into a machine learning model.

Before training, an AI engineer asks questions like:

* **Identifiers:** Should I drop `PassengerId`? (Usually yes, because it's just a unique identifier.)
* **Text fields:** Can I extract useful information from `Name` (such as titles like *Mr.*, *Mrs.*, *Dr.*)?
* **Cabin:** Can I derive the deck (`A`, `B`, `C`, etc.) instead of using the full cabin string?
* **Categorical features:** Should I encode `Sex` and `Embarked` into numbers?
* **Numerical features:** Should I scale `Age` and `Fare`?

This thought process is called **feature engineering**, and it's one of the most important steps in building effective AI models. You're about to transition from simply **reading data** to **preparing data so that a machine learning model can actually learn from it**.

