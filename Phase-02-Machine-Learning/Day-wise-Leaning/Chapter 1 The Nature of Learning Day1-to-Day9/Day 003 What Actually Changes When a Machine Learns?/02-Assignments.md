Excellent. Today's assignment introduces another fundamental idea in Machine Learning: **the algorithm remains the same, but its internal parameters (settings) change during training**. Here are my reference answers.

---

# Phase 2 — Machine Learning Foundations

# Day 003 Assignment

---

# Part A — Everyday Analogies

## 1. Camera

### What is the system?

A digital camera used for taking photos.

### What are its "internal settings"?

Focus, ISO, shutter speed, aperture, and exposure.

### What happens when those settings change?

The same camera can capture brighter, sharper, darker, or blurrier images depending on the settings.

### How is this similar to Machine Learning?

The camera hardware and software remain the same, but changing its settings changes the output. Similarly, an ML algorithm stays the same while its learned parameters change to improve predictions.

---

## 2. Air Conditioner

### What is the system?

An air conditioner.

### What are its "internal settings"?

Target temperature, fan speed, operating mode (cool, dry, auto), and airflow.

### What happens when those settings change?

The AC behaves differently while the machine itself remains unchanged.

### How is this similar to Machine Learning?

The algorithm (AC) doesn't change. Only the internal settings are adjusted to achieve the desired result, just as an ML model adjusts its parameters during training.

---

## 3. Guitar

### What is the system?

An acoustic guitar.

### What are its "internal settings"?

String tension (tuning), action height, and tuning of each string.

### What happens when those settings change?

The guitar produces different notes and sounds even though it's the same instrument.

### How is this similar to Machine Learning?

Training is like tuning a guitar. We don't build a new guitar—we adjust it until it produces the correct output.

---

## 4. Coffee Machine

### What is the system?

An automatic coffee machine.

### What are its "internal settings"?

Coffee strength, water quantity, brewing time, and temperature.

### What happens when those settings change?

The taste and quality of the coffee change without changing the machine.

### How is this similar to Machine Learning?

The machine stays the same; only its internal configuration changes. Likewise, ML adjusts parameters to improve predictions without changing the learning algorithm itself.

---

## 5. Mobile Phone Camera

### What is the system?

A smartphone camera.

### What are its "internal settings"?

Brightness, HDR, focus, white balance, portrait mode, and exposure.

### What happens when those settings change?

The same scene can produce dramatically different photos depending on the chosen settings.

### How is this similar to Machine Learning?

The software remains the same, but different settings lead to different outputs. An ML model works similarly by adjusting learned parameters rather than rewriting its logic.

---

# Part B — Think Like an Engineer

## Q1. If the code of an ML algorithm doesn't change during training, what do you think is changing?

The algorithm itself remains fixed, but its internal parameters or learned values are continuously updated. These parameters capture patterns from the training data, allowing the model to improve its predictions over time.

---

## Q2. Why do we call training a "process" instead of a one-time event?

Learning doesn't happen instantly. The model repeatedly makes predictions, measures its mistakes, adjusts its parameters, and tries again. This cycle continues until the predictions become increasingly accurate. Because improvement happens gradually through many iterations, training is a process rather than a single event.

---

## Q3. What is the difference between an algorithm and a trained model, based on today's discussion?

An **algorithm** is the learning procedure or method that defines *how* learning happens. It provides the rules for updating the model.

A **trained model** is the result of applying that algorithm to data. It contains the learned parameters that represent the patterns discovered during training.

In simple terms:

* **Algorithm = Learning method**
* **Model = Learned knowledge**

---

## Q4. Suppose a machine makes a wrong prediction. Why is repeatedly adjusting its internal settings better than rewriting the entire program each time?

Rewriting the entire program for every mistake would be inefficient, time-consuming, and impossible for complex real-world problems. Adjusting internal parameters allows the model to gradually improve while preserving everything it has already learned. This makes learning scalable, adaptive, and capable of handling millions of examples without requiring new code for each one.

---