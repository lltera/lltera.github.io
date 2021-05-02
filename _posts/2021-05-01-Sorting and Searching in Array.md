---
layout: splash
title:  "Sorting and Searching in Array"
subtitle: "2. Sorting and Searching in Array"
categories:
    - Algorithm
tags:
    - Algorithm
author_profile: true
---
# Sorting and Searching in Array

**Seraching** then means finding a record in the array that has a specified value in its key field.
**Sorting** means moving the records around in the array so that the key fields of the record are in invreasing (or decreasing) order.


```python
L = [3, 8, 2, 7, 6, 10, 9]
```


```python
L1 =sorted(L)
```


```python
L1
```




    [2, 3, 6, 7, 8, 9, 10]



## Sorting array in python
1) sorted()
- built-in function
- get new sorted list

2) .sort()
- method of the List
- sorts the corresponding list


```python
L.sort()
```


```python
L
```




    [2, 3, 6, 7, 8, 9, 10]



# When you want a descending sort


```python
L2 = sorted(L,reverse = True)
L.sort(reverse = True)
```


```python
L2
```




    [10, 9, 8, 7, 6, 3, 2]




```python
L
```




    [10, 9, 8, 7, 6, 3, 2]



# In case of sorting strings
Sorting order follows alphaetical order. Not about lenth of the string.


```python
L = ['abcd', 'xyz', 'spam']
```


```python
sorted(L)
```




    ['abcd', 'spam', 'xyz']



when you want to sort strings in order of length.


```python
sorted(L, key = lambda x: len(x))
```




    ['xyz', 'abcd', 'spam']



If you want to sort by specifying a key


```python
L = [{'name':'John','score': 83}, {'name':'Paul','score': 92}]
```

sort by name in list


```python
L.sort(key = lambda x : x['name'])
```

Sort in order of high scores in the list


```python
L.sort(key = lambda x : x['score'], reverse = True)
```

# Searcing in Array
## 1. Linear Search and Sequential search : O(n)
Search all elements sequentially to find the desired value. Because it takes time proportional to the length of the array. In the worst case, you may need to examine all elements in the array.


```python
def linear_search(L,x):
    i = 0
    while i < len(L) and L[i] != x:
        i += 1
    if i < len(L):
        return i
    else:
        return -1
```

## 2. Binary search : O(log n)
Applicable only if the array you are trying to search is already sorted. Comparing the elements in the middle of the array with the values you are trying to search, you can tell whether they are on the left or the right (if there is). Then, at least it's not on the other side, so you can discard half of the array without searching it. Repeat this process to find the desired value.


```python
def binary_search(L, x):
    upper = len(L)-1
    lower = 0 
    while lower <= upper:
        middle = (lower+upper)//2
        if L[middle] == x:
            return middle
        elif L[middle] > x:
            upper=middle
        else:
            lower=middle
    return -1
```

