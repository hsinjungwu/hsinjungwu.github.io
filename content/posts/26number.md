---
title: "在平方數跟立方數中求生存的數字"
date: 2020-08-14T10:20:00+08:00
draft: false
dropCap: false
categories:
    - "Math"
tags:
    - "Number Theorey"

---

26 實在是個很有趣的數字啊！

<!--more-->

## 題目

$x, y \in\mathbb{N},$ find all $x, y$ such that $x^3 = y^2+2$

這題的解法可以參考這篇 [The number 26, between 25 and 27 Resolution of the diophantine equation y^3 − x^2 = 2](https://www.normalesup.org/~baglio/maths/26number.pdf)

不過我自己也想了一個比較基礎的解法，證明答案只有 $x,y = (3,5)$。 :smile:

## 解法

1. 容易得知 $y \ne 1$ 
2. 又 $y^3-y^2 = y^{2}(y-1) > 2, \forall y > 1$，所以 $x^3 = y^2+2 < y^3, y>1 $。因此可以假設 $y=x+k, k\in\mathbb{N}$，即 $x^3 = (x+k)^2+2$
3. 考慮以下情況，然後討論就可以了
    + $x > k$
    + $x \leq k$

### Case 1

$$
\begin{aligned}
&(x+k)^2+2=x^3 \geq (k+1)x^2\\
\implies &2kx+k^2+2 \geq kx^2\\
\implies &2 \geq k(x^2-2x-k)
\end{aligned}
$$

因為 $1\leq k < x\in \mathbb{N}$，從上面的式子看來可以得到

+ 若 $x^2-2x-k\leq 0$，則 $x^2-2x+1 \leq k+1 \leq x$，即 $x^2-3x+1 \leq 0$。整理一下可以得到 $x,k = (2,1)$，但這個答案不對。
+ 反之， $k$ 被限縮在 $1, 2$，整理一下可得正整數解 $x,k = (3,2)$，$x,y = (3,5)$。

### Case 2

$$
\begin{aligned}
&(x+x)^2 < (x+k)^2+2\\
\implies &3x^2-2kx-k^2 < 2\\
\implies &(3x+k)(x-k)< 2
\end{aligned}
$$

但 $3x+k > 2$，所以 $x=k$。但這導致 $x^3 = 4x^2+2$，然而沒有一個整數的三次方 mod 4 會餘 2，所以這個情形下無解。