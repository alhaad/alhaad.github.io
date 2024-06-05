---
layout: post
title: "Multi-layer perceptron (MLP) is a universal classifier"
tag: MLP universal classifier
---

<html>
  <head>
    <script type="text/x-mathjax-config">
      MathJax.Hub.Config({
      TeX: { equationNumbers: { autoNumber: "AMS" } }
      });
    </script>
    <script type="text/javascript" async src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
  </script>
</head>
<body>

Notes from CMU 11-785. Lecture #1

## Perceptron is a linear classifier
A single perceptron (or neuron) acts as a linear classifier. `W` are weights, `X` is the input vector, `b` is the bias and `f` is the activation function - step function for binary classification.
$$
Y = f(W^T X + b)
$$

In two dimensions it will represent a line.
$$
\begin{bmatrix} y \\ \end{bmatrix} = \begin{bmatrix} w1 & w2 \\ \end{bmatrix} \begin{bmatrix} x1 \\ x2 \end{bmatrix} + \begin{bmatrix} b \end{bmatrix}
$$

## Logic AND is a linear classification problem
There exists atleast one linear decision boudnary that can separate the two outputs (0 and 1). An example is 
$$
f(x1 + x2 - 1.5)
$$

| x1 | x2 | x1 + x2 - 1.5 | f(x1 + x2 - 1.5) |
|----|----|---------------|------------------|
| 0  | 0  | -1.5          | 0                |
| 0  | 1  | -0.5          | 0                |
| 1  | 0  | -0.5          | 0                |
| 1  | 1  | 0.5           | 1                |

Here is a way to visualize
```plaintext

   y
   |
 1 +        (1,1)
   |        
   |        
 0 +   (0,0)      (0,1)
   |        (1,0)
   +----------------------> x
        0       1
```
Tangentially, individual perceptrons can act as boolean gates (e.g AND, OR), network of perceptrons are boolean functions (eg. XOR) and MLPs are universal boolean functions.

## Perceptron(s) can create an arbitrary bounding box
We can use multiple perceptrons to create an arbitrary bounding box.
Let's create a triangle. Everything within the triangle belongs to class A, everything outside is class B. 
$$
\begin{bmatrix} y1 \\ y2 \\ y3 \end{bmatrix} = \begin{bmatrix} 1 & 1 \\ 1 & -1 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} x1 \\ x2 \end{bmatrix} + \begin{bmatrix} 1 \\ 1 \\ -1 \end{bmatrix}
$$

The output of the above perceptrons can then be used by an AND layer. For examle,
```plaintext
Input Layer:       First Layer (Bounding Box):          Second Layer (AND):
(x1, x2)  ---->  [Perceptron 1: x ≥ 0.5]  ----------->  [AND Perceptron]  ----> Output
               \                                   /
                \                                 /
                 \->  [Perceptron 2: x ≤ 1.5]  -/
                 /->  [Perceptron 3: y ≥ 0.5]  -\
                /                                 \
               /                                   \
(x1, x2)  ---->  [Perceptron 4: y ≤ 1.5]  ----------->
```
A universal classifier can then be a tree of such linear classifers + AND layers and could be used to model any classification problem with arbitary precision.
</body>
</html>