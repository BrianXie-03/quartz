---
title: Time Complexity
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

>[!Question]- Example 4
> **Prove:**  $x^2lg(x) + \frac{100}{x^2} = O(x^3)$  
> **Scratch:** $x^2lg(x) \le x^2(x) = x^3$  
> **Need:** $\frac{100}{x^2}$  
> **Obeserve:**  $\frac{100}{x^2} \le x^3$ when $x =  \sqrt[5]100 \le x^5$, that is if $x \ge 100^(1/5)$  
> **Proof:** if $ x \ge 100^(1/5)$ then: $100/x^2 \le x^3$ and so:  
> $x^2lg(x) + \frac{100}{x^2} \le x^2(x) + x^3 = 2x^3$  
> So defintion is satisfied w/ $x_0 = 100^(1/5)$ and $C = 2$

# Big-Omega

**Definition:** We write $f(x) = \Omega (g(x))$ when $\exists x_0, \exists B \gt 0$, such that if $x_0$ then $f(x) \ge Bg(x)$
> Note: This provides a lower bound

>[!example]- Example One
> **Show** $3nlg(n) - n + 1 = \Omega (nlg(n))$  
> **Scratch:** want $3nlg(n) - n + 1 \ge \Omega (nlg(n))$  
> $3nlg(n) - n + 1 \ge 3nlg(n) - n$  
> Note: $ n \le nlg(n)$ when $lg(n) \ge 1$ when $n \ge 2$    
> In which case: $3nlg(n)-n \ge 3nlg(n) - nlgn(n) \ge 2nlg(n)$  
> **Proof:** Observe if $n \ge 2$ then:  
> $3nlg(n) - n + 1 \ge 3nlg(n) - n \ge 3nlg(n) - nlg(n) = 2nlg(n)$  
> The definition is satisfied with $n_0$ = 2 and B = 2

>[!example]+ Example Two
> **Show:** $n^2 - n = \Omega(n^2)$  
> **Scratch:** $n \le n^2$ when $n \ge 1$  
> $n^2 = n \ge n^2 - n^2 = 0$ is not possible because we need $Bn^2$ with $B \gt 0$  
>**Instead:** $n \le \frac{1}{2} n^2$ when $ 2 \le n$  
> In which case $n^2 - n \ge n^2 - \frac{1}{2} n^2 = \frac{1}{2} n^2$  
> **Proof:** observe if $n \ge 2$ then,  
> $n^2 - n \ge n^2 - \frac{1}{2} n^2 = \frac{1}{2} n^2$  
> The definition is satisfied with $n_0 = 2$ and $B = \frac{1}{2}$
>> **Note:** not unique. Note we could have done $n \le \frac{1}{3} n^2$ when $n \ge 3$ and then $n^2 - n \ge n^2 - \frac{1}{3}n^2 = \frac{2}{3}n^2$

# Big-Theta

**Definition:** We write $f(x) = \theta (g(x))$ when $\exists x_0, \exists B, c \gt 0$ such that if $x \ge x_0$ then $Bg(x) \ge f(x) \ge Cg(x)$

> Note knowing $\theta$ is the best! It provides the most information

# Limit Theorems:


Suppose we have two functions $f(x)$ and $g(x)$. Then suppose $\displaystyle \lim_{x \to \infty} f(x)$ and $\displaystyle \lim_{x \to \infty} g(x)$ exist (may be $\infty$)

Then we have

(A) if lim \frac{f(x)}{g(x)} != \infinity then f(x) = O(g(x))
(B) if lim \frac{f(x)}{g(x)} != 0 then f(x) = \Omega (g(x))
(c) if lim \frac{f(x)}{g(x)} != 0, != \infinity then f(x) = \theta (g(x))

>[!example]- Example One
>**Show** $x^2-1 = \theta (x^2)$  
>**Proof** lim \frac{x^2-1}{x^2} (x to infinity) = lim \frac{x^2/2 - \frac{1}{x^2} (x to infinity) = lim ( 1 - \frac{1/x^2} (x to infinity) = 1 so done.

>[!example]+ Example Two
>**Show** n^{10} = O(2^n)
>**Proof:** well lim \frac{n^10}{2^n} (n to infinity) we see \frac{\inf}{\inf} thus we do L'Hopital
> lim \frac{10n^9}{ln(2)2^n} (do it again)
> lim \frac{90n^8}{ln(2)ln(2)2^n) {see that top shrinks but bottom doesnt...
> we get lim \frac{10!}{ln2}^{10}2*n} = 0, so done


closing notes
(a) common functions
it is true for ex that x^2 = \theta(x^2 + 2x + 1)
but typically, we have f(x) = \theta(nice funcction) (or 0 or \Omega)
where "nice" functions are things like the following given in increasing order,
1, lgx, x, xlgx, x^2, x^2lgx ... all x^nlgx, 2^x, 3^x, ..., x!, ...

#### Intuition

When a function is made up of 'nice' functions, it's the "biggest" which is the most important. The entire function would be $\theta$ (biggest)

> $3n^2 + 7n^2lg(n) - n + 1 = $  
> We see that $n^2lg(n)$is the largest "nice" function

> $1 - n + 8n^2 + 2nlg(n) = \theta (n^2)$

**Note:** if you have functions not in the list, all bets are off! Think outside of the box

> $2 + sin(x) =$  
> Keep in mind that sin(x) ranges between -1 to 1 thus we can see that
> $ 1 \le 2 + sin(x) \le 3 $  
> thus $2 + sin(x) = \theta (1)$

>$x(2+sin(x))$
>$1\le x(2+sin(x)) \le 3$
>$x \le 2+sin(x) \le 3x$  
> thus $x(2+sin(x)) = \theta(x)$

Dont forget
$ \theta$ means both O and $\omega$
So if $f(x) = \theta(g(x))$ then it's guaranteed that $f(x) = O(g(x))$ and $f(x) = \Omega(g(x))$

> Q: if $f(x) = O(g(x))$ then $f(x) = \theta(g(x))$  
> A: This is not guanteed to be true

> Q: if $f(x) \ne O(g(x))$ then $f(x) = \Omega(g(x))$  
> A: This is not guaranteed to be true