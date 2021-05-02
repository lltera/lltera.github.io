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


```python

```

Let's search element '10' here. Start from node '12', '10' is smaller than '12'. So we go left side of '12' which is element '9'. Now elemet '10' is bigger than '9'. Then we go right side of it. We found it !

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

but the recursive algorithm, In some cases, it's not efficient because the function must be calleded continuosly.


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
    if x==0:
        return 0
    if x==1:
        return 1
    else:
        return solution(x-1) + solution(x-2)
# iterative way
def fibonacci_iter(x):
    a,b = 1,1
    if x==0:
        return 0
    if x==1:
        return 1
    for i in range(1,x):
        a,b = b, a+b
    return a
```
