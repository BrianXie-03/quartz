---
title: Python
tags:
- wip
- cmsc320
---

# Importance

**Python:** User friendly language for data analysis
**Git:** Helps manage code and data changes when workign with a team (LATER TOPIC)
**Pandas:** Simplifies data cleaning and manipulation (LATER TOPIC)
**Databases:** Needed for storing and retrieving data efficiently (LATER TOPIC)

These skills are essential for effective data anlysis, collaboration, and handling data in real-world projects

# Python Introduction

* Known for simplicity and readability
* Executre source code directly
* Intuitive and easy to program
* Support dynamic typing
* Focus on important modules
* Runs on most operating systems and platforms
* Slow

```python
def add(a, b):
    return a + b

def main():

    # Count to ten
    i = 0
    while i < 10:
    	  print(i)
	  i += 1

    # Count to ten a different way
    for i in range(0, 10):
    	print(i)

    # Printing a list
    myList = [1, 2, 3, 4]
    for some_item in my_list:
    	print(some_item)

    return
```

## Variable Types

**Dynamically Typed:** The type of the varaible is dervied from the value it is assigned




List (ordered, mutable set of objects) var = ['one', 1, 1.0]
Tuples (ordered, immutable set of objects) var = ('one', 1, 1.0
Dictionaries (Unordered lists of key-valued pairs) var = {'one';1;, 'two' :2}


## Slicing

In Python, slicing is a way t oextract a portion of a sequence (list a list, tuple, or string)
* The syntax: **start:stop:step::. Step is optional; if step is ot specified, it dafaults to 1