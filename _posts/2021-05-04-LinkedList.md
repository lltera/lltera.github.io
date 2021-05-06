# Linked List
## What is Linked List ?
The linked list is similar to a linear array in that it sequences data elements, but there is a significant difference between the two in terms of how data elements are arranged. 

In a linked list is a linear collection of data elements whose order is not given by their physical placement in memory. Instead, each element points to the next. It is a data structure consisting of a collection of nodes which represent a sequence.

![arrayandlinklist](https://i1.faceprep.in/Companies-1/difference-between-arrays-and-linked-list.png)

## Advantage of Linked List

In a list of connections, each nodes points to the next node, so it is easier to break in the middle to delete one, or break in the middle to insert another element in its place than in a linear array.

The expression "easy" here means that it can be processed **quickly**. 

Because of this advantage, the linked list is highly utilized in applications where elements are inserted/deleted frequently.

## Disadvantage of Linked List

One disadvantage is that compared to linear arrays, the storage (memory) requirements of data structures are bigger. Links must also be stored in memory, so in order to represent a linked list, the memory requirement that used to hold the same data elements is bigger.

It takes longer to find the "k-th element" than in the case of linear arrays. In a linear array, data elements are contained in numbered squares, so you can use that number to find a particular element at once, whereas in a linked list, elements appear to be connected by link, so you must follow the link one by one.


```python
class Node:

    def __init__(self, item):
        self.data = item
        self.next = None
```

node 사진 첨부


```python
class LinkedList:
    def __init__(self):
        self.nodeCount = 0
        self.head = Node(None)
        self.tail = None
        self.head.next = self.tail

```

dummy 사진첨부
To solve the problems that can occur when handling the first node, add dummy node at head

### Traverse


```python
    def traverse(self):
        result = []
        curr = self.head
        while curr.next:
            curr = curr.next
            result.append(curr.data)
        return result
```

### get k-th elements


```python
    def getAt(self, pos):
        if pos < 0 or pos > self.nodeCount:
            return None

        i = 0
        curr = self.head
        while i < pos:
            curr = curr.next
            i += 1

        return curr
```

### insert elemets
#### insertAfter()
When you want to insert a new Node in front of the prev Node.
if this process success then return True


```python
    def insertAfter(self, prev, newNode):
        newNode.next = prev.next
        if prev.next is None:
            self.tail = newNode
        prev.next = newNode
        self.nodeCount += 1
        return True
```

1. newNode.next indicates prev.next
2. prev.next indicates newNode

image insert last

in case add newNode at the last, need to consider about tail.
#### insertAt()
1. check the position that i want to insert is available. if not return False
2. if that position == 1, then insert newNode at in front of head.
3. if positon == nodeCount+1, it means that insert newNode at the tail.
4. if positon is not head or tail, then need to check that position from the first to that positon to use getAt() function.


```python
     def insertAt(self, pos, newNode):
        if pos < 1 or pos > self.nodeCount + 1:
            return False

        if pos != 1 and pos == self.nodeCount + 1:
            prev = self.tail
        else:
            prev = self.getAt(pos - 1)
        return self.insertAfter(prev, newNode)
```

### Pop elemets
#### popAfter()
When you want to pop Node in linked list. Pop the Node in front of prev node and return data in that node.

But
1. if prev node is the last, it means there is no node to pop.
2. and if pop the node at the last in that list, need to change the tail.


```python
    def popAfter(self, prev):
        if prev.next == None:
            return None
        curr = prev.next
        if curr.next == None:
            self.tail = prev
            prev.next = None
        else:
            prev.next = curr.next
        self.nodeCount -= 1
        return curr.data


    def popAt(self, pos):
        if pos < 1 or pos > self.nodeCount:
            raise IndexError
        prev = self.getAt(pos-1)
        return self.popAfter(prev)
```


```python

```
