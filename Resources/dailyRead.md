Large Language Models

LLMs generate language.

Examples:

OpenAI models
Anthropic models
Google Gemini models
CUDA (Compute Unified Device Architecture)
GPU kernels

# Community and Open Source

Most AI breakthroughs release Python implementations.

Examples:

Transformers → Hugging Face
PyTorch ecosystem
OpenAI SDK
LangChain
LlamaIndex


-----------------------------------------------------------------------
Q3. Explain Vector vs Matrix vs Tensor in your own words.
Vector

A vector is a single list of numbers arranged in one dimension.

Example:

[10, 20, 30]

You can think of it as a single row or column of values.

Examples:

User features
Word embeddings
Sensor readings
Matrix

A matrix is a collection of vectors arranged in rows and columns.

Example:

1  2  3
4  5  6

Matrices are commonly used to represent:

Datasets
Images
Neural network weights
Tensor

A tensor is a generalization of vectors and matrices into higher dimensions.

Examples:

Vector  = 1 Dimension
Matrix  = 2 Dimensions
Tensor  = 3+ Dimensions

Examples in AI:

RGB Images → Height × Width × Channels
Video Data → Frames × Height × Width × Channels
Deep Learning Batches → Batch × Features
Simple Understanding
Scalar → Single Number

Vector → List of Numbers

Matrix → Table of Numbers

Tensor → Collection of Tables in Higher Dimensions


Q4. What is vectorization? Why is it important in AI systems?
What is Vectorization?

Vectorization means performing an operation on an entire array or matrix at once instead of processing each element individually using loops.

Instead of:

result = []

for x in numbers:
    result.append(x * 2)

We can write:

result = numbers * 2

NumPy executes this internally using optimized low-level code.

Why is it Important in AI?

AI systems perform enormous numbers of calculations.

Examples:

Matrix multiplication
Neural network computations
Image processing
Embedding generation

If every operation used Python loops:

Very Slow
High CPU Usage
Poor Scalability

Vectorization allows:

Faster execution
Better CPU utilization
GPU acceleration
Efficient handling of large datasets

Without vectorization, modern AI training would be impractical. 



## --------------------

# A huge milestone happened today.

For the first time, you can understand a real AI equation:

output = X @ W + b

A week ago this might have looked mysterious.

Now you can identify:

X → Input Data

W → Learned Weights

b → Bias

@ → Matrix Multiplication

+ → Broadcasting

This single equation sits at the heart of:



---------------------------------------------------------

Row represents one observation (customer)
Column represents one feature (Age, Salary, Department)

Q3. Explain the difference between Row vs Column from an AI perspective.
Row

A row represents one complete observation or one data sample.

Example:

CustomerID	Age	Salary	Department
101	25	50000	IT

This single row describes one customer.

In AI:

One Row = One Training Example

Each row is one input that the model learns from.

Column

A column represents one feature or attribute shared by all observations.

Example:

Age

contains the age of every customer.

Similarly:

Salary

contains the salary of every customer.

In AI:

One Column = One Feature

Features are the inputs used by machine learning models to make predictions.

AI Perspective

Suppose we want to predict salary.

Rows:

Customer 1
Customer 2
Customer 3
...

Columns:

Age
Experience
Education
Department

# The model learns patterns across columns using every row as a training example.

Summary
Row	            Column
One observation	One feature
One customer	Age
One house	    Price
One email	    Spam label
One training sample	One model input feature




# Final Cleaning Workflow

Load Dataset
        ↓
Inspect (head, info, shape)
        ↓
Handle Missing Values
        ↓
Detect & Fix Invalid Values
        ↓
Remove Duplicates
        ↓
Verify Data Types
        ↓
Validate Final Dataset
        ↓
Ready for Feature Engineering and Model Training