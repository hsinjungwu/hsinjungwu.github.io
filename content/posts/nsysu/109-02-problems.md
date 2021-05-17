---
title: "雙週一題 109-02"
date: 2021-03-23T10:20:00+08:00
draft: false
dropCap: false
categories: 
    - "中山大學雙週一題"
---

[109學年度第二學期問題及解答](http://www.math.nsysu.edu.tw/~problem/2021s/1092Q&A.htm)

<!--more-->

## Q1 ✔

$f(x)$ 為實數函數，若 $f(0) = 1013$，且對任意 $x\in\mathbb{R}$ 滿足
<div>
$$f(x + 5) − f(x)\leq 3(x + 3), f(x + 15) − f(x)\geq 9(x + 8)$$
</div>
則 $\frac{f(2025)}{2026} =?$

> 利用 [裂項求和(Telescoping sum)](https://zh.wikipedia.org/wiki/%E8%A3%82%E9%A0%85%E5%92%8C) 就可以了。總之答案是 608。

## Q2 ✔

設 $\mathcal{S}$ 是由正整數所組成的集合，裡面元素為 "後五位數字為 20210，且其後五位數被刪除後的數字仍可整除該數" 的正整數(例如 520210 刪除 20210 後的 520210 可被 5 整除)，求 $\mathcal{S}$ 裡面所有元素之位數總和(例如 520210 為 5 + 2 + 0 + 2 + 1 + 0 = 10)

> 根據題意知道這些數字為這種形式 $n\times100000+20210$ 且滿足 $n\mid20210$，所以 $n$ 為以下 16 個數字：
> <div>
> $$
> 1,2,5,43,47,10,86,94,215,235,2021,430,470,4042,10105,20210
> $$
> </div>
> 所以答案為 $(1+2+5+7+11+1+14+13+8+10+5+7+11+10+7+5)+16\times 5=197.$

## Q3 ✔

一個圓心為 $O$ 半徑為 65 的圓。已知弦 $\overline{AB}$ 長為 32 與弦 $\overline{CD}$ 長為 66 相交於 $P$ 點，且兩弦中點的距離為 39，求 $\overline{OP}$。

> 假設 $\overline{AB}$ 與 $\overline{CD}$ 中點分別為 $M$ 與 $N$，可以知道 $\angle{OMP} = \angle{ONP} = 90^\circ$ 因此 $MONP$ 為圓內接四邊形
> 
> 接著先做以下假設 $\overline{OM}, \overline{MP}, \overline{PN}, \overline{NO}$ 以及對角線 $\overline{OP}, \overline{MN}$ 的長度分別為 $b,x,y,a,z,c$。
> 
> 根據 [托勒密定理](https://zh.wikipedia.org/wiki/%E6%89%98%E5%8B%92%E5%AF%86%E5%AE%9A%E7%90%86) 以及 [畢氏定理](https://zh.wikipedia.org/wiki/%E5%8B%BE%E8%82%A1%E5%AE%9A%E7%90%86) 有
> 
> <div>
> $$
> \begin{aligned}
> cz &= ax+by\\
> z^2 &= b^2 + x^2\\
> z^2 &= a^2 + y^2
> \end{aligned}
> $$
> </div>
> 
> 再把這三個方程式整理一下可以得到
> 
> <div>
> $$
> (a+b-c)(a+b+c)(c+a-b)(c-a+b)z^2 = (2abc)^2
> $$
> </div>
> 
> 又根據題目給的資料可知 $a=56, b=63, c=39$，代入即可得到 $z=\frac{17199}{2\sqrt{18170}}$

## Q4 ✔

在 $1, 2, 3, \cdots, 2021$ 的直線排列 $(a_1, a_2, \cdots, a_{2021})$ 中，滿足條件 $(∗)$ 的排列共有多少
個？

(∗) : 恰有一個 $i\in \{1, 2, 3, \cdots, 2020\}$，使得下面的式子成立。

<div>
$$
\begin{equation*}
\left\{
    \begin{array}{l}
    a_1 < a_2 < \cdots < a_i\\
    a_i > a_{i+1}\\
    a_{i+1} < a_{i+2} < \cdots < a_{2021}
    \end{array}
\right.
\end{equation*}
$$
</div>

> 根據 $1, 2, 3, \cdots, n$ 定義條件為 $C_n$ 且滿足條件的個數為 $V_n$，則 $V_1 = 0$。又滿足 $C_n$ 的集合可以用兩種方式建構：
> 1. 先拿出滿足 $C_{n-1}$ 的集合，然後讓 $n = a_n$。
> 2. $n$ 就是那個轉折點 $a_i$
>
> 所以 $V_n = V_{n-1} + 2^{n-1}-1$
>
> 再次利用 [裂項求和(Telescoping sum)](https://zh.wikipedia.org/wiki/%E8%A3%82%E9%A0%85%E5%92%8C) 可以得到 $V_n = 2^n-n-1$，因此答案為 $2^{2001}-2002$

## Q5 ✔

如圖，已知一個直角三角形 $\triangle ABC$，$\overline{BC}$ 為斜邊，斜邊長為 $a$，斜邊上的高為 $h$，$O$
為斜邊上的中點，今將斜邊 $n$ ($n > 1$, $n$ 為奇數) 等分，若 $P, Q$ 為其中兩個等分點，且 $\overline{PQ} =
\frac{a}{n}$，$O$ 點介於 $P$, $Q$ 之間，設 $\angle PAQ = \alpha$，求 $\lim\limits_{n\to\infty}n\tan\alpha$。

> 令 $\overline{OH} = k$， 可知 $h^2+k^2=\frac{a^2}{4}$。
>
> 再令 $\angle QAH=\beta, \angle PAH=\gamma$，則根據和角公式可以得到
>
> <div>
> $$
> \tan(\alpha) = \tan(\beta-\gamma) = \frac{\tan(\beta)-\tan(\gamma)}{1-\tan(\beta)\tan(\gamma)}
> $$
> </div>
>
> 又 $\tan(\beta) = \frac{k+\frac{a}{4n}}{h}$ 以及 $\tan(\gamma) = \frac{k-\frac{a}{4n}}{h}$
>
> 因此帶入可得到
>
> <div>
> $$
> \lim\limits_{n\to\infty}n\tan\alpha = \frac{4h}{a}
> $$
> </div>

## Q6 
今一單位球(半徑為 1 的球)球心為原點，且球面上兩點 $P、Q$ 座標分別為 $P(1, 0, 0),
Q(−\frac{1}{2}, \frac{3}{4}, \frac{\sqrt{3}}{4})$，延著球面行進，於 $PQ$ 最短路徑中取一點 $R$，使得
$\overset{\frown}{PR} : \overset{\frown}{QR} = 1 : 3$，試求 $R$ 點座標。

> 由 $\cos{\theta} = \frac{\mathbf{a \cdot b}}{|\vec{a}| \, |\vec{b}|}$ 可以得知 $\angle POQ = 120^{\circ}$。
>
> 因為 $\overset{\frown}{PR} : \overset{\frown}{QR} = 1 : 3$ 則
> <div>
> $$
> \begin{aligned}
> \left \langle \vec{OP}, \vec{OR} \right \rangle &= \cos30^{\circ}\\
> \left \langle \vec{OQ}, \vec{OR} \right \rangle &= \cos90^{\circ}
> \end{aligned}
> $$
> </div>
>
> 令 $R = (x,y,z)$，因此
> <div>
> $$
> \begin{aligned}
> x^2 + y^2 + z^2 &= 1\\
> x &= \frac{\sqrt{3}}{2}\\
> \frac{-1}{2}x+\frac{3}{4}y+\frac{\sqrt{3}}{4}z &=0
> \end{aligned}
> $$
> </div>
> 所以 $R=(\frac{\sqrt{3}}{2}, \frac{\sqrt{3}}{4}, \frac{1}{4})$