
# Day 001 Today's Engineering Vocabulary

### 1. Reality

* **What is it?** The actual world as it exists, independent of a computer.
* **Why does it exist?** It is the source of everything we want to understand or predict.
* **Where does it fit in the learning loop?** It is the starting point.
* **When will we use it?** Always—every ML problem begins with some aspect of reality.

### 2. Representation

* **What is it?** A machine-processable form of reality (such as numbers, pixels, text, or structured records).
* **Why does it exist?** Because computers cannot work directly with real-world experiences.
* **Where does it fit in the learning loop?** Immediately after reality and before observation.
* **When will we use it?** Throughout Machine Learning; every dataset is a representation.

### 3. Observation

* **What is it?** The information available to the learning system after reality has been represented.
* **Why does it exist?** A machine can only learn from what it can observe.
* **Where does it fit in the learning loop?** After representation and before learning.
* **When will we use it?** Every time we collect data for training or prediction.

--------------------------------------------------------------------------------------------------------------------------------------



# Day 002 Today's Engineering Vocabulary

## 1. Information

* **What is it?** Facts or measurements describing some aspect of reality.
* **Why does it exist?** To represent reality in a form that can be stored, processed, or communicated.
* **Where does it fit in the learning loop?** It makes up the representation that the machine observes.
* **When will we use it?** Every ML dataset is built from information collected about the problem.

---

## 2. Relevance

* **What is it?** The degree to which a piece of information helps solve a specific problem.
* **Why does it exist?** Because not all information contributes equally to every task.
* **Where does it fit in the learning loop?** Between representation and learning, guiding what is most useful.
* **When will we use it?** When deciding what information to collect and later when building better ML models.

---

## 3. Prediction Task

* **What is it?** The specific question we want the machine to answer.
* **Why does it exist?** Without a clear goal, we cannot judge whether information is useful.
* **Where does it fit in the learning loop?** It defines the purpose of learning and determines what information matters.
* **When will we use it?** Throughout Machine Learning—from spam detection to price prediction to image recognition.

----------------------------------------------------------------------------------------------------------------------------------------


# Day 003 Today's Engineering Vocabulary

### 1. Example

* **What is it?** A single observation or instance of reality represented as data.
* **Why does it exist?** Because learning begins with observing individual cases.
* **Where does it fit in the learning loop?** After representation and before discovering patterns.
* **When will we use it?** Every ML problem is built from many examples.

---

### 2. Variation

* **What is it?** The natural differences that exist among examples of the same concept.
* **Why does it exist?** Reality is diverse; no two situations are exactly the same.
* **Where does it fit in the learning loop?** Variation is what allows a learner to separate essential characteristics from accidental ones.
* **When will we use it?** Throughout Machine Learning, especially when discussing data quality and model generalization.

---

### 3. Pattern

* **What is it?** A relationship or regularity that appears across many examples.
* **Why does it exist?** Learning is the process of discovering these recurring relationships.
* **Where does it fit in the learning loop?** It emerges after observing many examples and drives prediction.
* **When will we use it?** This idea will become the foundation of every ML algorithm we study.

---------------------------------------------------------------------------------------------------------------------------------------------

# Day 004 Today's Engineering Vocabulary

## 1. Example

* **What is it?** One observation or one instance of reality represented as data.
* **Why does it exist?** Because learning starts by observing individual cases.
* **Where does it fit in the learning loop?** It is the basic building block of learning.
* **When will we use it?** Every row in a dataset is an example.

---

## 2. Organization

* **What is it?** Arranging information into a structured form that makes analysis and learning possible.
* **Why does it exist?** Raw information is difficult to interpret; organization reveals relationships.
* **Where does it fit in the learning loop?** After collecting many examples and before learning begins.
* **When will we use it?** Whenever we prepare data for analysis or training.

---

## 3. Dataset *(Our First Official ML Term)*

* **What is it?** A well-organized collection of many examples that a machine can learn from.
* **Why does it exist?** Because learning requires both sufficient examples and a consistent structure.
* **Where does it fit in the learning loop?** It is the bridge between collecting experiences and discovering patterns.
* **When will we use it?** In every Machine Learning project—from predicting house prices to recognizing handwritten digits.
---------------------------------------------------------------------------------------------------------------------------------------------


# Day005 Today's Engineering Vocabulary

### 1. Feature

* **What is it?** A piece of information that describes an example and helps the machine make a prediction.
* **Why does it exist?** Because the machine needs observations to reason about an outcome.
* **Where does it fit?** Inside each row of a dataset, alongside other descriptive information.
* **When will we use it?** Every time we build or train a Machine Learning model.

---

### 2. Label (Target)

* **What is it?** The outcome or answer the machine is trying to learn or predict.
* **Why does it exist?** Because learning needs a goal; without an outcome, the machine has nothing to compare its predictions against.
* **Where does it fit?** Alongside the features in the dataset, but with a different responsibility.
* **When will we use it?** In supervised learning problems, where examples include the correct answer.
