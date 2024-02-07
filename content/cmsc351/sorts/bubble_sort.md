---
title: Bubble Sort
tags:
- cmsc351
---

# Introduction

Some notes to keep in mind is that:  
* This is the simplest sorting algorithm
* There are various versions of this
* Be aware of which algoritm we're thinking of.

# Bubble Sort

We pass through a list from left-to-right, comparing adjacent elements as we iterate. If the elements are out of order, we swap the two elements. At the end of this pass, the largest element is on the right.

>[!visual]+ One Iteration of Bubble Sort
>[2, **11**, 1, 5, 8, 0]  
>[2, **11**, 1, 5, 8, 0]  
>[2, 1, **11**, 5, 8, 0]  
>[2, 1, 5, **11**, 8, 0]  
>[2, 1, 5, 8, **11**, 0]  
>[2, 1, 5, 8, 0, **11**]  

>This is done repeatedly until only the first two elements of the list are left to be compared

```python
# PRE: A is a list of length n
for i = 0 to n - 2
    for  j = 0 to n - i - 2
        if A[j] > A[j + 1]
            swap A[j] and A[j + 1]
        end
    end
end
# POST: A is sorted 
```

Observe that wheen $i = 0$ we see $j$ goes from $0$ to $n - 2$.  
* starts by comparing $A[0]$ and $A[1]$  
* ends by comparing $A[n-2]$ and $A[n-1]$  

Observe that when $i =  2$ we see $j$ goes from $0$ to $n - ( n - 2 ) - 2 = 0$

# TIme Complexity

No matter what the list looks like, the time, with the labeling above is:

$$
\sum_{i=0}^{n - 2} \sum_{i=0}^{n - i - 2} c = \theta(n^2)
$$

**Best Case:** $\theta(n^2)$  
**Average Case:** $\theta(n^2)$  
**Worse Case:** $\theta(n^2)$  