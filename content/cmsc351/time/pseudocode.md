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