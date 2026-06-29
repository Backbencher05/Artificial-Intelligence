🚀 Phase 1 → Day 002 → Session 2
# AI Development Environment & AI Engineering Workspace

Today is not about AI models.

Today is about something that many beginners skip:

Building a professional AI engineering environment.

As a backend engineer, you already know:

Bad environment
↓
Dependency conflicts
↓
Broken projects
↓
Lost productivity

The same thing happens in AI.

In fact, AI projects usually have more dependencies than backend projects.

# Session Goals

By the end of today, you should understand:

What an AI development environment is.
Why virtual environments are mandatory.
How AI projects are structured.
Package management fundamentals.
Jupyter Notebooks and why they exist.
The difference between notebooks and production code.
How professional AI engineers organize projects.


## Part 1: What Is a Development Environment?
What is it?

A development environment is:

The collection of tools, libraries, configurations, and workflows used to build software.

For AI:

OS
↓
Python
↓
Virtual Environment
↓
Libraries
↓
Editor
↓
Git
↓
Datasets
↓
Projects
Why does it exist?

Imagine:

Project A requires:

NumPy 1.26

Project B requires:

NumPy 2.0

Install both globally:

Conflict

Your project breaks.

Problem It Solves

Virtual environments isolate dependencies.

Think of them as:

Docker containers
for Python packages

Not technically identical.

But conceptually very close.

Since you're familiar with Docker:

Container
    isolates application dependencies

Virtual Environment
    isolates Python dependencies
Part 2: Why Virtual Environments Matter
Without Virtual Environment

System Python:

Python
 ├── pandas
 ├── numpy
 ├── torch
 ├── fastapi
 ├── django
 └── hundreds more

Eventually:

Version conflicts
With Virtual Environment
Project A
 └── venv

Project B
 └── venv

Project C
 └── venv

Each project has:

Own packages
Own versions
Own dependencies
Real Industry Rule

Never install project dependencies globally.

Always:

python -m venv .venv

or

uv venv

or

conda create

depending on the ecosystem.

Part 3: Package Management
What is a package?

A package is reusable code.

Example:

import pandas
import numpy
import torch

You didn't write them.

Someone else did.

Why Package Managers Exist

Imagine manually downloading:

NumPy
Pandas
Matplotlib
PyTorch

and every dependency.

Impossible at scale.

pip

Python's package manager.

Example:

pip install numpy
requirements.txt

Backend analogy:

Think of:

requirements.txt

as:

package.json

for Python.

Example:

numpy==2.0.1
pandas==2.2.2
matplotlib==3.9.0

Install everything:

pip install -r requirements.txt
Part 4: Jupyter Notebooks

This is where AI begins to feel different from backend development.

What is Jupyter?

Jupyter is an interactive environment.

Instead of:

python main.py

you execute code cell by cell.

Example

Cell 1:

x = 10

Run.

Cell 2:

x + 5

Run.

Output:

15
Why It Exists

AI work is exploratory.

Example:

You receive:

5 million rows

You don't know:

what's inside
missing values
outliers
patterns

You investigate.

Notebook workflow:

Load Data
↓
Inspect
↓
Visualize
↓
Experiment
↓
Analyze
Why Researchers Love It

Fast feedback loop.

Instead of:

run file
fix code
run file
fix code

You execute tiny pieces.

Part 5: Notebook vs Production Code

This is extremely important.

Many beginners think:

Notebook = Application

Wrong.

Notebook

Purpose:

Research
Exploration
Experimentation
Learning
Production Code

Purpose:

Reliability
Scalability
Maintainability

Example:

Research:

Notebook

Production:

FastAPI
Docker
Kubernetes
Real AI Workflow
Notebook
 ↓
Experiment
 ↓
Model
 ↓
Package
 ↓
API
 ↓
Deploy
 ↓
Production

This should feel familiar as a backend engineer.

Part 6: AI Project Structure

As projects grow:

Bad:

project/
 ├── final.py
 ├── final_final.py
 ├── final_v2.py
 ├── latest.py

We've all seen this 😄

Professional structure:

project/
│
├── data/
│
├── notebooks/
│
├── src/
│
├── models/
│
├── tests/
│
├── requirements.txt
│
└── README.md
Meaning
data/

Raw datasets.

notebooks/

Experiments.

src/

Actual code.

models/

Saved models.

Later:

.pkl
.pt
.gguf

You'll learn these.

tests/

Unit tests.

You already know this.

Part 7: AI Engineer Toolbelt

You don't need mastery yet.

Just awareness.

Core Tools
Python

Main language.

Git

Version control.

Already known.

VS Code

Primary editor.

Jupyter

Experiments.

NumPy

Mathematics.

Pandas

Data analysis.

Matplotlib

Visualization.

PyTorch

Deep learning.

FastAPI

Serving AI models.

Docker

Deployment.

Kubernetes

Scaling.

Notice something?

You already know:

Git
Docker
Kubernetes
FastAPI

This is why your transition path is strong.

Architecture Perspective

Most beginners see:

AI = Model

Engineers see:

Data
↓
Training
↓
Model
↓
API
↓
Infrastructure
↓
Monitoring

The model is only one component.

The system matters.

Connecting To Future Phases

Today's concepts connect directly to:

Phase 2

Machine Learning

Notebook
↓
Pandas
↓
Scikit-Learn
Phase 3

Deep Learning

Notebook
↓
PyTorch
↓
GPU
Phase 4

LLMs

Notebook
↓
Transformers
↓
RAG
↓
Agents
Phase 5

Production AI

FastAPI
Docker
Kubernetes
Monitoring



## Day 002 Assignment

Answer in Assignment.md

Q1

Why are virtual environments important in AI projects?

Q2

Explain the difference between:

System Python
vs
Virtual Environment
Q3

Why are Jupyter Notebooks popular in AI development?

Q4

When should you use:

Notebook
vs
Production Python Code
Q5

Why is an AI model only one component of an AI system?


