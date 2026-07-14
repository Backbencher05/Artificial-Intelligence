# Machine Learning

- Learning means becoming capable of making good decisions about situations you've never seen before.
---------------------

- A machine doesn't learn by adding more code.
  It learns by changing its internal state.

Think about something you've already worked with: a backend service.

- Suppose your service has a configuration file:

    - max_connections: 100
    - timeout: 30
    - cache_enabled: true

If the system performs poorly, you might tune these settings:

    - Increase the timeout.
    - Adjust the cache.
    - Change connection limits.

- The code hasn't changed, but the behavior has.
  Machine Learning is similar in spirit.

- The algorithm (the code) defines how learning happens.
- The learned settings determine how the trained model behaves.

# This distinction is fundamental:

- Algorithm → the learning procedure.
- Model → the result after those internal settings have been adjusted.

We'll revisit this distinction many times.
- Training simply means: Find better settings.

# Learning: 
- Learning is the process of changing internal settings so that future predictions become better.

# Model: 
- Note: That's a first-principles definition. We'll refine it as we learn more.
- A model is an internal representation of reality that has been learned from data and is useful for making predictions or decisions.
- A model is simply a simplified representation of reality created for a specific purpose.

- A machine cannot improve unless it receives meaningful feedback about how wrong its predictions are.

# The Big Idea

Learning isn't just about knowing:

- "I was wrong."

It's about answering two questions:

- What should I change?
- How much should I change it?

Every learning system—human or machine—must solve these two problems.

❌ Don't memorize

"The algorithm updates the parameters."

That's only a statement.

✅ Instead, ask yourself:

Whenever you see a model making a mistake, ask:

Which part of the model should change?
How much should it change?
Why not change everything?

Those three questions are the foundation of optimization in ML.
# So
- Learning requires deciding what to change and how much to change after every mistake.
- Key Takeaway: Learning isn't about changing everything after a mistake. It's about identifying the responsible parts, making careful adjustments, observing the results, and repeating the process.