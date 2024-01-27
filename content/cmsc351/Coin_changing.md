---
title: Coin Changing
tags:
- cmsc351
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

# Greedy Algorithm

**Definition:** A greedy agorithm makes the *best* next move without regard for the future.

For coin-changing, we progress as follows, for some n = total.
1. Pick highest value coins $\le$ n
2. Subtract the value from n, until you cant
3. pick the next lowest coin value $\le$ new amount subtract from amount
4. Repeat until n is reached in value.

Provided are some examples of using the **Greedy Algorithm:**
>[!example]- Example One
>Let c = [1, 5, 10, 25] (types of coins that we have)  
>if n = 17:
>1. Choose 10-cent, now need 7-cent
>2. Choose 5-cent, now need 2-cent
>3. Choose 1-cent, now need 1-cent
>4. Choose 1-cent, now need 0-cent
>5. Done! 17 = 10 + 5 + 1 + 1 (4 coins)

>[!example]- Example Two
>c = [1, 4, 6] (types of coins that we have)  
>if n = 9:
>1. choose 6-cent, now need 3-cent
>2. choose 1-cent, now need 2-cent
>3. choose 1-cent, now need 1-cent
>4. choose 1-cent, now need 0-cent
>5. Done! 9 = 6 + 1 + 1 + 1 (4 coins)  
>>**Important** this is actually not the most optimal amount of coins that can be used. We could've actually used two 4-cent coins and one 1-cent coin.

**Note:** For some cases, using the **Greedy Algorithm** does not yield the most optimal solution (see Example Two), For those cases we may use Dynamic Programming to find the most optimal solution.

# Dynamic Programming

As previously mentioned, the Greedy Algorithm does not necessarily give the most optimal solution to an coin changing problem.

**Definition** We use earlier answers to get later answers. Fundamentally, we record our previous answers and use it to guide an decided what would be the next most optimal answer.

Suppose we have an array A with:
* A[1] = minimal amount of coins to make 1-cent
* A[2] = minimal amount of coins to make 2-cent
* ...
* A[n-1] = minimal amount of coins to make n-1 cents.

>[!example]- Example Three
> **Question:** How can we figure out A[n] = minimal amount of coins to make n-cents given C = [1, 4, 6]  
>Notice that since we have 3 coins we have 3 cases  
>**Case 1:** We use a 1-cent coin and then n-1 cents left over. This takes A[n-1] coins, resulting in a total of 1 + A[n-1] coins.  
>**Case 2:** we use a 4-cent coin and then n-4 cents left over. This takes A[n-4] coins, resulting in  a total of 1 + A[n-4] coins.  
>**Case 3:** we use a 6-cent coin and then n-6 cents left over. This takes A[n-6] coins, resulting in a total of 1 + A[n-6] coins.  
>Dynamically Programming method wants the best, thus:  
>A[n] = min{ 1+A[n-1], 1 + A[n-4], 1 + A[n-6] }
>>[!done]- Solution
>>>A[0] = 0  
>>>A[1] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{1} = 1  
>>>A[2] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{2} = 2  
>>>A[3] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{3} = 3  
>>>A[4] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{4, 1} = 1  
>>>A[5] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{2, 2} = 2  
>>>A[6] = min{1+A[n-1], 1 + A[n-4], 1 + A[n-6]} = min{3, 3, 1} = 1

**Note:** For some n, not all cases will make sense. The most optimal amount of coins needed will usually yield only a few cases. Use only the coins which do provide the most optimal answer.

```python
A = empty list which can grow #Thus this can allow for any amount of coins
A[0] = 0 #Set the first value of the list to 0
C = list of coin denominations #Possible values of coins
for n = 1 to x: #Start from the beginning to x amount of times
    howmanycoins = infinity #Set a value of how many coins can be used
    for each coin in C: #iterate through the coin denominations for possible values
    	if n - coins >= 0 #check if the coin is usable
	       	     howmanycoins = min(howmanycoins, 1+A[n-coins]) #calc best sol
	   	end if
	end for
    A[n] = howmanycoins #Record how many coins is needed for n value
end for
```

### Time Requirements:

* We see that the outer loops runs x times
* We See that the inner loops runs length(c) times
* We calculate (x)(length(c) amount of times the code is iterated
> if we think of c as fixed, then length(c) = constant

So innermost assignment runs x * lenth(c) times, where length(c) is a constant
thus we see that this is linear **O(n)**