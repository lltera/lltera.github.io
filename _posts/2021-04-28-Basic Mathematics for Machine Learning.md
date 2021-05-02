---
layout: splash
title:  "Basic Linear system"
subtitle: "0. Basic Linear system"
categories:
    - Mathematics for Machine Learning
tags:
    - Mathematics
author_profile: true
---
# Linear system
## import numpy

first. import numpy in this notebook


```python
import numpy as np
```

it means we gonna use numpy library as np

# why numpy


```python
# List array
L=range(1000)
%timeit [i**2 for i in L]
```

    251 µs ± 18 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)



```python
# Numpy array
N = np.arange(1000)
%timeit N**2
```

    1.54 µs ± 55.9 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)


This shows that The Numpy array overwhelming computational speed compared to the list.

### numpy.array


```python
# array
arr = np.array([1,2,3])

arr
```




    array([1, 2, 3])




```python
arr_2d = np.array([[1,2,3],[4,5,6],[7,8,9]])
arr_2d
```




    array([[1, 2, 3],       [4, 5, 6],       [7, 8, 9]])




```python
List_2d=[[1,2,3],[4,5,6],[7,8,9]]List_2d
```




    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]



Numpy array is also convenient to see in a 2-dimensional array as well.


```python
arr_2d.shape
```




    (3, 3)




```python
# vectora = np.array([[3, 1, 1], [1, -2, -1], [1, 1, 1]])b = np.array([4, 1, 2])
```


```python
b
```




    array([4, 1, 2])




```python
np.shape(b)
```




    (3,)




```python
# inverse matrixa_inv = np.linalg.inv(a)a_inv
```




    array([[ 5.00000000e-01, -7.40148683e-17, -5.00000000e-01],       [ 1.00000000e+00, -1.00000000e+00, -2.00000000e+00],       [-1.50000000e+00,  1.00000000e+00,  3.50000000e+00]])




```python
np.shape(a_inv)
```




    (3, 3)




```python
# Using the inverse matrix to solve Ax = B x = np.matmul(a_inv, b)x
```




    array([ 1., -1.,  2.])




```python
x = a_inv @ bx
```




    array([ 1., -1.,  2.])




```python
# prove the result
bb = a @ x

print(np.shape(bb))
print(bb)

if np.linalg.norm(b-bb) < 1e-3: # compare with original array
    print("OK")
else:
    print("something wrong")
```

    (3,)
    [4. 1. 2.]
    OK


