---
title: "[還債] 今天想的一題高微"
date: 2023-01-07T00:30:00+08:00
draft: false
dropCap: false
tags:
  - "Math"
---

在 **2004/02/20 00:49:48** 於未來最舊小棧留下的問題，終於解了

## 題目

Prove 

$$
a_n = 2\sqrt{n} - \sum^n_{k=1}\frac{1}{\sqrt{k}}\to p, 1<p<2
$$

## 證明

$\lbrace a_n\rbrace$ is monotone increasing, because

{{< math >}}
$$
\begin{align*}
a_{n+1} - a_{n} &= 2\sqrt{n+1} - 2\sqrt{n} - \frac{1}{\sqrt{n+1}}\\
&=\frac{2}{\sqrt{n+1}+\sqrt{n}}- \frac{1}{\sqrt{n+1}}\\
&>\frac{2}{\sqrt{n+1}+\sqrt{n+1}}- \frac{1}{\sqrt{n+1}}=0
\end{align*}
$$
{{< /math >}}

Let 

{{< math >}}
$$
I_n=\int^{n+1}_{1}\frac{1}{\sqrt{x}}\mathrm{d}x,\ S_n=\sum^{n}_{k=1}\frac{1}{\sqrt{k}}
$$
{{< /math >}}

we have

{{< math >}}
$$
\begin{align*}
&\int^{n+1}_{1}\frac{1}{\sqrt{x}}\mathrm{d}x - \sum^{n}_{k=1}\frac{1}{\sqrt{k}}\\
=&\sum^{n}_{k=1}\int^{k+1}_{k}\frac{1}{\sqrt{x}}\mathrm{d}x - \sum^{n}_{k=1}\int^{k+1}_{k}\frac{1}{\sqrt{k}}\mathrm{d}x\\
=&\sum^{n}_{k=1}\int^{k+1}_{k}(\frac{1}{\sqrt{x}}-\frac{1}{\sqrt{k}})\mathrm{d}x
\end{align*}
$$
{{< /math >}}

But for all $k$, $\frac{1}{\sqrt{x}}-\frac{1}{\sqrt{k}}<0$, then 
{{< math >}}
$$
I_n-S_n\leq\int^{2}_{1}(\frac{1}{\sqrt{x}}-\frac{1}{\sqrt{1}})\mathrm{d}x=2\sqrt{2}-3
$$
{{< /math >}}

then 

{{< math >}}
$$
\begin{aligned}
1&=a_1< a_n\\
&=2\sqrt{n}-S_n\leq2\sqrt{n}-I_n+2\sqrt{2}-3\\
&=2\sqrt{n}-2\sqrt{n+1}+2+2\sqrt{2}-3\\
&<2\sqrt{2}-1
\end{aligned}
$$
{{< /math >}}

By [Monotone convergence theorem](https://en.wikipedia.org/wiki/Monotone_convergence_theorem), we have 

{{< math >}}
$$
1 < \lim_{n\to\infty}a_n\leq 2\sqrt{2}-1<2
$$
{{< /math >}}