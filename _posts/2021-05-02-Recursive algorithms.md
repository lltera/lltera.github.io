---
layout: splash
title:  "Recursive algorithms"
subtitle: "3. Recursive algorithms"
categories:
    - Algorithm
tags:
    - Algorithm
author_profile: true
---

# Recursive algorithms
A recursive algorithm is an algorithm which calls itself with "smaller (or simpler)" input values, and which obtains the result for the current input by applying simple operations to the returned value for the smaller (or simpler) input.

## An example of a recursive algorithm.
### Binary trees
Based on one node, when the left node is smaller and the right node is bigger, it has recursive properties.

![Recursive algorithms1](_posts/images/2021-05-02-Recursive algorithms/Recursive algorithms1.JPG)

Let's search element '10' here. Start from node '12', '10' is smaller than '12'. So we go left side of '12' which is element '9'. Now element '10' is bigger than '9'. Then we go right side of it. We found it !

### sum of the First n natural numbers


```python
def sum(n):
    print(n)
    if n <= 1:
        return n
    else:
        return n + sum(n-1)
```


```python
a= 5
print(sum(a))
```

    5
    4
    3
    2
    1
    15


#### compared recursive and iterative
Recursive version : O(n)

Iterative version : O(n)

but the recursive algorithm, In some cases, it's not efficient because the function must be called continuously.


```python
def sum(n):  ## O(1)
    return n*(n+1)//2
```

### Factorial algorithm


```python
def factorial(n):
    if n <= 1:
        return 1
    else:
        return n * factorial(n-1)
```

### Fibonacci Sequence


```python
# recursive way
def fibonacci_rec(x):
    if x<=0:
        return x
    return fibonacci_rec(x-1) + fibonacci_rec(x-2)
# iterative way
def fibonacci_iter(x):
    if x<=1:
        return x
    else:
        i = 2
        a,b = 0,1
        while i <= x:
            a,b = b, a+b
            i += 1
        return a
```

### Binary search in recursive way

```python
def binary_search(L, x, l, u):
  if l > u:
    	return -1
    mid = (l + u) // 2    
    if x == L[mid]:        
    	return mid    
   	elif x < L[mid]:        
   		return binary_search(L, x, l, mid-1)
   	else:        
   		return binary_search(L, x, mid+1, u)
```
