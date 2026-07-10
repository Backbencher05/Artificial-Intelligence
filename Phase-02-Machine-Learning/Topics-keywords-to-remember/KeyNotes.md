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