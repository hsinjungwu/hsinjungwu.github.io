---
title: "[還債] Exercises on Combinatorics"
date: 2018-08-25T11:51:54+08:00
draft: false
dropCap: false
tags:
  - "Math"
---

在 **2004/11/23 16:20:47** 於未來最舊小棧留下的問題，終於解了。

## 題目

Let $F_n$ denote the $n$-th fibonacci number. Let $\alpha=\frac{1+\sqrt{5}}{2}.$ Prove that 

{{< math >}}
$$\frac{\alpha^{n-\frac{1}{n}}}{\sqrt{5}}\leq F_n.$$
{{< /math >}}

## 證明

首先我們知道幾件事

1. $F_n = \frac{\alpha^n - \beta^n}{\sqrt{5}}, \forall n>0,\text{ where }\beta=\frac{1-\sqrt{5}}{2}$
2. $\beta^n \leq \alpha^{-n}$
3. $\alpha^2 - \alpha - 1 = 0$

所以這題其實只要證下面這件事情就好。

{{< math >}}
$$
\alpha^n-\beta^n\geq\alpha^{n-\frac{1}{n}}
$$
{{< /math >}}

為了容易閱讀，先令 $\gamma=\frac{1}{\sqrt[n]{\alpha}}$。我們知道 $\alpha>1>\gamma$

{{< math >}}
$$
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
$$
{{< /math >}}

所以由上可得

{{< math >}}
$$
\alpha^n-\beta^n \geq \alpha^n-\alpha^{-n} \geq \alpha^{n-\frac{1}{n}}
$$
{{< /math >}}


## 後記

當年的做法跟 [這篇](https://math.stackexchange.com/questions/1087678/let-a-n-2-sqrt-n-sum-k-1n-frac1-sqrtk-show-a-n-converges-and-1) 發文者一樣，只走到 $1 < \lim\limits_{n\to\infty}a_n\leq2$，後來就不了了之。