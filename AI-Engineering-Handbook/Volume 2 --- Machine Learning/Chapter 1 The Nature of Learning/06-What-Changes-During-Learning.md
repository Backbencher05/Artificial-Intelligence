I'm genuinely enjoying writing this handbook with you.

This doesn't feel like we're summarizing lessons anymore.

It feels like we're writing the book that **we wished existed when we started learning Machine Learning**.

And now...

We arrive at the first question that almost every beginner asks:

> **"If the program doesn't rewrite itself... what actually changes when a machine learns?"**

Let's answer it from first principles.

# Section 4 — What Changes During Learning?

## If the Program Doesn't Change, What Does?

One of the most common misunderstandings about Machine Learning is believing that a computer somehow rewrites its own program while learning.

This idea is understandable.

After all, if we say that a machine "learns," it is natural to imagine that its code must also change.

Surprisingly, that is not what happens.

To understand Machine Learning, we must first distinguish between three different ideas:

* The **algorithm**
* The **model**
* The **learned parameters**

Understanding the difference between these three concepts removes much of the mystery surrounding Machine Learning.

---

## The Learning Algorithm

Imagine a teacher teaching mathematics.

Every year, new students enter the classroom.

The teacher follows the same teaching process.

The explanation may be adjusted slightly, but the teaching method itself remains largely the same.

The students change.

The teacher's teaching process does not.

A Machine Learning algorithm behaves similarly.

The algorithm defines **how learning happens**.

It is a procedure.

It is a method.

It is a learning strategy.

Whether the algorithm is used today, tomorrow, or next year, its learning procedure remains the same.

The algorithm does not become smarter.

It simply provides the process through which learning can occur.

---

## The Model

Now imagine two students taught by the same teacher.

One has studied for one day.

The other has studied for one year.

The teaching method was identical.

Yet the knowledge stored by the students is completely different.

The student represents the learned knowledge.

In Machine Learning, this learned knowledge is called the **model**.

A model is the result of learning.

It contains the knowledge acquired from experience.

When we say,

> "Train the model,"

we are really saying,

> "Allow the learning process to build useful knowledge from experience."

---

## The Internal Parameters

Imagine tuning a guitar.

The guitar itself does not change.

The wood does not change.

The strings do not change.

What changes is the tuning of the strings.

Small adjustments gradually produce better music.

Machine Learning works in a remarkably similar way.

The learning algorithm remains the same.

The model remains the same type of model.

What changes are the model's **internal parameters**.

These parameters gradually adjust during learning until the model represents useful patterns found in the data.

At this stage, you do not need to know the mathematics behind these parameters.

Simply understand their purpose.

They are the part of the model that changes as learning takes place.

---

## A Camera Analogy

Imagine using a professional camera.

The camera body remains exactly the same.

However, you can adjust:

* Focus
* Exposure
* ISO
* Shutter speed
* White balance

The hardware has not changed.

Only the internal settings have changed.

Those settings dramatically influence the final photograph.

Machine Learning follows the same principle.

The algorithm remains fixed.

The learning process adjusts internal settings until the predictions improve.

---

## A Software Engineering Analogy

Imagine deploying a backend service.

The application architecture remains unchanged.

The APIs remain unchanged.

The database schema remains unchanged.

However, you adjust configuration values such as:

* Cache size
* Database connection pool
* Timeout values
* Thread limits

The software system is still the same application.

Yet these carefully chosen settings significantly affect performance.

Machine Learning behaves similarly.

Learning is primarily the process of adjusting internal parameters—not rewriting the entire system.

---

## The Relationship Between the Three

The easiest way to understand Machine Learning is to separate these ideas clearly.

```text id="3v8n1m"
Learning Algorithm
        │
Defines HOW learning happens
        │
        ▼
Model
        │
Stores learned knowledge
        │
        ▼
Internal Parameters
        │
Change during learning
```

Each component has a different responsibility.

Confusing them often leads to confusion later when studying Machine Learning algorithms.

---

## Why This Matters

Understanding what changes during learning prepares us for almost everything that follows.

Later, we will study:

* Linear Regression
* Decision Trees
* Neural Networks
* Support Vector Machines

These algorithms are very different from one another.

Yet they all share one important characteristic.

During training, something inside the model changes.

The learning algorithm guides that change.

The result is an improved model.

The fundamental idea remains the same regardless of the specific algorithm.

---

## Engineering Perspective

As software engineers, we often improve systems by changing configuration rather than rewriting the entire application.

Machine Learning follows the same philosophy.

Instead of rewriting the algorithm after every mistake, the learning process adjusts the model's internal parameters.

This makes learning:

* Repeatable
* Scalable
* Adaptable
* Efficient

It also explains why one algorithm can be trained on many different datasets.

The learning procedure stays the same.

The learned knowledge becomes different.

---

## Key Takeaways

* The learning algorithm defines how learning happens.
* The model represents the knowledge learned from experience.
* Internal parameters are the part of the model that change during training.
* Learning does not usually involve rewriting the algorithm.
* Different datasets produce different models because they lead to different learned parameters.

---

## 🔍 One Sentence That Changed My Thinking

> **Learning does not rewrite the algorithm; it refines the model by continuously adjusting its internal parameters based on experience.**

---

### Mentor's Reflection

I want to point out something that I deliberately did in this section.

Did you notice that I **never used the word "weights"**?

That wasn't an accident.

Back on **Day 003**, you told me something very honestly:

> *"I know the term mathematical weights, but I don't really understand it yet."*

Instead of introducing terminology early, we built the mental model first.

Now you understand that:

* Something changes.
* That "something" belongs to the model.
* Those changes are guided by the learning algorithm.

Only later, when we introduce **weights**, you'll have a place to put that idea.

You won't memorize the term.

You'll recognize it as **one specific kind of internal parameter**.

That's the difference between building understanding and collecting vocabulary.

And that's exactly how we're going to continue through the rest of this handbook. 🚀
