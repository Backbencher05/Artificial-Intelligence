Excellent.

Today is the day where Phase 2 starts becoming **real**.

Until now, we've talked about:

* Why ML exists
* Learning vs memorization
* Patterns
* Generalization

Today we'll ask the question that every ML engineer should be able to answer.

---

# Phase 2 — Day 003

# What Actually Changes When a Machine Learns?

Again...

No code.

No algorithms.

No mathematics.

Only thinking.

---

# Step 1 — A Blank Notebook

Imagine I give you a brand-new notebook.

It's completely empty.

```
Notebook

Page 1: Blank
Page 2: Blank
Page 3: Blank
...
```

Now I start teaching you multiplication.

```
2 × 3 = 6
3 × 4 = 12
5 × 6 = 30
...
```

After one month...

Has the notebook changed?

Yes.

It now contains information.

---

Now imagine I erase the notebook.

Again it's blank.

This time, instead of writing in the notebook...

I teach **you**.

One month later...

You can solve multiplication problems.

Where is the knowledge?

Not in the notebook.

It's **inside you**.

Interesting...

---

# Step 2 — What Changed Inside You?

Think carefully.

When you learned multiplication...

Did your brain suddenly become physically larger?

No.

Did it download a multiplication app?

No.

So what changed?

---

Don't answer yet.

Let's make it even simpler.

---

# Step 3 — Learning to Ride a Bicycle

The first day.

You fall.

Again.

Again.

Again.

After one week...

You can balance.

After one month...

You ride confidently.

Now ask yourself:

What changed?

Did the bicycle change?

No.

Did gravity change?

No.

Did the road change?

No.

**You changed.**

But what exactly changed?

---

# Step 4 — The Machine Version

Imagine a machine.

Day 1:

```
Input → Wrong Answer
```

You tell it:

> Wrong.

The machine adjusts something.

Next example.

```
Input → Slightly Better Answer
```

Again:

> Wrong.

The machine adjusts something.

Next example.

```
Input → Better Answer
```

Again.

Again.

Again.

Eventually...

```
Input → Correct Prediction
```

Notice something.

The machine itself didn't become "smarter" by magic.

Something inside it was adjusted repeatedly.

---

# Step 5 — The Radio Analogy 📻

Imagine an old FM radio.

When you first turn the knob...

```
📻
~~~~~~~
Noise
~~~~~~~
```

You rotate the knob slightly.

```
📻
~~~music~~~
```

Rotate again.

```
📻
♫ Clear Music ♫
```

Did the radio become a different radio?

No.

You simply adjusted its internal setting.

Machine Learning is surprisingly similar.

A machine starts with poor internal settings.

Training is the process of **adjusting those settings** until the outputs become useful.

---

# Step 6 — Let's Build the Mental Model

Imagine this black box.

```
          Input
             │
             ▼
     ┌────────────────┐
     │                │
     │   ???          │
     │                │
     └────────────────┘
             │
             ▼
         Prediction
```

Question:

When the prediction is wrong...

Which part changes?

* The input?
* The output?
* The black box?

Obviously...

The **black box**.

---

Now imagine training happens one thousand times.

```
Input

↓

Black Box
(adjust)

↓

Prediction

↓

Feedback

↓

Adjust Again
```

Eventually...

The black box behaves differently.

---

# Here's the Important Idea

A machine **doesn't learn by adding more code**.

It learns by **changing its internal state**.

That sentence is incredibly important.

Write it down mentally.

---

# But What Is This "Internal State"?

This is where most books immediately jump to:

> Weights.

Parameters.

Coefficients.

Biases.

Neurons.

Matrices.

Not us.

Instead...

Let's call it something simpler.

> **Internal Settings**

That's all.

Imagine every machine has thousands...

Sometimes millions...

Sometimes billions...

Of tiny adjustable settings.

Training simply means:

> Find better settings.

That's it.

Everything else we'll study later is built on this idea.

---

# Engineering Perspective

Think about something you've already worked with: a backend service.

Suppose your service has a configuration file:

```yaml
max_connections: 100
timeout: 30
cache_enabled: true
```

If the system performs poorly, you might tune these settings:

* Increase the timeout.
* Adjust the cache.
* Change connection limits.

The **code** hasn't changed, but the **behavior** has.

Machine Learning is similar in spirit.

The algorithm (the code) defines **how learning happens**.

The learned settings determine **how the trained model behaves**.

This distinction is fundamental:

* **Algorithm** → the learning procedure.
* **Model** → the result after those internal settings have been adjusted.

We'll revisit this distinction many times.

---

# A Small Thought Experiment

Imagine two machines.

### Machine A

Has **10 settings**.

### Machine B

Has **10 billion settings**.

Which one can learn more complex patterns?

At first glance, you might say Machine B.

But...

Does having more settings automatically mean better learning?

Or could it introduce new challenges?

Don't answer yet.

That's another seed we're planting.

---

# Today's Goal

Don't remember terms.

Remember this idea:

> **Learning is the process of changing internal settings so that future predictions become better.**

Not perfect.

Better.

One adjustment at a time.

---

# Your Assignment

## Part A — Everyday Analogies

Think of **5 real-world systems** whose behavior changes because of adjusting internal settings rather than changing the whole system.

For each one, answer:

1. What is the system?
2. What are its "internal settings"?
3. What happens when those settings change?
4. How is this similar to Machine Learning?

Examples could include:

* Camera
* Guitar
* Car engine
* Air conditioner
* Game difficulty
* Coffee machine
* Phone settings

Try to come up with your own examples.

---

## Part B — Think Like an Engineer

Answer these questions in your own words:

1. If the code of an ML algorithm doesn't change during training, what do you think is changing?
2. Why do we call training a "process" instead of a one-time event?
3. What is the difference between an **algorithm** and a **trained model**, based on today's discussion?
4. Suppose a machine makes a wrong prediction. Why is repeatedly adjusting its internal settings better than rewriting the entire program each time?

---

## Engineering Checkpoint

Reflect on:

1. What new mental model did I build today?
2. What misconception did I correct today?
3. What question is still confusing me?
4. If I had to teach today's lesson in 2 minutes, what would I say?

---

## Before You Go

I want to leave you with one question that I don't want you to answer immediately.

Imagine I give two machines the **same data** and the **same algorithm**.

One learns well.

The other learns poorly.

**Why might that happen?**

If the data is the same...
If the algorithm is the same...

What else could be different?

We'll explore that mystery next, and it will naturally lead us into one of the most important concepts in Machine Learning.


# Answer Feedback and next

😂 Good catch.

You're absolutely right.

I got carried away by our discussion about honesty and learning, and I skipped the **Day 003 review**.

This is another reason I like our mentorship style—you keep me accountable too. 😄

So let's do the review properly.

---

# Phase 2 — Day 003 Review

## Overall Assessment

**Score (for understanding): 9.5/10**

Not because every statement is technically perfect.

But because your **mental model is becoming stronger.**

You're beginning to separate:

* Algorithm
* Training
* Model
* Parameters

You don't fully understand all of them yet, but you no longer think they're the same thing.

That is huge progress.

---

# Our Honesty Review

## 🟢 What you genuinely understand

I believe you genuinely understand these ideas.

### ✅ Learning is adjustment

You wrote:

> "Training is essentially a process of fine-tuning these parameters."

Even though you don't yet know what "parameters" are internally...

You understand that **something is repeatedly adjusted.**

That's the important idea.

---

### ✅ Algorithm vs Model

You wrote:

> Algorithm = Learning Method

> Model = Learned Knowledge

Excellent.

This is one of those simple statements that will remain true throughout your ML journey.

Later we'll refine it further, but today it's exactly the right abstraction.

---

### ✅ Training is iterative

You wrote:

> Prediction → Mistake → Adjust → Repeat

Perfect.

This is one of the biggest mental models in ML.

Almost every learning algorithm follows some variation of this loop.

---

# 🟡 Things you've heard before but don't fully understand

This is where your honesty really helped.

---

## Mathematical Weights 🟡

You used the term.

Then you told me:

> "I've heard it in tutorials."

Perfect.

That means we keep it here:

```text
Weights 🟡

Known vocabulary

Unknown mechanism
```

Exactly where it belongs.

---

## Learned Parameters 🟡

Same thing.

You know they're important.

You don't yet know:

* What they look like.
* Why they're numbers.
* Who changes them.
* How they're updated.

We'll build this naturally.

---

# 🔴 Things we haven't learned yet

Your question:

> Are they numbers?

🔴

Excellent.

We'll answer it.

---

> Are they probabilities?

🔴

Sometimes.

Depends on the algorithm.

We'll see.

---

> Are they weights?

🔴

For many models, yes.

Not all.

We'll learn why.

---

# Review of Part A (Analogies)

I loved these.

Let's analyze them one by one.

---

## 📷 Camera

Excellent.

One improvement.

You wrote:

> Camera settings change the image.

True.

But think one level deeper.

Why do photographers spend years learning camera settings?

Because different environments require different settings.

That's exactly like ML.

Different datasets require different learned parameters.

Wonderful analogy.

---

## ❄️ Air Conditioner

Very good.

The system remains identical.

Behavior changes.

Exactly the idea we wanted.

---

## 🎸 Guitar

This is my favorite.

Why?

Because tuning is gradual.

Nobody tunes a guitar by jumping directly to the perfect sound.

You tighten.

Listen.

Adjust.

Listen.

Adjust.

That process is remarkably similar to how many ML algorithms improve a model.

We'll revisit this analogy when we study optimization.

---

## ☕

Coffee Machine

Nice.

One small refinement.

The coffee machine analogy is stronger if you imagine trying different settings repeatedly until the coffee tastes right.

Again...

Prediction.

Feedback.

Adjustment.

Repeat.

Notice how that mirrors training.

---

## 📱 Mobile Camera

Excellent.

One camera.

Different internal settings.

Different outputs.

Exactly what we wanted.

---

# Review of Part B

---

## Q1

> The algorithm remains fixed.

Excellent.

You now clearly distinguish:

Algorithm ≠ Model.

That's progress.

---

## Q2

This was one of your best answers.

You naturally described an iterative loop.

Prediction

↓

Mistake

↓

Adjustment

↓

Repeat

Without knowing it...

You've already described the skeleton of **Gradient Descent**.

Don't worry about the name yet.

The mental model comes first.

---

## Q3

Beautiful.

Especially this:

> Model = Learned Knowledge

I actually prefer this over saying:

> Model = Mathematical Function

Because "learned knowledge" captures the purpose.

Later, we'll add the mathematical details.

---

## Q4

Excellent engineering thinking.

You focused on scalability.

Exactly right.

Imagine rewriting code after every email classified as spam.

Impossible.

Adjusting parameters scales.

Rewriting code doesn't.

---

# Engineering Checkpoint

Now my favorite section.

---

## 1. New Mental Model

Perfect.

One tiny refinement.

Instead of saying:

> "Machine Learning adjusts parameters."

I'd say:

> "Machine Learning **learns by adjusting** parameters."

That wording emphasizes that adjustment is the learning mechanism, not just something that happens alongside learning.

---

## 2. Misconception

Very common misconception.

You thought:

Training changes code.

Now you know:

Training changes learned settings.

That's a major conceptual milestone.

---

## 3. Remaining Question

This...

is now becoming our central thread.

You asked:

> What exactly are these parameters?

Good.

Notice something.

The same question has appeared three days in a row.

Day 1

↓

What is stored?

Day 2

↓

What is learning?

Day 3

↓

What are parameters?

This is not repetition.

This is **progressive refinement**.

You're narrowing the question.

That's exactly how engineers investigate complex systems.

---

## 4. Teaching in 2 Minutes

Excellent.

I especially liked:

> "Training isn't about rewriting the program—it's about tuning the model."

That sentence deserves to stay in your long-term memory.

---

# One Thing I'd Like You to Improve

This is not criticism.

It's the next step in your growth.

Currently your answers often end with:

> "This is similar to Machine Learning because..."

I want you to begin adding one extra sentence:

> **Why is this analogy limited?**

For example:

### Guitar

Similarity:

* Tuning changes behavior.

Limitation:

* A guitar doesn't automatically retune itself based on feedback, whereas an ML model adjusts its settings during training.

Every analogy has limits.

Understanding those limits deepens your understanding of the real concept.

---

# Mentor's Observation

Do you know what I'm happiest about?

It's not your answers.

It's your questions.

Three days ago, you asked:

> "What is stored?"

Today you're asking:

> "What exactly are those stored things?"

That means your brain isn't collecting isolated facts. It's building a connected model, where each answer naturally leads to a better question.

That's a strong sign that you're learning from first principles rather than memorizing terminology.

---

# Day 003 Status

* ✅ Concept: Completed
* ✅ Assignment: Completed
* ✅ Review: Completed (this time 😄)
* ✅ Engineering Checkpoint: Completed
* 🧠 Key takeaway: **A machine learns by repeatedly adjusting its internal settings; the algorithm defines *how* those adjustments happen, and the trained model is the result of those adjustments.**

Now we're truly ready to move on to **Day 004**. I have a feeling you're going to enjoy it, because we're finally going to start opening the "black box" instead of just talking about it from the outside.
