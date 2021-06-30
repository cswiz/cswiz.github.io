---
layout: single
title: "Fluent Python for Problem Solving"
categories:
    - Python
tags:
    - Python
    - Problem Solving
    - Syntax
---

# I/O

## `input()`, `map()`

```python
s = input()  # Read a line
a, b, c = map(int, input().split())  # Read a line, split the line by whitespaces, and map each one to int
a = list(map(int, input().split()))  # Make a list
```

## `sys.stdin.readline()`

For fast input read, use `sys.stdin.readline()`
```python
import sys

input = sys.stdin.readline
N, M = map(int, input().split())  # few inputs
m = [list(map(int, input().split())) for _ in range(N)]  # 2D Array

# 2D Array Initialization
v = [[True] * 10] * 10  # No
v = [[True for _ in range(10)] for _ in range(10)]  # Yes

# readline
s = input().rstrip()  # NOTE: `sys.stdin.readline()` also reads newline character, so you should strip it out if you don't need the character
```

## f-string

```python
n = 1000
print(f"The answer is {n}!")
```

## Unpacking

```python
a = [1, 2, 3]

print(a)  # [1, 2, 3]

for elem in a:
    print(elem, end=' ')  # 1 2 3

# Unpack
print(*a)  # 1 2 3
```

## File I/O

```python
import sys

sys.stdin = open("input.txt", "r")
```


# String

```python
# Definition
s = "abc"

# Conversion to list
l = list(s)  # ['a', 'b', 'c']

# Conversion from list to string
converted_string = ''.join(l)  # "abc"
```


# List

##  `index()`

```python
operators = ['-', '*', '-', '+']
i = operators.index('-')  # 0
i = operators.index('-')  # 0

del operators[i]
i = operators.index('-')  # 1
```

##  `count()`
```python
a = [1, 2, 3, 3, 3, 3, 2, 5, 6, 10, 5, 4]

a.count(3)  # 4
a.count(2)  # 2
a.count(5)  # 2
```


# Set

```python
# Definition
s1 = set([1, 2, 3])  # {1, 2, 3}
s2 = set("Hello")  # {'e', 'H', 'l', 'o'}

# Conversion to list
l1 = list(s1)  # [1, 2, 3]
l2 = list(s2)  # ['e', 'H', 'l', 'o']

# Conversion to tuple
t1 = tuple(s1)  # (1, 2, 3)
t2 = tuple(s2)  # ('e', 'H', 'l', 'o')

# Add one element
s1.add(4)  # [1, 2, 3, 4]
# Remove one element
s1.remove(4)  # [1, 2, 3]
# Accept another iterable
s1.update([4, 5, 6])  # [1, 2, 3, 4, 5, 6]

s3 = set([4, 5, 6, 7, 8, 9])
# Intersection
intersection = s1 & s3  # {4, 5, 6}
# Union
union = s1 | s3  # {1, 2, 3, 4, 5, 6, 7, 8, 9}
# Difference
difference1 = s1 - s3  # {1, 2, 3}
differecne2 = s3 - s1  # {8, 9, 7}
```


# Loop

```python
# Case 1
s = 0
for i in range(1, 10 + 1):
    s += i

# Case 2
s = sum(i for i in range(1, 10 + 1))
```


# Iterate through Array

```python
a = ['A', 'B', 'C']
for element in a:
    print(element)
```


# Generics

```python
# Case 1
def are_equal(a, b):
    return a == b

are_equal(10, 10.0)

# Case 2
from typing import TypeVar

T = TypeVar('T')
U = TypeVar('U')

def are_equal(a: T, b: U) -> bool:
    return a == b

are_equal(10, 10.0)
```


# Struct

```python
from dataclasses import dataclass

# Data Classes module is only work in Python 3.7 and above.
# A backport of the module for Python 3.6 <https://pypi.org/project/dataclasses/>
@dataclass
class Product:
    weight: int = None
    price: float = None

apple = Product()
apple.price = 10
```


# Class

```python
from dataclasses import dataclass

@dataclass
class Rectangle:
    width: int
    height: int

    def area(self):
        return self.width * self.height

rect = Rectangle(3, 4)
print(rect.area())
```


# Inheritance

```python
from dataclasses import dataclass

@dataclass
class Animal:
    name: str

    def move(self, distanceInMeters: int = 0):
        print('%s moved %sm.' % (self.name, distanceInMeters))

class Horse(Animal):
    def move(self, distanceInMeters: int = 45):
        print('Galloping...')
        super().move(distanceInMeters)

tom: Animal = Horse('Tommy')
tom.move(34)
```


# Built-in Functions

## `enumerate()`

```python
a = ['a', 'b', 'c']
for i, v in enumerate(a):
    print(i, v)

'''
0 a
1 b
2 c
'''
```

## `eval()`

```python
x = 1
eval('x+1')  # 2

eval("100-200*300-500+20")  # -60380
```

## `zip()`

Make an iterator that aggregates elements from each of the iterables.
```python
a = [1, 2, 3]
b = [4, 5, 6]
for i, j in zip(a, b):
    print(i, j)

'''
1 4
2 5
3 6
'''
```

# Libraries

## collections

### Counter

```python
from collections import Counter
a = Counter([1, 1, 2, 2, 2])  # Counter({1: 2, 2: 3})
```

#### "-" Operation

```python
from collections import Counter

a = Counter([1, 1, 2, 2, 2])
b = Counter([1, 2, 2, 3])

print(a - b)  # Counter({1: 1, 2: 1})
```

### deque

```python
from collections import deque

queue = deque([1, 2, 3, 4, 5])
queue.popleft()  # O(1)
```

## itertools

### permutations

```python
from itertools import permutations

a = [1, 2, 3]
p = list(permutations(a))  # [(1, 2, 3), (1, 3, 2), (2, 1, 3), (2, 3, 1), (3, 1, 2), (3, 2, 1)]

```

### combinations

```python
from itertools import combinations

a = [1, 2, 3]
c = list(combinations(a, 2))  # [(1, 2), (1, 3), (2, 3)]
```

## functools

### `cmp_to_key()`

```python
from functools import cmp_to_key

# Your goal is to sort the give numbers to ["9", "5", "34", "3", "30'],
# not ["9", "5", "34", "30", "3'] since 9534330 is larger than 9534303.
numbers = ["34", "3", "30", "9", "5"]


def compare(a, b):
    """Compare two given parameters"""
    t1 = a + b
    t2 = b + a
    if t1 < t2:
        return -1
    elif t1 > t2:
        return 1
    else:
        return 0

numbers = sorted(numbers, key=cmp_to_key(compare), reverse=True)  # ["9", "5", "34", "3", "30"]
```

## re

### `sub()`

```python
from re import sub

s = "...!@BaT#*..y.abcdefghijklm"
s = sub("[^a-z0-9-_.]", "", s)  # "...a..y.abcdefghijklm"
s = sub("[.]+", ".", s)  # ".a.y.abcdefghijklm"
```

### `findall()`

```python
from re import findall

expression = "100-200*300-500+20"
operators = findall("[*+-]+", expression)  # ['-', '*', '-', '+']
operands = findall("[0-9]+", expression)  # ['100', '200', '300', '500', '20']
```

### `split()`

```python
from re import split

expression = "100-200*300-500+20"
operands = split("[*+-]+", expression)  # ['100', '200', '300', '500', '20']
```


# Error

## Recursion Error

### Solution1

Use iteration instead of recursion.

### Solution2

Increase recursion limit.
```python
import sys
sys.setrecursionlimit(10 ** 6)
```
