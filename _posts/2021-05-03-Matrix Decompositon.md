---
layout: splash
title:  "Matrix Decomposition"
subtitle: "3. Matrix Decomposition"
categories:
    - Mathematics for Machine Learning
tags:
    - Mathematics
author_profile: true
---

# Matrix Decomposition

## LU decomposition
In numerical analysis and linear algebra, LU decomposition factors a matrix as the product of a lower triangular and an upper triangular matrix. LU decomposition can be viewed as the matrix form of Gaussian elimination. It is a key step when inverting a matrix or computing the determinant of a matrix.



L : lower triangular matrix
U : upper triangular matrix

### Usage of LU decomposition
### If Ax = b

 ![image](./images/2021-05-03-Matrix%Decompositon/Ax=b.JPG)

### Forward-substitution : calculate y

![L](./images/2021-05-03-Matrix%Decompositon/L.JPG)

### Back-substitution : calculate x

![U](images/2021-05-03-Matrix%Decompositon/U.JPG)


### Advantage of LU decomposition
1. It is much easier to compute the inverse of an upper or lower triangular matrix. Since inverses are useful for solving linear systems, this makes solving any linear system associated to the matrix much **faster** as well.

2. Frequent updates of b in Ax = b: In a linear system, if the matrix A is fixed and b changes, the solution of the linear system can be obtained whenever b is updated.

## QR decomposition
updating...

## SVD(Singular Value Decomposition)
updating...


