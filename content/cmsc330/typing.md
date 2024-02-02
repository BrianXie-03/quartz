---
title: Typings
tags:
- cmsc330
---

# Typing

**Type Checking:** The process of determining a variable's type

Type statements, associated with variables, determine what data is and how it's used

| Type | Java | C90 |
| -- | -- | -- |
| 3 | int | int |
| true | boolean | not supported |
| 3.4 | double | double |
| 3 + 4 | int | int |
| 55 && 10 | not supported | supported |

**Note:** There are different types of typing that are able to describe the way other coding languages are set up and some may be able to have multiple typings.

| Typing | Definition |
| -- | -- |
| Dynamic Typing | Perform type checking at run-time
| Static Typing | Perform type checking at compile-time
| Manifest (explicit) Typing | Explicitly telling compiler the type |
| Latent (implicit) Typing | Not needed to give a type to a variable |

```python
x = 4 # Initialization
print(x)
y = True # Initialization
x = "hello" #latent typing went from 4 to hello
print(x)
```