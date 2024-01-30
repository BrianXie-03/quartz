---
title: Big-O Notation
tags:
- cmsc351
- wip
- need review
---

# Fundamentals

Suppose we have two algorithms  
* A1 takes time $5n$  
* A2 takes time $n^2$

**Note:** In the case where $n$ increases, we see that at first A1 takes more time, but after a certain point ($x_0 = 5$), A2 will take longer.

# Big-0

We are interested in the following: given a function $f(x)$, is there some cutoff for x ($x_0$) after which $f(x)$ is guranteed to be $\le$ some other function?

We find an $f(x)$ and $g(x)$, defined for x $\ge$ 0, where: $f(x) = O(g(x))$

>$\exists C \le 0$, $\exists x_0$ such that if $x\ge x_0$, then $f(x) \le Cg(x)$  
>>i.e. At $x= x_0$ and beyond $f(x) \le Cg(x)$

**Note:** The cutoff is when the we find the beginning of where the function stands true to the previous definition.

>[!Question]- Example 1
>**Prove:** $x^2 = O(x^2)$  
>**Observe:** $x^2 - 1 \le 1*x^2$ for all x $\ge$ 0.  
>**Solution:** We're satisfied the definition with $C=1$ and $x_0 = 0$    
>**Note:** It's also the case that $x^2 - 1 = O(x^3)$ because $x^2 - 1 \le 1x^3$ for all $x \le 0$. However $0(x^2)$ is *better* in the sense that we prefer "smaller" functions.  
>>**Note:** Technically $O(x^2)$ is a set of functions and we should note $x^2 - 1 \in O(x^2)$, but it is unnecessary

>[!Question]- Example 2
>**Prove:** $2x^2 + 1 = O(x^2)$  
>**Scratch:** Need $2x^2 + 1 \le ... \le cx^2$  
>**Observe:** $1 \le x$ when $x \ge 1$  
>**Proof:** if $x \ge 1$ then $x^2 \ge 1$ and so $2x^2 + 1 \le 2x^2 + x^2 = 3x^2$  
>**Solution:** So definition is satisfied with $x_0 = 1$ and $c = 3$

>[!Question]- Example 3
> **Prove:** $4x^2 + xlg(x) - 1 = O(x^2)$  
> **Scratch:** need $4x^2 + xlg(x) - 1 \le ... \le cx^2$  
> **Scratch:**  $4x^2 + xlg(x) -1 \le 4x^2 + xlg(x)$ always  
> **Fact:** $lg(x) \lt x$ for all $x \gt 0$  
>**Together:** $4x^2 + xlg(x) - 1 \le 4x^2 + xlg(x) \le 4x^2 + x(x)$  
> **Proof:** if $x \gt 0$ then we have $4x^2 + xlg(x) - 1 \le 4x^2 xlg(x) \le 4x^2 + x(x) = 5x^2$  
So defintion is satisfied with $x_0 = 1$ and $C = 5$  
>>**Note:** We can't use $x_0 = 0$ because $lg(0)$ is undefined.

>[!Question]+ Example 4
> **Prove:**  $x^2lg(x) + \frac{100}{x^2} = O(x^3)$  
> **Scratch:** $x^2lg(x) \le x^2(x) = x^3$  
> **Need:** $\frac{100}{x^2}$  
> **Obeserve:**  $\frac{100}{x^2} \le x^3$ when $x =  \sqrt[5]100 \le x^5$, that is if $x \ge 100^(1/5)$
> Proof: if $ x \ge 100^(1/5)$ then: $100/x^2 \le x^3$ and so:
> $x^2lg(x) + \frac{100}{x^2} \le x^2(x) + x^3 = 2x^3$
> So defintion is satisfied w/ $x_0 = 100^(1/5)$ and $C = 2$