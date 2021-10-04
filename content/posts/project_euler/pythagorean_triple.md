---
title: "畢氏三元數"
date: 2021-05-20T02:13:00+08:00
draft: false
dropCap: false
categories:
  - "Project Euler"
---

在 [Project Euler](https://projecteuler.net/) 中偶爾會遇到 [畢氏三元數](https://en.wikipedia.org/wiki/Pythagorean_triple)，才知道原來跟它不是很熟啊！ 😣

<!--more-->

解題時通常會將 $a^2+b^2=c^2$ 的 $a,b,c$ 轉成兩個正整數 $m>n$ 以下列方式表示：

<div>
$$
\begin{align*}
a &= m^2-n^2\\
b &= 2mn\\
c &= m^2+n^2
\end{align*}
$$
</div>

---

裡面有一題有提到一個有趣的性質[^1]

> 如果 $c$ 也是一個正整數 $k$ 的平方，那三角形面積必定是 7 的倍數

證明如下：

因為 $c=k^2$ 且 $c=m^2+n^2$, 可以得到另一組 $(m,n,k)$ 滿足畢氏定理。因此依樣畫葫蘆可以用正整數 $x>y$ 來建構出 $m, n, k$。

<div>
$$
\begin{align*}
m &= x^2-y^2\\
n &= 2xy\\
k &= x^2+y^2
\end{align*}
$$
</div>

然後不要動腦，用暴力法列出所有情況就可以得到結論了。 😛

[^1]: 不影響解題樂趣，有調整內容敘述。
