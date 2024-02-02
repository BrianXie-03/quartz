---
title: Functional Programming
tags:
- cmsc330
---

# Functional Programming

**Functional Programming:** A way of programming that focuses on creating functions rather than listing out steps to solve a problem.  

**Programming Paradigm:**
* Typically used interchangibly with language features
* Many languages have a ton of overlap. eg:
* Python is imperative, objective-orientated and function
* Ocaml is imperative, object-oriented and funcction
* but they focus on different things

## Declarative Languages

There are two common types of declarative langauges when it comes to functional languages, **imperative** and **declariative**.

**Imperative** instructions tell how to do something in steps while **declarative** instructions tells you what you are looking for and assumes you can do it.

**Imperative:**
* make an empty list called results
* look at each item in the list
* divide the item by 2 and look at the remainder
* if the remainder is 0, add the vavlue to the results list
* return the results list after you looked at all the items

```python
# This is an example of an imperiative function
def evens(arr):
    results = []
    for x in arr:
    	remainder = item % 2
    	if remainder == 0:
       	   results.push(item)
    return results
```

**Declariative:**
* take all the values that are evenly divisibly by 2 from the list
* return those values

```ocaml
(* this is an example of a declariative function *)
let results = [x for x in arr if x % 2 == 0]
```
## Side Effects and Immutability

**Side Effects:** Actions in code that end up manipulating some sort of element in the code. Alternatively, it is when non-local variables get modified
> x++;

| Mutability | Definition |
| -- | -- |
| Mutable | Changeable object that can be modified after it is created  |
| Immutable | Non-changable object that can not be modified after it is created |

**Program State:** the state of the machine at any given time

**Imperative** instructions have **states** thare are **mutable**, thus changing or destructive as it can cause side effects. 

```java
# side_effects
int count = 0;
int f(Node node){
    node.data = count;
    count += 1; #side effect
    return count;
}
```

Futhermore, lets look at a comparison of two different function calls:

```python
f(x) + f(x) + f(x) = 3 * f(x)
```
Mathematically, this may look like it makes sense but the L.H.S function call yields more side effects then the R.H.S. In order to combat this issue, some programming languages like [[ocaml]] makes all variables immutable to help maintain **referential transparency**.

**Referential Transparency:** The ability to replace an expression or a function with it's value and still obtain the same output.