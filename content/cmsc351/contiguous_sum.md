---
title: Maximum Contiguous Sum
tags:
- cmsc351
---

# Introduction

**Definition:** The highest summation of consecutive elements in an list.

>[!example]- Simple Example
>**Question:** Find the max contiguous sum given a list. This is the maximum sum of the form A[i]+A[i+1]+...+A[i+j], where A is the list.  
>**Example One:** A = [-3, 5, 1, -2, 8, -10,1] MCS= 6 + 1 -2 + 8 =12  
>**Example Two:** A = [-3, -2, -5, -1, -8] MCS = -1  
>> **Note:** We must take at least one element.  

## Brute Force

**Definition:** Trying all possible contiguous sums

>[!code]- Pseudocode
>```python
>#PRE: A is a list of length n
>max = A[0]
>for i = 0 to n - 1:
>    sum = 0
>    for j = i to n - 1:
>    	sum = sum + A[j]
>		if sum > max:
>			max = sum
>		end
>    end
>end
>#POST: max is the maximum sum
>```

>[!info]- Time Complexity
> T(n) = 
>
>$$
>	  = \sum_{i = 0}^{n - 1} \sum_{j = i}^{n - 1}c 
>$$
>$$ 
>     = \sum_{i = 0}^{n - 1} [c(n-1-i+1)]  
>$$
>$$
>     = \sum_{i = 0}^{n - 1} c(n-i)  
>$$
>$$
>     = cn\sum_{x = 0}^{n - 1} 1 - c\sum_{i = a}^{n-1} i  
>$$
>$$
>     = cn(n) - c(n-1)(n)/2  
>$$
>$$
>     = \theta (n^2)
>$$

## Divide and Conquer (DAC)

DAC algorithms work as follows:
* Break list into two (or more) sublists
* Interact with sublists (typically recursive)
* Combine the reuslts, finding the max out of the sublists	

**Idea:** The MCS of a list of length 1 is just that element. Given list $A$ (of length $n$) we divide it in half. We recursively find the MCS's of each half and then we find the largest MCS which straddles the middle. We take the max of all 3.

>[!code]- Pseudocode
>```python
>function mcs(A, L, R)
>    if L == R:
>		return(A[L])
>    else:
>	C = (L + R) // 2 #"floor" 2 (lower integer value of divided by 2 if decimal)
>	Lmax = mcs(A, L, C) # grab the left sublists
>	Rmax = mcs(A, C+1, R) # grab the right sublists
>	
>	# calclate the staddle max
>	Lhmax = -infinity
>	Lhsum = 0
>
>	for i = C downto L	# C = L + 1 times
>	    Lhsum = Lhsum + A[i]
>	    if Lhsum > lhmax
>	       Lhmax = Lhsum
>	    end
>	end
>	
>	Rhmax = -infinity
>	Rhsum = 0
>	
>	for i = C + 1 to R	# R - ( C + 1 ) + 1 = R - C times
>	    Rhsum = Rhsum + A[i]
>	    if Rhsum > Rhmax:
>	       Rhmax = Rhsum
>	    end
>	end
>
>	Smax = Lhmax + Rhmax
>	# Return the overall max
>	return(max(Lmax,Rmax,Smax)
>   end  
>end
> #how to call the function
> result = mcs(A, 0, len(A) - 1)
>```

>[!info]- Time Complexity
>**Time Complexity:**  
>* $0^{th}$ level of recursion - we do some constant time things like C = (L + R) // 2, we make 2 recursion calls, we find max straddle sum. That requires n steps so we could say at >that level of recursion, ignoring the recursive calls, we get linear time $cn$.  
>* $1^{th}$ level of recursion - we have *two* lists of length $\frac{n}{2}$, each takes $c\frac{n}{2}$ for a total of $cn$
>* $2^{th}$ level of recursion - we have *four* lists of length $\frac{n}{4}$, each takes $c\frac{n}{4}$ for a total of $cn$
>* $k^{th}$ level of recursion - etc...
>
> Thus, this brings us to ask how many levels of recursions are there? What is $k$?  
> Suppose $k$ = max level of recursion, at level $k$, list length is:  
>$\frac{n}{2^k}$  
>which gets to 1 (recursion ends) when:  
>$\frac{n}{2^k}$ so $2^k = n$ so $k = lgn$  
>So the levels of recursion are $0,1,2,3,..., lgn$  
>thus we have $1 + lgn$ levels of recursion, each taking time $cn$ for a total:  
>$cn(1+lgn) = \theta(nlgn)$  
> Which we can see is better than $\theta(n^2)$ for the brute force method.

## Kadane's Algorithm (Dynamic Programming)

**Defintion:** For an list $A$ and an index $i$, define a maximun contiguous sum ending at $i = $ mcs which goes up to and **must include and no futher** index i

>[!example]- Simple Example
> $A$ = [ 4, -8, 6, -1, 3, 1, 5, 9]  
> with $i = 4$  
> mcs $= 8 \to (3, -1, 6)$  

> **Note:** MCS ending at index 0 is just A[0]  
> **Note:** MCS ending at index $i$ is: $max(A[i], A[i] +$ mcs ending at index $i - 1)$

>[!example]- More Complex Example
> A = [1, -10, 5, 2, -8, 2, ...]  
> B = [1, -10, 4, -1, 5, 2, ...]   
> $i = 5$  
>For A, the mcs at $i$ is just 2, for B the mcs is 10

**Overall:** MSC = max(mcs ending at all i)

```python
# PRE: A is a list of length n
maxoverall = A[0]
maxendingati = A[0]
for i = 1 to n - 1
    maxendingati = max(maxedningati+A[i],A[i])
    maxoverall = max(maxoverall, maxendingatai)
end
# POST: maxoverall is the maximum contiguous sum.
```

Time Complexity: $\theta(n)$
