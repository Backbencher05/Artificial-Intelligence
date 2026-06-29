🚀 Phase 1 → Day 006 → Session 6
Data Visualization with Matplotlib

We now transition from:

How AI Computes

to

How Humans Understand Data

This is a major shift.

Session Goal

By the end of today, you should understand:

Why data visualization exists.
Why AI engineers visualize data before modeling.
What Matplotlib is.
Line Charts.
Bar Charts.
Histograms.
Scatter Plots.
How visualization connects to EDA and Machine Learning.
Part 1: Why Visualization Exists

Imagine I give you:

[12, 14, 15, 16, 15, 17, 18, 20, 21, 22]

Can you understand the trend?

Maybe.

Now imagine:

100,000 values

Suddenly:

Human Brain

becomes the bottleneck.

The Problem

Humans are bad at reading large tables.

Humans are excellent at spotting patterns visually.

Visualization converts:

Numbers
↓
Pictures
↓
Insights
Real AI Workflow

Before building a model:

Load Data
↓
Visualize Data
↓
Understand Data
↓
Clean Data
↓
Train Model

Notice:

Visualization happens BEFORE modeling

Almost always.

Part 2: What Is Matplotlib?

Matplotlib is Python's most popular visualization library.

Import:

import matplotlib.pyplot as plt

Think of:

plt

as:

Plotting Toolkit
Part 3: Line Plot

The simplest graph.

Example
import matplotlib.pyplot as plt

days = [1,2,3,4,5]
sales = [10,15,20,18,25]

plt.plot(days, sales)

plt.show()
What Does It Show?
Time
↓
Trend

Questions:

Increasing?
Decreasing?
Seasonal?
Stable?
Real AI Example

Track:

Training Loss

during model training.

Day 006 insight:

Many AI engineers stare at line plots every day.

Part 4: Labels Matter

Bad:

plt.plot(days, sales)

Better:

plt.plot(days, sales)

plt.title("Sales Trend")

plt.xlabel("Day")

plt.ylabel("Sales")

plt.show()

Good visualization tells a story.

Part 5: Bar Chart

Used for categories.

Example:

products = ["A", "B", "C"]

sales = [100, 150, 90]

plt.bar(products, sales)

plt.show()

Questions answered:

Which category is biggest?
Which category is smallest?
AI Example

Class Distribution

Cat
Dog
Bird

How many examples of each?

Bar chart.

Part 6: Histogram

One of the most important plots in AI.

Why?

It shows:

Distribution

Example

import numpy as np

ages = np.random.randint(
    18,
    60,
    1000
)

plt.hist(ages)

plt.show()

Questions answered:

Are values clustered?
Are values spread out?
Are there outliers?
AI Engineers Love Histograms

Because they reveal:

Data Quality

very quickly.

Part 7: Scatter Plot

Another extremely important plot.

Example

height = [150,160,170,180]
weight = [50,60,72,85]

plt.scatter(
    height,
    weight
)

plt.show()

Questions answered:

Relationship?
Correlation?
Trend?
AI Example
Years Experience
vs
Salary

Scatter plot.

Why This Matters

Suppose you see:

Experience ↑
Salary ↑

Strong relationship.

Useful for prediction.

Part 8: Outliers

Visualization helps detect strange data.

Example:

20
22
21
23
24
500

Table:

Hard to notice

Histogram:

Immediately obvious
Part 9: Real AI Workflow

Suppose we receive:

Customer Dataset

First questions:

Age distribution?
Income distribution?
Outliers?
Relationships?
Missing values?

Visualization answers many of these.

Architecture Perspective

Backend Engineers:

Logs
Metrics
Dashboards

to understand systems.

AI Engineers:

Plots
Charts
Distributions

to understand data.

Same philosophy:

Observe
↓
Understand
↓
Act
Hands-On Exercise

Create:

Day-006/practice/
Line Plot
import matplotlib.pyplot as plt

days = [1,2,3,4,5]

sales = [10,15,20,18,25]

plt.plot(days, sales)

plt.title("Sales Trend")

plt.xlabel("Day")

plt.ylabel("Sales")

plt.show()
Bar Chart
products = ["A","B","C"]

sales = [100,150,90]

plt.bar(products, sales)

plt.show()
Histogram
import numpy as np

ages = np.random.randint(
    18,
    60,
    1000
)

plt.hist(ages)

plt.show()
Scatter Plot
height = [150,160,170,180]

weight = [50,60,72,85]

plt.scatter(
    height,
    weight
)

plt.show()


## Day 006 Assignment
-------------------------------------------------------
Q1

Why is data visualization important in AI projects?

Q2

What kind of information is best represented using:

Line Plot
Bar Chart
Histogram
Scatter Plot
Q3

Why do AI engineers often visualize data before training a model?

Q4

What is an outlier?

Why can outliers be problematic?

Q5

Suppose you receive a dataset containing:

Age
Salary
Years Experience

Which visualizations would you use first and why?

Notes.md Topics

Document:

Why Visualization Exists
Matplotlib Basics
Line Plot
Bar Chart
Histogram
Scatter Plot
Outliers
Visualization in AI Workflow
Mentor Insight

Today marks another important transition.

Until now:

Data
↓
Arrays
↓
Matrices
↓
Computation

Now:

Data
↓
Visualization
↓
Understanding
↓
Insights

A strong AI engineer doesn't start by building models.

A strong AI engineer starts by asking:

"What is my data trying to tell me?"

Matplotlib is one of the first tools that helps answer that question. 🚀