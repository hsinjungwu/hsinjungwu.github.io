---
title: "[還債] Elementary Classical Analysis Ch-2(26)"
date: 2023-01-30T00:30:00+08:00
draft: false
dropCap: false
tags:
  - "Math"
---

在 **2003/12/23 02:11:27** 於未來最舊小棧留下的習題，終於解了。

## 題目

Define the sequence if numbers $a_n$ by 

$$
a_0 = 1, a_1 = 1 + \frac{1}{1+a_0}, \cdots, a_n = 1 + \frac{1}{1+a_{n-1}}
$$

Show that $a_n$ is convergent sequence. Find the limit.

## 證明

Let $A_0 = a_0$ and $A_n= a_n - a_{n-1}$, then 

$$
\frac{A_n}{A_{n-1}} = \frac{-1}{(1+a_{n-1})(1+a_{n-2})}
$$

It's easy to see that $a_i\geq 1$, then $|A_n|\leq \frac{|A_{n-1}|}{4}$.

So $A_n$ is an alternating series with decreases monotonically and limit is 0.

By [alternating series test](https://en.wikipedia.org/wiki/Alternating_series_test), we have $a_n = \sum\limits_{i=0}^{n} A_n$ converges.

It's easy to check $\lim\limits_{n\to\infty}a_n = \sqrt{2}.$

## 後記

當年沒有看出 $|A_n|\leq \frac{|A_{n-1}|}{4}$ 所以證不出 limit is 0。