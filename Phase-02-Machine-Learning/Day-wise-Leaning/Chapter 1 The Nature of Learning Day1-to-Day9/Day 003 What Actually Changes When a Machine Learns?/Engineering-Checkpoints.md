

# Engineering Checkpoint

## 1. What new mental model did I build today?

Today, I realized that Machine Learning doesn't learn by changing its program. Instead, it learns by repeatedly adjusting internal parameters while the learning algorithm itself remains unchanged. Learning is essentially a process of fine-tuning these parameters to better represent patterns in the data.

---

## 2. What misconception did I correct today?

I previously assumed that training somehow rewrote the program or created new logic. Today, I understood that the program (algorithm) stays the same throughout training. What changes are the internal parameters that the algorithm adjusts based on the data.

---

## 3. What question is still confusing me?

What exactly are these internal parameters? Are they just numbers, mathematical weights, probabilities, or something more complex? I'd like to understand what a trained model physically stores after learning.

---

## 4. If I had to teach today's lesson in 2 minutes, what would I say?

Imagine buying a new guitar.

The guitar itself doesn't become better by replacing its wood or redesigning it every time you play. Instead, you tune its strings until each one produces the correct note.

The guitar remains the same; only its tuning changes.

Machine Learning works in a similar way.

The learning algorithm is like the guitar—it stays the same throughout training. What changes are the model's internal settings. After each prediction, the algorithm checks how wrong it was, slightly adjusts those settings, and tries again. Over many repetitions, those adjustments help the model produce better predictions.

Training isn't about rewriting the program—it's about tuning the model until it captures the patterns hidden in the data.

---

# Looking Ahead

Today's puzzle is an important one:

> Two machines receive:
>
> * The same data
> * The same learning algorithm
>
> Yet one learns well, while the other performs poorly.

If both the **data** and the **algorithm** are identical, something else must influence the learning process.

That "something else" will lead us to one of the most important ideas in Machine Learning: **hyperparameters**—the settings that control *how* learning happens, rather than *what* the model learns.

Understanding the distinction between **parameters** (learned by the model) and **hyperparameters** (chosen by the engineer) is a key milestone in becoming an ML engineer.
