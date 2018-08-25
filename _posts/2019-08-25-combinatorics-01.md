---
layout: post
title:  "一題關於費氏數列的組合數學"
date:   2018-08-25 11:51:54
tags:  
  - math
  - combination
  - Fibonacci_Sequence
---

雖然只是複製內容在數學解答部落格，但還是會稍微看內容在寫什麼。結果發現有一題的答案貼了兩篇，結果一篇 [我的作法] 是半對，另一篇 [同學的做法] 是錯的... :cold_sweat:

<!-- more -->

為了面子只好把這 14 年前的問題再想一遍。 :sob:

## 題目

Let <katex>F_n</katex> denote the <katex>n</katex>-th fibonacci number. Let <katex>\alpha=\frac{1+\sqrt{5}}{2}.</katex> Prove that 

<katex centred = "true">\frac{\alpha^{n-\frac{1}{n}}}{\sqrt{5}}\leq F_n.</katex>

## 解答

首先我們知道幾件事

1. <katex>F_n = \frac{\alpha^n - \beta^n}{\sqrt{5}}, \forall n>0,\text{ where }\beta=\frac{1-\sqrt{5}}{2}</katex>
2. <katex>\beta^n \leq \alpha^{-n}</katex>
3. <katex>\alpha^2 - \alpha - 1 = 0</katex>

所以這題其實只要證下面這件事情就好。

<katex centred = "true">\alpha^n-\beta^n\geq\alpha^{n-\frac{1}{n}}</katex>

為了容易閱讀，先令 <katex>\gamma=\frac{1}{\sqrt[n]{\alpha}}</katex>。我們知道 <katex>\alpha>1>\gamma</katex>，接著就開始 ~~推倒~~ 推導吧！

<katex centred = "true">
\begin{aligned}
&\quad &\sum\limits_{i=0}^{n-1} {n-1 \choose i}\alpha^{i} \geq \sum\limits_{i=0}^{n-1} \gamma^{i}\\
&\implies &(\alpha+1)^{n-1} \geq \frac{1-\gamma^n}{1-\gamma}\\
&\implies &(\alpha+1)^{n-1}(1-\gamma) \geq 1-\gamma^n\\
&\implies &(\alpha^2)^{n-1}(1-\frac{1}{\sqrt[n]{\alpha}}) \geq 1-\frac{1}{\alpha}\\
&\implies &\alpha^{2n-2}-\alpha^{2n-2-\frac{1}{n}}\geq 1-\frac{1}{\alpha}\\
&\implies &\alpha^{2n}-\alpha^{2n-\frac{1}{n}}\geq\alpha^2-\alpha =1\\
&\implies &\alpha^n-\alpha^{n-\frac{1}{n}} \geq \alpha^{-n}\\
&\implies &\alpha^n-\alpha^{-n} \geq \alpha^{n-\frac{1}{n}}
\end{aligned}
</katex>

所以由上可得

<katex centred = "true">\alpha^n-\beta^n \geq \alpha^n-\alpha^{-n} \geq \alpha^{n-\frac{1}{n}}</katex>