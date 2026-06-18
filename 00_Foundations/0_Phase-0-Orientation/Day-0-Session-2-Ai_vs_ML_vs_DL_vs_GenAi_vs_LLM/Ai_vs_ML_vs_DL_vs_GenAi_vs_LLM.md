## Today's Big Goal

By the end of Session 2, you should be able to confidently explain:

- What is AI?
- What is ML?
- What is Deep Learning?
- What is Generative AI?
- What is an LLM?

And most importantly:

How are they related?

Think of It Like a Family Tree

Most beginners see these words:

AI
ML
Deep Learning
GenAI
LLM

and think they are separate things.

They are not.

They are nested inside each other.

Artificial Intelligence
│
└── Machine Learning
     │
     └── Deep Learning
          │
          └── Generative AI
               │
               └── LLMs

Let's understand each layer.

# 1. Artificial Intelligence (AI)

AI is the biggest umbrella.

Definition:

AI is the field of creating machines that perform tasks requiring human-like intelligence.

Examples:

Chess AI
Face recognition
Self-driving cars
ChatGPT
Recommendation systems

Notice:

AI does not say how the machine becomes intelligent.

It only defines the goal.

Problem With Early AI

Initially people wrote rules manually.

Example:

IF fever > 100
THEN sick
IF customer spends > 10000
THEN premium customer

This worked for simple problems.

But reality is messy.

You cannot write millions of rules.

So a better approach was needed.

# 2. Machine Learning (ML)

Machine Learning is a subset of AI.

Definition:

Instead of programming every rule, we allow the machine to learn patterns from data.

Traditional Programming:

Rules + Data
      ↓
Answer

Machine Learning:

Data + Answers
      ↓
Learns Rules

Example:

Spam Detection.

Instead of manually writing:

IF email contains "free money"
THEN spam

We give:

thousands of spam emails
thousands of normal emails

The model learns patterns itself.

Key Insight

AI says:

Build intelligent systems.

ML says:

Use data to learn intelligence.

# 3. Deep Learning

Machine Learning worked well.

But it struggled with:

images
speech
language
complex patterns

So researchers built neural networks inspired loosely by the brain.

This became:

Deep Learning

Deep Learning = Machine Learning using large neural networks.

Examples:

Face recognition
Speech recognition
Image generation
Language understanding

Most modern AI breakthroughs come from Deep Learning.

Why "Deep"?

Because the neural network contains many layers.

Conceptually:

Input
 ↓
Layer 1
 ↓
Layer 2
 ↓
Layer 3
 ↓
Layer 4
 ↓
Output

More layers → deeper network.

Hence:

Deep Learning.

# 4. Generative AI

Until recently, most AI systems only predicted or classified.

Examples:

Is this email spam?
Is this a cat or dog?
Will customer churn?

Then came a new goal:

Can AI CREATE something new?

This created:

Generative AI

Generative AI generates:

text
images
videos
music
code
speech

Examples:

ChatGPT
Image generation
Video generation
AI coding assistants
Key Difference

Traditional ML:

Predict
Classify
Recommend

Generative AI:

Create
Generate
Produce

# 5. LLMs

Inside Generative AI we have:

Large Language Models

LLMs generate language.

Examples:

OpenAI models
Anthropic models
Google Gemini models

An LLM is trained on enormous amounts of text.

Its core task is surprisingly simple:

Predict the next token.

Example:

The capital of France is _____

Model predicts:

Paris

Scale that prediction to trillions of examples and you get systems that appear conversational and intelligent.

# The Complete Picture
AI
│
├── Goal:
│   Build intelligent systems
│
└── ML
    │
    ├── Learns from data
    │
    └── Deep Learning
        │
        ├── Neural networks
        │
        └── Generative AI
            │
            ├── Creates content
            │
            └── LLMs
                │
                ├── Generate text
                ├── Answer questions
                ├── Write code
                └── Power chatbots

What Matters For You?

As a backend engineer, your future focus will be:

ML Foundations
      ↓
Deep Learning Basics
      ↓
     LLMs
      ↓
     RAG
      ↓
     Agents
      ↓
AI Backend Systems
      ↓
  AI Products

You do not need to become an ML researcher.

You need enough ML and Deep Learning knowledge to understand what happens under the hood, then you'll spend most of your time building AI systems.


# Session 2 Assignment

Add this to Assignment.md and answer in your own words:

Question 1

What is the relationship between:

AI → ML → Deep Learning → Generative AI → LLMs?

Question 2

Why was Machine Learning created?

Question 3

Why was Deep Learning needed if ML already existed?

Question 4

What is the biggest difference between traditional ML and Generative AI?

Question 5

Where does ChatGPT fit in the hierarchy?