There's one important concept I'd like to introduce today because it appears naturally in this analysis.

You wrote:

> **Sex and Passenger Class together provide a much better understanding of survival than either feature alone.**

This sentence has a formal name in Machine Learning.

## Interaction Effect (Feature Interaction)

Suppose we build three models.

### Model A

Uses only:

```text
Sex
```

Prediction:

```text
Female
↓

Higher Survival
```

---

### Model B

Uses only:

```text
Pclass
```

Prediction:

```text
First Class
↓

Higher Survival
```

---

### Model C

Uses both:

```text
Female
        +
First Class
        ↓
Very High Survival
```

Notice something?

The combination gives us **new information** that wasn't fully visible from either feature alone.

That is called a **feature interaction**.

---

Imagine another example.

A hospital wants to predict disease risk.

Feature 1:

```text
Age
```

Feature 2:

```text
Smoking
```

Individually:

```text
Older Age

↓

Higher Risk
```

and

```text
Smoking

↓

Higher Risk
```

But together:

```text
Old
     +
Smoking
     ↓
Extremely High Risk
```

The interaction is stronger than either feature individually.

Modern ML models (Random Forests, XGBoost, Neural Networks) are very good at discovering these interactions automatically.

---

# Why This Matters Later

When we reach Feature Engineering, you'll sometimes create interaction features manually.

For example:

```python
FamilySize = SibSp + Parch + 1
```

or

```python
Fare_Per_Person = Fare / FamilySize
```

Those are engineered because the **combination** contains more information than the original columns.

Today is the first time you're naturally seeing why.
