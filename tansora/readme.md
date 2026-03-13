

# 📘 Tensors in Machine Learning

A beginner friendly guide to understanding **tensors, arrays, matrices, tensor shape, rank, dimension, and how tensors work inside neural networks**.

---

# 1. What is a Tensor?

A **Tensor** is a **container used to store numbers in multiple dimensions**.

You can think of it like a **box that holds structured numerical data**.

In Machine Learning, tensors store things like:

• training data
• images
• text embeddings
• neural network weights
• gradients

### Simple Definition

A **Tensor is a multi dimensional data structure used in machine learning to store and process numerical data.**

---

# 2. Basic Building Blocks

Before understanding tensors, we start with simpler structures.

---

# 2.1 Scalar (0D Tensor)

A **scalar** is just **one number**.

Example

5

Dimension

0

Think of it as **one value stored in a box**.

---

# 2.2 Vector (1D Tensor)

A **vector** is a **list of numbers**.

Example

2   5   7   9

Dimension

1

Vectors are commonly used for

• features
• embeddings
• coordinates

---

# 2.3 Matrix (2D Tensor)

A **matrix** is a **table of numbers**.

Example

1 2 3
4 5 6

Dimensions

Rows × Columns

Matrices are widely used in

• neural networks
• datasets
• transformations

---

# 2.4 Tensor (3D or Higher)

When data has **more than two dimensions**, it becomes a **tensor**.

Example (3D)

Matrix 1

1 2 3
4 5 6

Matrix 2

7 8 9
10 11 12

You can imagine it as **a stack of matrices**.

---

# 3. Real Machine Learning Example

## Image as Tensor

An image is stored as a tensor.

Example image properties

Height = 224
Width = 224
Channels = 3

Tensor shape

(224, 224, 3)

Channels represent

R = Red
G = Green
B = Blue

Each pixel contains **three numbers representing color intensity**.

Example pixel

[255, 120, 60]

---

# 4. Batch of Images

Neural networks usually process **multiple images together**.

Example

Batch size = 32

Tensor shape

(32, 224, 224, 3)

Meaning

32 → number of images
224 → image height
224 → image width
3 → color channels

---

# 5. Tensor vs Array vs Matrix

Array
A general container that stores elements in one or more dimensions.

Matrix
A **two dimensional structured table of numbers**.

Tensor
A **generalization of vectors and matrices to higher dimensions**.

Example hierarchy

Scalar → 0D tensor
Vector → 1D tensor
Matrix → 2D tensor
Tensor → 3D or higher dimensional data

Important interview statement:

**A tensor is a generalization of scalars, vectors, and matrices to higher dimensions.**

---

# 6. Tensor Shape

**Shape describes the size of each dimension of a tensor.**

Example

(3, 4)

Meaning

3 rows
4 columns

Example for images

(32, 224, 224, 3)

Meaning

32 images
224 height
224 width
3 color channels

---

# 7. Tensor Rank

**Rank means the number of dimensions in a tensor.**

Examples

Scalar → Rank 0
Vector → Rank 1
Matrix → Rank 2
Image tensor → Rank 3
Batch of images → Rank 4

Example

Shape (32, 224, 224, 3)

Rank = 4

---

# 8. Tensor Dimension

Dimension refers to the **size along each axis**.

Example

Tensor shape

(3, 4)

Dimensions

3
4

Example

(32, 224, 224, 3)

Dimensions

32
224
224
3

---

# 9. Why Tensors Are Important

Machine learning frameworks rely on tensors because they enable

• fast mathematical computation
• parallel processing
• GPU acceleration
• efficient deep learning operations

Popular frameworks that use tensors include **PyTorch** and **TensorFlow**.

---

# 10. How Tensors Work Inside Neural Networks

Neural networks perform **all operations using tensors**.

---

## Input Data

Data enters the neural network as tensors.

Example

Image tensor
(224, 224, 3)

---

## Weights

The weights of neurons are stored as **weight tensors**.

These tensors connect input features to neurons.

---

## Forward Pass

During the forward pass, the neural network performs mathematical operations between tensors.

Input tensor → multiplied with weight tensor → produces output tensor.

---

## Activation Functions

Activation functions transform each element of the output tensor.

Examples

ReLU
Sigmoid
Softmax

---

## Backpropagation

During training, the model calculates **gradient tensors**.

These gradients update the weight tensors to reduce prediction error.

---

# 11. Neural Network Data Flow

Input Tensor
↓
Weight Tensor
↓
Mathematical Operations
↓
Activation Function
↓
Output Tensor

---

# 12. Simple Analogy

Think of tensors like containers of numbers.

Scalar
↓
Vector
↓
Matrix
↓
Tensor

Visual idea

Tensor

Matrix
Matrix
Matrix

---

# 13. Interview One Line Answer

A **tensor is a multi dimensional numerical data structure used in machine learning to represent data such as images, features, and neural network parameters.**


