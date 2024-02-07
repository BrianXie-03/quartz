---
title: Pseudocode
tags:
- cmsc351
- wip
---

Q: When looking at pseudocode + analyzing time, what do we need to care about

```
sum = 0				#c1
for i = 1 to n (inclusive)	#c2 per iteration
    sum = sum + i		#c3
end for				#included in c2
```
$ T(n) = c_1 + nc_2 = nc_3$

if we care about exact time, we need **all** of these.

If we want $\Omega$, $O$, or $\theta$ we can ignore some stuff
(A) Provided the body of the loop takes any time at all, we can ignore loop maintenance lines: $c_2$ in above can eb ignored

$T(n) = c_1 + nc_3 = \theta(n)$ still

howeever if we had
```
for i = 1 to n
    #comment takes no time
end for
```
we will have to pay attention to the maintenance lines even though the body takes no time

$T(n) = \theta(n)$
Any constant time code which is adjacent code which takes any time at all can be ignored

$c_1$ is unecessary, thus we get  
$T(n) = nc_3 = \theta(n)$

**Conditionals:** conditionals do take time, even if thy are false. However the overall time might depend on whether it's true for false
```
if n > 10
   print("hi")
end if
```
$T(n) = \theta(1)$

the $if$ certainly takes time, even if false

```
if x < y
   for i=1 to n:
       print("friday")
   end for
end if
```

Here, if x $\le$ y then the body runs, takes c-time per iteration for an overall linear result, and if x $\ge$ y then just the conditional check happens (constant time)  
**Thus:** if $T(n) = $ time it takes to run (we don't know x,y):  
$T(n) = O(n)$ and $T(n) = \omega(1)$ so $T(n) = \Omega$(nothing works here)


# Best, worst, average case

suppose our algorithm has input of size n
we don't get to specify n but we can still ask the following:
* How fast could this code run
* How slow can this code run
* On average how fast/slow can this code run

```
A = list of length n
i = 0
while i < n and A[i] != 0
      print("cmsc")
      i++	
end while
```
in the best case, A[0] = 0 and the body of the while loop does not run  
$T(n) = \theta(1)$
in the worst case A[i] $\ne$ 0 for all i. Then
$T(n) = \theta(n)$
Average Case: Difficult because it's frequently difficult to define what "average" means 