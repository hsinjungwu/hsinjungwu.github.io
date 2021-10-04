---
title: "看到的一題"
date: 2020-10-01T03:14:00+08:00
draft: false
dropCap: false
categories:
  - "Math"
---

Given $a > 0, a\neq 1$, $\forall n \in \mathbb{N}$, we have

$$
\frac{1+a^2+a^4+\cdots + a^{2n}}{a+a^3+\cdots+a^{2n-1}} > \frac{n+1}{n}
$$

<!--more-->

---

First of all, I give a lemma

Given integers $p, q$ where $ p > q\geq 0$, $\forall a > 0$, we have $a^p + a^q \geq a^{p-1} + a^{q+1} $

Sketch : If $a = 1$ trivial. Otherwise it is easy to see that $a-1$ and $a^{p-1}-a^q$ have the same sign.

note ： equality holds if and only if $a=1$

---

Next step, it is also easy to check

<div>
$$
\begin{aligned}
&\frac{1+a^2+a^4+\cdots + a^{2n}}{a+a^3+\cdots+a^{2n-1}}\\\\
= &\frac{(1+a^2+a^4+\cdots+a^{2n})(1+a)}{(a+a^3+\cdots+a^{2n-1})(1+a)}\\\\
= &\frac{1+a+a^2+\cdots + a^{2n+1}}{a+a^2+\cdots+a^{2n}}\\\\
= &1 + \frac{1+a^{2n+1}}{a+a^2+\cdots+a^{2n}}
\end{aligned}
$$
</div>

then we can change our problem to show

$$
\frac{1+a^{2n+1}}{a+a^2+\cdots+a^{2n}} > \frac{1}{n}
$$

that is

$$
\frac{a+a^2+\cdots+a^{2n}}{1+a^{2n+1}} < n
$$

So by our lemma, we have

$$
1+a^{2n+1} > a^1+a^{2n} > \cdots > a^i+a^{2n+1-i} > \cdots > a^n+a^{n+1}
$$

that means

$$
\frac{a^i+a^{2n+1-i}}{1+a^{2n+1}} < 1, \forall 1\leq i\leq n
$$

Hence we complete the proof.
