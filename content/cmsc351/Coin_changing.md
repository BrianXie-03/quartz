---
title: Coin Changing
tags:
- cmsc351
- wip
---

# Introduction

Suppose our currencty has certain coin denominations.

| U.S. Currency | Justinland Currency |
| ---- | ---- |
| 1-cent | 1-cent |
| 5-cent | 4-cent |
| 10-cent | 6-cent |
| 25-cent | 7-cent |

**General Question: For any total n, how can we obtain n using a optimal (minimal) amount of coins)?**

**Note:** To avoid uncalculatable numbers, we wil always have a 1-cent coin.

# Greedy Method

**Definition:** A greedy agorithm makes the *best* next move without regard for the future.

For coin-changing, we progress as follows, for some n = total.
1. Pick max coins $\le$ n
2. subtract ron n
3. pick " " $\le$ new amount subtract from amount
4. etc.


>[!example]- Example One
>Let c = [1, 5, 10, 25]
>if n = 17:
>1. choose 10-cent. now need 7-cent
>2. choose 5-cent. now need 2-cent
>3. choose 1-cent, now need 1-cent
>4. Done 17 = 10 + 5 + 1 + 1 (4 coins)

>[!example]- Example Two
>c = [1, 4, 6]
>if n = 9:
>1. choose 6-cent
>2. choose 1-cent
>3. choose 1-cent
>4. choose 1-cent
done! 9 = 6 + 1 + 1 + 1 (4 coins)

**Note:** For some cases, using the Greedy Algorithm does not yield the most optimal solution (see Example Two), For those cases we may use Dynamic Programming to find the most optimal solution.

# Dynamic Programming

**Definition** We use earlier answers to get later answers.

Suppose we have an array A with:
xsad

A[1]= min # coins to make 1-cent

A[2]= min # coins to make 2-cent

.

.

.

A[n-1]= min # coins to make n-1 cents.

>[!example]+ Example Three
> **Question:** How can we figure out A[n} = min # coins to make n-cents given C = [1, 4, 6]


Q: How can we figure out A[N]= min # coins to make n cents?
A: Look at C = [1, 4, 6]
When we make n-cents we must use at least one coin!
3 options
We use a 1-cent coin and then n-1 cents left over.
that takes A[n-1] coins (optimal).
Total of 1 + A[n-11]

we use a 4-cent coin and then n-4 cents left over.
that takes A[n-4] coins (optimal)
Total of 1 + A[n-4]

we use a 6-cent coin and then n-6 cents left over
that takes A[n-6] coins (optimal)
total: 1 + A[n-6]

Want the best, thus
A[n] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]}

**Note:** For some n, not all will make sense. Use only those which do

Example; C = [1, 4, 6]


A[0] = 0

A[1] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{1} = 1

A[2] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{2} = 2

A[3] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{3} = 3

A[4] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{4, 1} = 1

A[5] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{2, 2} = 2

A[6] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{3, 3, 1} = 1


```python
A = empty list which can grow as needed
A[0] = 0
C = list of coin denominations
for n = 1 to x:
    howmanycoins = infinity
    for each coin in C:
    	if n - coins >= 0
	       	     howmanycoins = min(howmanycoins, 1+A[n-coins])
	   	end if
	end for
    A[n] = howmanycoins
end for
```

Time Requirements:

Outer loops runs x times

inner loops runs length(c) times (#diff coins)

Innernmost assignment (x)(length(c) times

if we think of c as fixed, then length(c) = constant

so innermost assignment runs x * lenth(c) times, where length(c) is a constant
thus we see that this is linear O(n)