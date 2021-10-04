---
title: "ptt-math [其他] 連加的益智題"
date: 2020-10-01T13:14:00+08:00
draft: false
dropCap: false
categories:
  - "Math"
---

文章：http://www.ptt.cc/bbs/Math/M.1340716565.A.698.html

<!--more-->

題目： Consider the equation $\sum\limits_{k=1}^n \frac{1}{x_k^2} = 1.$ For which $n$ such that the equation has positive integer solution $x_k$ ?

Note it is know that $\frac{1}{4} + \frac{1}{4} + \frac{1}{4} + \frac{1}{9} + \frac{1}{9} + \frac{1}{36}$ and $\frac{1}{4} + \frac{1}{4} + \frac{1}{9} + \frac{1}{9} + \frac{1}{9} + \frac{1}{9} + \frac{1}{36} + \frac{1}{36}.$

---

解答：首先不失一般性，可以假設 $x_1\leq x_2\leq \cdots \leq x_n$

接著我們有以下解

<div>
$$
\begin{cases}
n = 1&\frac{1}{1}\\
n = 4&\frac{1}{4} + \frac{1}{4} + \frac{1}{4} + \frac{1}{4}\\
n = 6&\frac{1}{4} + \frac{1}{4} + \frac{1}{4} + \frac{1}{9} + \frac{1}{9} + \frac{1}{36}\\
n = 7&\frac{1}{4} + \frac{1}{4} + \frac{1}{4} + \frac{1}{16} + \frac{1}{16} + \frac{1}{16} + \frac{1}{16}\\
n = 8&\frac{1}{4} + \frac{1}{4} + \frac{1}{9} + \frac{1}{9} + \frac{1}{9} + \frac{1}{9} + \frac{1}{36} + \frac{1}{36}
\end{cases}
$$
</div>

而下面這個等式說明如果 $N$ 有解，那就可以拓展到 $N+3$ 也有解。

<div>
$$
\frac{1}{a^2} = \frac{1}{(2a)^2} + \frac{1}{(2a)^2} + \frac{1}{(2a)^2} + \frac{1}{(2a)^2},
$$
</div>

於是對於所有 $n=1, 4$ 或 $n \ge 6$ 的情況都能找到整數解。

---

如果 $n=2\text{ 或 }3$ 都會得到 $x_1=1$ 的矛盾。

<div>
$$
\begin{cases}
n = 2&\implies\frac{2}{x_1^2}\geq1&\implies x_1=1\\
n = 3&\implies\frac{3}{x_1^2}\geq1&\implies x_1=1
\end{cases}
$$
</div>

---

最後當 $n=5$ 用同樣的方法可以知道 $x_1 = 2$

- 假設 $x_4 \geq 3$ 得到以下矛盾

<div>
$$
\sum\limits_{k=1}^5 \frac{1}{x_k^2} \le \frac{1}{4} + \frac{1}{4} + \frac{1}{4} + \frac{1}{9} + \frac{1}{9} = \frac{35}{36} < 1
$$
</div>

- 假設 $x_4 = 2$，表示 $x_1 = x_2 = x_3 = x_4=2$ 則得到以下矛盾

<div>
$$
\sum\limits_{k=1}^5 \frac{1}{x_k^2} = \frac{1}{4} + \frac{1}{4} + \frac{1}{4} + \frac{1}{4} + \frac{1}{x_5^2} = 1 + \frac{1}{x_5^2} > 1
$$
</div>

於是 $\forall n\in\mathbb{N}$ 其中 $n\neq 2, 3, 5$ 都會有解。
