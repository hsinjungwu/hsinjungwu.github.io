---
title: "一題關於費氏數列的組合數學"
date: 2020-08-20T13:14:00+08:00
draft: false
dropCap: false
categories:
    - "Math"
---

之前讀研究所的作業。 😰

<!--more-->

## 題目

Let $F_n$ denote the $n$-th fibonacci number. Let $\alpha=\frac{1+\sqrt{5}}{2}.$ Prove that 

$$
F_n\geq\frac{\alpha^{n-\frac{1}{n}}}{\sqrt{5}}.
$$

## 解答

首先我們知道幾件事

1. $F_n = \frac{\alpha^n - \beta^n}{\sqrt{5}}, \forall n>0,\text{ where }\beta=\frac{1-\sqrt{5}}{2}$
2. $\beta^n \leq \alpha^{-n}$
3. $\alpha^2 - \alpha - 1 = 0$

所以這題其實只要證下面這件事情就好。

$$
\alpha^n-\beta^n\geq\alpha^{n-\frac{1}{n}}
$$

為了容易閱讀，先令 $\gamma=\frac{1}{\sqrt[n]{\alpha}}$。我們知道 $\alpha>1>\gamma$，接著就開始 ~~推倒~~ 推導吧！

<div>
$$
\begin{aligned}
&\quad &\sum\limits_{i=0}^{n-1} {n-1 \choose i}\alpha^{i} &\geq \sum\limits_{i=0}^{n-1} \gamma^{i}\\
&\implies &(\alpha+1)^{n-1} &\geq \frac{1-\gamma^n}{1-\gamma}\\
&\implies &(\alpha+1)^{n-1}(1-\gamma) &\geq 1-\gamma^n\\
&\implies &(\alpha^2)^{n-1}(1-\frac{1}{\sqrt[n]{\alpha}}) &\geq 1-\frac{1}{\alpha}\\
&\implies &\alpha^{2n-2}-\alpha^{2n-2-\frac{1}{n}} &\geq 1-\frac{1}{\alpha}\\
&\implies &\alpha^{2n}-\alpha^{2n-\frac{1}{n}} &\geq \alpha^2-\alpha =1\\
&\implies &\alpha^n-\alpha^{n-\frac{1}{n}} &\geq \alpha^{-n}\\
&\implies &\alpha^n-\alpha^{-n} &\geq \alpha^{n-\frac{1}{n}}
\end{aligned}
$$
</div>

所以由上可得

$$
\alpha^n-\beta^n \geq \alpha^n-\alpha^{-n} \geq \alpha^{n-\frac{1}{n}}
$$