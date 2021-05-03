---
layout: splash
title:  "Numpy operation"
subtitle: "Numpy operation"
categories:
    - data analysis
tags:
    - data analysis
author_profile: true
---

# Numpy operation

## vector - scalar operation
operate each element in vector with scalar

x = [1,2,3] c = 5


```python
import numpy as np
x = np.array([1,2,3]) 
c = 5
print("plus : {}".format(x + c))
print("minus : {}".format(x - c))
print("multiply : {}".format(x * c))
print("divide : {}".format(x / c))
```

    plus : [6 7 8]
    minus : [-4 -3 -2]
    multiply : [ 5 10 15]
    divide : [0.2 0.4 0.6]
    

## vector - vector operation
operate same index in each vector

y = [1,3,5]  z = [2,9,20]


```python
y = np.array([1,3,5])
z = np.array([2,9,20])

print("plus : {}".format(y + z))
print("minus : {}".format(y - z))
print("multiply : {}".format(y * z))
print("divide : {}".format(y / z))
```

    plus : [ 3 12 25]
    minus : [ -1  -6 -15]
    multiply : [  2  27 100]
    divide : [0.5        0.33333333 0.25      ]
    

## Indexing in Array
similar to List in python


```python
W = np.array([[1,2,3,4],[5,6,7,8],[9,10,11,12]]) # 3 * 4 matrix
print(W[0,0])
print(W[2,3])
```

    1
    12
    


```python
# if i want 7?
W[1,2]
```




    7



## Slicing in Array


```python
W[0:2,1:3]
```




    array([[2, 3],
           [6, 7]])




```python
print(W[0:2,0:4]) # same result
print(W[0:2])
print(W[0:2,:])
```

    [[1 2 3 4]
     [5 6 7 8]]
    [[1 2 3 4]
     [5 6 7 8]]
    [[1 2 3 4]
     [5 6 7 8]]
    

## Broadcasting in Array
A special way to proceed with an operation in Numpy.
Basically particular shapes of array are possible to operate.
But numpy treats arrays with different shapes during arithmetic operations. Subject to certain constraints, the smaller array is broadcast across the larger array so that they have compatible shapes.

1. M * N matrix , M * 1 matrix


```python
a = np.array([[1,2,3],[4,5,6],[7,8,9]])
x = np.array([0,1,0])
```


```python
x = x[:,None]# transpose matrix x
x
```




    array([[0],
           [1],
           [0]])




```python
print(a+x) # get same result matrix a + [[0 0 0], [1 1 1], [0 0 0]]
```

    [[1 2 3]
     [5 6 7]
     [7 8 9]]
    

2. M * N matrix , 1 * N matrix 


```python
y = np.array([0,1,-1])
print(a*y)
```

    [[ 0  2 -3]
     [ 0  5 -6]
     [ 0  8 -9]]
    

3. M * 1 matrix , 1 * N matrix


```python
t = np.array([1,2,3])
t= t[:,None] # Transpose

u = np.array([2,0,-2])
print(t+u)
```

    [[ 3  1 -1]
     [ 4  2  0]
     [ 5  3  1]]
    

[1 1 1]  +  [2 0 -2]    =     [3  1  -1] \
[2 2 2]  +  [2 0 -2]    =    [4  2   0] \
[3 3 3]  +  [2 0 -2]    =     [5  3   1] 

# Numpy with linear algebra
## A. Basics
### Zero(or Null) matrix
-  a zero matrix or null matrix is a matrix all of whose entries are zero.  
-  create `np.zeros(dim)`,  dim need to be nature number or tuple


```python
np.zeros(3)
```




    array([0., 0., 0.])




```python
np.zeros(3,3) # need to be tuple
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-32-a1af5744063d> in <module>
    ----> 1 np.zeros(3,3)
    

    TypeError: data type not understood



```python
np.zeros((3,3))
```




    array([[0., 0., 0.],
           [0., 0., 0.],
           [0., 0., 0.]])



### Matrix of ones
-  a matrix of ones or all-ones matrix is a matrix where every element is equal to one
-  `np.ones(dim)`,  dim need to be nature number or tuple


```python
np.ones(2)
```




    array([1., 1.])




```python
np.ones((3,3))
```




    array([[1., 1., 1.],
           [1., 1., 1.],
           [1., 1., 1.]])



### Diagonal Matrix
-   a diagonal matrix is a matrix in which the entries outside the main diagonal are all zero
-  `np.diag((main_diagonal))`


```python
np.diag((2,4))
```




    array([[2, 0],
           [0, 4]])




```python
np.diag((1,3,5))
```




    array([[1, 0, 0],
           [0, 3, 0],
           [0, 0, 5]])



### Identitiy Matrix
-    the identity matrix (sometimes called a unit matrix) of size n is the n × n square matrix with ones on the main diagonal and zeros elsewhere.
-  `np.eye(size, (data_type= int, uint, float, complex, .....))`


```python
np.eye(2)
```




    array([[1., 0.],
           [0., 1.]])



### Dot product
-  `np.dot()`,`@`


```python
mat_1 = np.array([[1,4],[2,3]])
mat_2 = np.array([[7,9],[0,6]])

mat_1.dot(mat_2)
```




    array([[ 7, 33],
           [14, 36]])




```python
mat_1 @ mat_2
```




    array([[ 7, 33],
           [14, 36]])



## B. Furthermore
### Trace
-  sum of main diagonal
-  `np.trace()`


```python
arr = np.array([[1,2,3],[4,5,6],[7,8,9]])
arr
```




    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])




```python
arr.trace()
```




    15




```python
np.eye(2, dtype=int).trace()
```




    2



### Determinant
-  a scalar value that is a function of the entries of a square matrix. It allows characterizing some properties of the matrix and the linear map represented by the matrix.
-  In particular, the determinant is nonzero if and only if the matrix is invertible, and the linear map represented by the matrix is an isomorphism.
-  `np.linalg.det()`


```python
arr_2 = np.array([[2,3],[1,6]])
arr_2
```




    array([[2, 3],
           [1, 6]])




```python
np.linalg.det(arr_2)
```




    9.000000000000002




```python
arr_3 = np.array([[1,4,7],[2,5,8],[3,6,9]])
arr_3
```




    array([[1, 4, 7],
           [2, 5, 8],
           [3, 6, 9]])




```python
np.linalg.det(arr_3) # this matrix is non invertable
```




    0.0



### Inverse matrix
- for an n × n matrix A-1 which is called the inverse of A such that: AA-1 = A-1A = I (identity matrix)
- `np.linalg.inv()`


```python
mat = np.array([[1,4],[2,3]])
mat
```




    array([[1, 4],
           [2, 3]])




```python
mat_inv = np.linalg.inv(mat)
mat_inv
```




    array([[-0.6,  0.8],
           [ 0.4, -0.2]])




```python
mat @ mat_inv
```




    array([[1., 0.],
           [0., 1.]])



### Eigenvalue and Eigenvector
- When a nonzero vector x exists with Ax = λx (constant λ) for the square matrix A. The constant λ is called the eigenvalue of matrix A, and the corresponding eigenvector of x.
- `np.linalg.eig()`


```python
mat = np.array([[2,0,-2],[1,1,-2],[0,0,1]])
mat
```




    array([[ 2,  0, -2],
           [ 1,  1, -2],
           [ 0,  0,  1]])




```python
np.linalg.eig(mat)
```




    (array([1., 2., 1.]),
     array([[0.        , 0.70710678, 0.89442719],
            [1.        , 0.70710678, 0.        ],
            [0.        , 0.        , 0.4472136 ]]))




```python
#validation

eig_val, eig_vec = np.linalg.eig(mat)

eig_val
```




    array([1., 2., 1.])




```python
eig_vec
```




    array([[0.        , 0.70710678, 0.89442719],
           [1.        , 0.70710678, 0.        ],
           [0.        , 0.        , 0.4472136 ]])




```python
mat @ eig_vec[:,0] # Ax
```




    array([0., 1., 0.])




```python
eig_val[0] * eig_vec[:,0]# λx
```




    array([0., 1., 0.])




```python

```
