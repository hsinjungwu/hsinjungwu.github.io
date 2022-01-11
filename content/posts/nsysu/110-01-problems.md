---
title: "雙週一題 110-01"
date: 2021-09-30T02:13:00+08:00
draft: false
dropCap: false
categories:
  - "中山大學雙週一題"
---

[110 學年度第一學期問題及解答](http://www.math.nsysu.edu.tw/~problem/2021f/1101Q&A.htm)

<!--more-->

## Q1 ✔

下列方程組

<div>
$$
\left\{
    \begin{aligned}
        x + y &= 3(z + u)\\
        x + z &= 5(y + u)\\
        x + u &= 7(y + z)
    \end{aligned}
\right.
$$
</div>
的解 $(x, y, z, u)$，其中 $x、y、z、u$ 皆為正整數，求 $x$ 可能的最小值為何？

> 暴力解：可得 $x:y:z:u = 35:1:5:7$，所以 $x$ 最小值為 $35$。

## Q2 ✔

設 $x, y\in \mathbb{R}$，求 $\sqrt{x^2+y^2-6x+4y+17} + \sqrt{x^2+y^2+6x-8y+50}$ 的最小值。

> 找出空間一點 $(x,y,0)$ 與 $(3,-2,\pm2)$ 跟 $(-3,-4,\pm5)$ 的距離和最短。經過一番簡單計算可以得到 $(x,y)=(\frac{9}{7},\frac{-2}{7})$ 有最小值 $11$。

## Q3 ✔

設 $\frac{1}{2a}+\frac{1}{3b}=30$，其中 $a, b$ 為正數，求 $3\log_{\frac{1}{6}}a+2\log_{\frac{1}{6}}b$ 的最大值。

> 因為 $180 = \frac{3}{a} + \frac{2}{b} \geq 5\sqrt[5]{\frac{1}{a^3b^2}}$，所以 $a^3b^2 \leq{\frac{1}{6}}^{10}$。又題目所求原式可寫成 $\log_{\frac{1}{6}}{a^3b^2}$ 所以答案為 $10.$

## Q4 ✔

如下圖，大圓的半徑為 $10$，小圓的半徑為 $4$，$A$ 在大圓的圓周上且為小圓的圓心，$\overline{BC}$ 為大圓的弦且與小圓相切。若 $\overline{AB} = 16$ ，則 $\overline{AC}$ =？

![NSYSU-110-01-Q4](https://i.imgur.com/bwW3rYy.png)

> 令大圓圓心為 $O$，點 $A$ 到 $\overline{BC}$ 的垂足為 $M$。設圓周角 $\angle{ABC}=\theta$，則圓心角 $\angle{AOC}=2\theta$。
>
> 從 $\triangle ABM$ 可得 $\sin\theta = \frac{1}{4}$。而從 $\triangle ACO$ 可得 $\cos 2\theta = \frac{200-\overline{AC}^2}{200}=1-\frac{\overline{AC}^2}{200}$。
>
> 於是由兩倍角公式可得到 $\overline{AC} = 5$

## Q5 ✔

將一個圓分成 $12$ 個相等的扇形，並用紅藍綠三種顏色塗上顏色，相鄰的扇形顏色不同，則有幾種塗色方法？(註：不考慮旋轉的情形)

> 將題目考慮分成 $n\ge2$ 個扇形且編號為 $1$ ~ $n$。令有效的塗色方法為 $C(n)$。則編號為 $1$ 與 $n-1$ 同色的情況等價於 $C(n-2)$。異色則是等價於 $C(n-1)$。因此可以得到
>
> <div>
> $$
> C(n) = C(n-1)+2\times C(n-2)
> $$
> </div>
>
> 又 $C(2) = C(3) = 6$，所以 $C(12) = 4098$。

## Q6 ✔

試求函數 $f(x)$，對任意實數 $x$，$\lvert x\rvert\neq 1$，滿足 $f(\frac{x-3}{x+1})+f(\frac{3+x}{1-x}) = x$

> 令 $y=\frac{x-3}{x+1}$ 可得 $f(y)+f(\frac{y-3}{1+y})=\frac{y+3}{1-y}$，即
>
> <div>
> $$
> f(x)+f(\frac{x-3}{1+x})=\frac{x+3}{1-x}
> $$
> </div>
>
> 同理，令 $y=\frac{3+x}{1-x}$ 亦有
>
> <div>
> $$
> f(x)+f(\frac{x+3}{1-x})=\frac{x-3}{1+x}
> $$
> </div>
>
> 又 $f(\frac{x-3}{x+1})+f(\frac{3+x}{1-x}) = x$，所以兩式相加得到答案 $f(x) = \frac{4x}{1-x^2}-\frac{x}{2}$。

## Q8 ✔

有 $C_1、C_2、\cdots、C_n$ 共 $n$ 個硬幣。對每個 $k$，$C_k$ 是不公正的硬幣，且 $C_k$ 有 $\frac{1}{2k+1}$ 的機率投擲出正面。如果投擲 $n$ 個硬幣，出現奇數次正面的機率是多少？答案請以 $n$ 表示成一個有理函數。

> 假設出現正面機率為 $P(n)$ 則有
>
> <div>
> $$
> P_n = P_{n-1}\times\frac{2n}{2n+1} + (1-P_{n-1})\times\frac{1}{2n+1}
> $$
> </div>
>
> 整理一下可得 $(2n+1)P_n=(2n-1)P_{n-1}+1$。
>
> 接著再利用遞迴得到 $(2n+1)P_n=3P_{1}+n-1=n$ 所以 $P_n=\frac{n}{2n+1}$
