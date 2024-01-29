---
title: Big-O Notation
tags:
- cmsc351
- wip
- need review
---

# Fundamentals

Here are some ideas to consider: suppose we have two algoritms  
* A1 takes time $5n$  
* A2 takes time $n^2$

**Note:** We are able to see that as n increases, the time it takes for A2 becomes much higher than A1, but near the smaller values of n A1 actually takes more time than A2 (n = 5).

However, we will almost never come up with explicit (exact) time or memory (or whatever) functions.

# Big-O Notation

Informally, we're interested in the following:
* Given a function $f(x)$, is there some cutoff for x after which $f(x)$ is guranteed to be $\le$ some other function?

Formally: Given functions $f(x)$ and $g(x)$, defined for x $\ge$ 0, we say:  
$f(x) = O(g(x))$

$\exists C \le 0$, $\exists x_0 st. if x\ge x0, then f(x) \le Cg(x)$

i.e. At x= x0 and beyond $f(x) \le Cg(x)$

**Note:** the cutoff is when the wew find the beginning of where the function stands true.

>[!Question]- Example 1
>$x^2 = O(x^2)$  
>**Observe:** $x^2 - 1 \le 1x^2$ for all x $\ge$ 0.
>We're satisfied the defn. w/ $C=1$ and $x_0 = 0$  
>**Note:** it's also the case that $x^2 - 1 = O(x^3)$ because $x^2 - 1 \le 1x^3$ for all $x \le 0$. However $0(x^2)$ is "better" in the sense that we prefer "smaller" fctns.
>**Note:** Technically $O(x^2)$ is a set of fctns and we should note $x^2 - 1 \in O(x^2)$, but we don't!

>[!Question]- Example 2
>Show that $2x^2 + 1 = O(x^2)$  
>Scratch: Need $2x^2 + 1 \le ... \le cx^2$
>Observe that $1 \le x$ when $x \ge 1$  
>So observe
>**Proof:** if $x \ge 1$ then $x^2 \ge 1$ and so $2x^2 + 1 \le 2x^2 + x^2 = 3x^2$  
>So definition is satisfied with $x_0 = 1$ and $c = 3$

>[!Question]- Example 3
> Show $4x^2 + xlg(x) - 1 = O(x^2)$  
> Scratch: need $(4x^2 + xlg(x) - 1 \le ... \le cx^2$  
> Know $4x^2 + xlg(x) -1 \le 4x^2 + xlg(x)$ always
> Fact: $lg(x) \lt x$ for all $x \gt 0$  
> Together: $4x^2 + xlg(x) - 1 \le 4x^2 + xlg(x) \le 4x^2 + x(x)$
> Proof: if $x \gt 0$ then we have $4x^2 + xlg(x) - 1 \le 4x^2 xlg(x) \le 4x^2 + x(x) = 5x^2$  
So defintion is satisfied with $x_0 = 1$ and $C = 5$
>>**Note:** We can't use $x0 = 0$ because $lg(0)$ is undefined. Any larger value works

[!Question]+ Example 4
> Show $x^2lg(x) + \frac{100}{x^2} = O(x^3)$  
> Scratch: $x^2lg(x) \le x^2(x) = x^3$  
> How about $\frac{100}{x^2}$? Want $\frac{100}{x^2}$ too!  
> Is it true that $\frac{100}{x^2} \le x^3$

> well, that's $ 100 \le x^5$, that is if $x \ge 100^(1/5)$
> Proof: if $ x \ge 100^(1/5)$ then: $100/x^2 \le x^3$ and so:
> $x^2lg(x) + \frac{100}{x^2} \le x^2(x) + x^3 = 2x^3$
> So defintion is satisfied w/ $x_0 = 100^(1/5)$ and $C = 2$