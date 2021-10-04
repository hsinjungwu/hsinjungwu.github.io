---
title: "雙週一題 108-02"
date: 2020-08-26T10:20:00+08:00
draft: false
dropCap: false
categories:
  - "中山大學雙週一題"
---

[108 學年度第二學期問題及解答](http://www.math.nsysu.edu.tw/~problem/2020s/1082Q&A.htm)，我只解到第 6 題。 😓

<!--more-->

## Q1 ✔

假設 <span>$n$</span> 是一個最小正整數，其為 3 與 4 的倍數，在十進位中，<span>$n$</span> 出現的數字只有 3 及 4 且各數字至少一個。請問：<span>$n$</span> 值為何？

> 因為 <span>$n$</span> 是 3 的倍數，且數字中必須有 3 跟 4，所以最少要 1 個 3 與 3 個 4。又 3444 為此種情形下的最小解，故 <span>$n = 3444$</span>。

## Q2 ✔

袋中有編號 <span>$1, 2, 3, \dots, 90$</span> 號的球各一個，設每一球被取到的機會相等，今由袋中一次任取一球，每次取完後均放回袋中再取。令 <span>$a_n$</span> 表取完 <span>$n$</span> 次後所取球號總和為 4 的倍數的機率，求 <span>$a_4$</span>。

> 暴力解法：
>
> - 法 1：每次選擇都有 4 種情況，全部列出並加總找出 4 的倍數即可
> - 法 2：計算每次取完為除 4 餘 0~3 的組合，並用馬可夫鍊去算。
>
> 答案為 0.249999969516842。

## Q3 ✔

已知正整數中前 <span>$m$</span> 個正奇數和比前 <span>$n$</span> 個正偶數和大 2020。請問：所有可能的 <span>$n$</span> 之和為何？

> 前 <span>$m$</span> 個正奇數和 = <span>$m^2$</span>，前 <span>$n$</span> 正偶數和 = <span>$n(n+1)$</span>。所以整理一下可以得到
>
> <div>
> $$
> (2m+2n+1)(2m-2n-1) = 8079 = 2693\times3 = 8079\times1
> $$
> </div>
>
> 因為 <span>$m,n$</span> 皆為整數，可得 <span>$(m,n) = (674,672) = (2020,2019)$</span>，所以答案為 <span>$2691.$</span>

## Q4 ✔

設兩矩陣 <span>$\bf{P, Q}$</span> 滿足

<div>
$$
\left\{
  \begin{array}{c}
    7{\bf P}+8{\bf Q} = {\bf A}\\ 
    {\bf P}+{\bf Q} = {\bf I_2}
  \end{array}
\right.
$$
</div>

，其中

<div>
$$
{\bf A} = \begin{bmatrix}
  11 & -3 \\
  4 & 4 
\end{bmatrix},
{\bf I_2} = \begin{bmatrix}
  1 & 0 \\
  0 & 1 
\end{bmatrix},
$$
</div>

若 <span>${\bf A^{21}} = a{\bf P} + b{\bf Q}$</span>，求 <span>$(a, b)$</span>。

> 易解出
>
> <div>
> $$
> {\bf P} = \begin{bmatrix}
>   -3 & 3 \\
>   -4 & 4 
> \end{bmatrix},
> {\bf Q} = \begin{bmatrix}
>   4 & -3 \\
>   -3 & 4 
> \end{bmatrix},
> $$
> </div>
>
> 且容易得出 <span>${\bf P^2 = P, Q^2 = Q, PQ=O_2}$</span>，其中
>
> <div>
> $$
> {\bf O_2} = \begin{bmatrix}
>   0 & 0 \\
>   0 & 0 
> \end{bmatrix},
> $$
> </div>
>
> 最後可得 <span>${\bf A^{21} = 7^{21}P + 8^{21}Q}$</span>, 所以答案 <span>$(a,b)=(7^{21}, 8^{21}).$</span>

## Q5 ✔

令 <span>$P(x)$</span> 為整係數多項式滿足 <span>$P(17)=11$</span> 與 <span>$P(25)=19$</span>。假設 <span>$P(n)=n+8$</span> 有兩個不同整數解 <span>$n_1$</span> 與 <span>$n_2$</span>，<span>$(n_1 < n_2)$</span>，試求 <span>$n_1, n_2$</span>。

> 容易得知 <span>$P(x)=(x-17)(x-25)Q(x)+x-6$</span>。
>
> 要求 <span>$P(x)=x+8$</span> 的整數解，等同於求 <span>$(x-17)(x-25)Q(x)=14$</span> 的整數解。
>
> 因數分解 <span>$14$</span> 可得以下 4 組解
>
> <div>
> $$
> 1\times2\times7 = 1\times-2\times-7 = -1\times2\times-7 = -1\times-2\times7.
> $$
> </div>
>
> 又 <span>$x-17 = (x-25)+8$</span>，所以可知 <span>$x-17=1$</span> 或 <span>$x-17=7$</span>，即 <span>$x=18,24$</span>。所以 <span>$n_1=18, n_2=24$</span>

## Q6 ✔

四邊形 ABCD，<span>$\overline{AB} = 8, \overline{BC} = 15, \overline{CD} = 17, \overline{DA} = 10$</span>，求四邊形 ABCD 的內切圓之最大面積。

> 令 <span>$x$</span> 為內切圓之半徑，<span>$\angle{ADC} = \theta_1, \angle{ABC} = \theta_2$</span>，可得四邊形 ABCD 面積為
>
> <div>
> $$
> \frac{(10+8+15+17)x}{2} = \frac{17\times10\times\sin{\theta_1}}{2} + \frac{8\times15\times\sin{\theta_2}}{2}
> $$
> </div>
>
> 兩邊整理一下可得到式一：
>
> <div>
> $$
> 25x^2 = (17\sin{\theta_1})^2 + 2\times17\times12\times\sin{\theta_1}\times\sin{\theta_2} + (12\sin{\theta_2})^2
> $$
> </div>
>
> 又 <span>$\overline{AC}$</span> 長度為
>
> <div>
> $$
> 17^2+10^2-2\times10\times17\times\cos{\theta_1} = 15^2+8^2-2\times15\times8\times\cos{\theta_2}
> $$
> </div>
>
> 兩邊整理一下可得到式二：
>
> <div>
> $$
> 25 = (17\cos{\theta_1})^2 - 2\times17\times12\times\cos{\theta_1}\times\cos{\theta_2} + (12\cos{\theta_2})^2
> $$
> </div>
>
> 所以式一加式二得到
>
> <div>
> $$
> x^2 = \frac{17^2+12^2-25-2\times17\times12\times\cos(\theta_1+\theta_2)}{25}
> $$
> </div>
> 所以當 <span>$\theta_1+\theta_2 = \pi$</span> 時，圓有最大面積 <span>$\frac{816\pi}{25}$</span>
