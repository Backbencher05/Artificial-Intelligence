# Machine Learning

let's first now discuss ablut ML

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

# Machine Learning
Machine Learning is a journey of continuous improvement rather than a one-time action. It involves observing examples, making predictions, receiving feedback, making adjustments, and repeating this cycle. The learning comes from the entire process, not from a single step.

On Day 1, I thought Machine Learning was mainly about computers learning from data. Now I understand that it's better viewed as a learning process inspired by how humans improve through experience. It isn't about memorizing examples or writing countless rules—it's about gradually improving through observation, feedback, thoughtful adjustments, and repetition.

Today, I connected all the previous lessons into one complete learning loop. I now see learning as a continuous cycle of attempting, observing, improving, and repeating until the goal is achieved, rather than as a single event.

# One Sentence That Changed My Thinking

> **Learning is not a single event—it's a continuous loop of trying, receiving feedback, making thoughtful improvements, and repeating until the goal is achieved.**

## 🎉 Milestone Reached

Congratulations.

You've completed the **Foundations of Learning** section of Phase 2.

If I had to summarize these nine days in one sentence, it would be:

> **Machine Learning is the engineering discipline of building systems that improve through experience using a structured feedback loop.**

That isn't a textbook definition.

It's a definition **you've earned** through reasoning.

And that makes all the difference.
