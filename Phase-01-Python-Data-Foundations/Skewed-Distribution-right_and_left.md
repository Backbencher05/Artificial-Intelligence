🧠 Mentor Tip (The 5-Second Rule)

Whenever you see describe(), compare Mean and Median:


| If...             | Think...                                         |
| ----------------- | ------------------------------------------------ |
| **Mean ≈ Median** | Distribution is probably fairly symmetric        |
| **Mean > Median** | Likely **right-skewed** (long tail to the right) |
| **Mean < Median** | Likely **left-skewed** (long tail to the left)   |


Excellent question.

This is one of the **most important concepts in EDA** because almost every real-world dataset contains **skewed distributions**.

Let's understand it visually instead of memorizing the definition.

---

# First, what is a Distribution?

A **distribution** tells us:

> **How the data is spread out.**

For example, imagine these Fare values:

```text
5
7
8
9
10
12
15
18
20
25
30
35
40
45
50
```

A histogram of these values would look something like:

```text
Count
 5 |         █
 4 |      ████
 3 |    ██████
 2 |      ████
 1 |         █
   +------------------------
     5 10 15 20 25 30 35 40
```

This is fairly balanced.

---

# Now look at the Titanic Fare

Most passengers paid **small fares**.

Very few paid **very expensive fares**.

Imagine these fares:

```text
7
8
9
10
12
15
18
20
25
30
40
50
100
200
512
```

Notice:

Most values are small.

Only a few are very large.

---

The histogram looks like this:

```text
Count

10 | ████████████████████
 9 | ███████████████
 8 | ██████████
 7 | ███████
 6 | █████
 5 | ███
 4 | ██
 3 | █
 2 | █
 1 | █
   +-------------------------------------------->
      0   20   40   60 100 200 300 500
```

See the long stretch toward the **right**?

That long stretch is called the **tail**.

---

# Why is it called Right-Skewed?

Because the **tail** extends toward the **right-hand side**.

```text
███████████▇▆▅▄▃▂▁──────────────►
```

The tail points to the right.

Hence:

> **Right-skewed**

Another name is:

> **Positively Skewed**

These two mean the same thing.

---

# Why does this happen?

Suppose 10 people paid these fares:

```text
7
8
9
10
11
12
13
15
18
500
```

Nine passengers paid small fares.

One passenger paid **500**.

That one expensive ticket creates the long tail.

---

# Effect on Mean and Median

Let's calculate.

Data:

```text
7
8
9
10
11
12
13
15
18
500
```

---

Median:

Middle values:

```text
11
12
```

Median:

```text
11.5
```

---

Mean:

```text
603 / 10
```

=

```text
60.3
```

Notice something amazing.

```text
Median = 11.5

Mean = 60.3
```

One large value pulled the average upward.

That's exactly what happened in the Titanic dataset.

---

Your output was:

```text
Mean   = 32.20

Median = 14.45
```

The average is **much larger** than the median.

That tells us:

> A few passengers paid extremely expensive fares.

---

# Easy Memory Trick

## Right-skewed

```text
██████████────────────►
```

Tail →

Right

Mean >

Median

---

## Left-skewed

```text
◄──────────██████████
```

Tail →

Left

Mean <

Median

---

## Symmetric

```text
      █
    █████
  █████████
    █████
      █
```

Mean ≈ Median

---

# Titanic Example

Your statistics:

```text
Mean = 32.20

Median = 14.45

Max = 512.33
```

These immediately tell us:

* Most passengers paid low fares.
* A few passengers paid extremely high fares.
* Those expensive tickets pulled the mean upward.
* Therefore, the distribution is **strongly right-skewed**.

---

# Real-World Examples of Right-Skewed Data

Many real-world datasets look like this:

### Salaries

```text
Most people

₹30k
₹40k
₹50k

Few people

₹10 lakh
₹1 crore
```

Right-skewed.

---

### House Prices

```text
Most houses

₹40 lakh
₹50 lakh

Few houses

₹20 crore
```

Right-skewed.

---

### Company Revenue

```text
Most companies

₹10 lakh

₹15 lakh

Few companies

₹500 crore
```

Right-skewed.

---

### Titanic Fare

```text
Most passengers

₹7
₹10
₹15

Few passengers

₹200
₹300
₹512
```

Right-skewed.

---

# Why Do AI Engineers Care?

Because many machine learning algorithms assume that numerical features are **roughly symmetric**.

If a feature is heavily right-skewed, we may later apply transformations such as:

* Log Transformation (`log(x)`)
* Square Root Transformation
* Box-Cox Transformation

These reduce the skewness and can improve model performance.

Don't worry about these transformations yet—we'll study them later.

---

# 🧠 Mentor Tip (The 5-Second Rule)

Whenever you see `describe()`, compare **Mean** and **Median**:

| If...             | Think...                                         |
| ----------------- | ------------------------------------------------ |
| **Mean ≈ Median** | Distribution is probably fairly symmetric        |
| **Mean > Median** | Likely **right-skewed** (long tail to the right) |
| **Mean < Median** | Likely **left-skewed** (long tail to the left)   |

For the Titanic Fare:

```text
Mean   = 32.20
Median = 14.45
```

Since:

```text
32.20 > 14.45
```

you can immediately suspect a **right-skewed distribution**, even **before** looking at the histogram. The histogram then confirms what the statistics suggested. This habit—using summary statistics first and visualizations second—is exactly how experienced data scientists quickly understand a dataset.
