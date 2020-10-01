---
title: "有趣的一題"
date: 2020-10-01T02:13:00+08:00
draft: false
dropCap: false
categories:
    - "Math"
---

很久以前在 FB 上看到的這題

> 求證不等式 對於實數 $x$，$\cos(\sin x) > \sin(\cos x)$

<!--more-->

有人貼了很乾淨的解法：

> 因為 $\sin(\cos(x)) = \sin(\cos(-x))$ 跟 $\cos(\sin(x)) = \cos(-\sin(x)) = \cos(\sin(x))$，所以只需對 $x\in [0, \pi]$ 證明即可。
>
> 當 $x \in [0, \pi/2]$ 時，因為 $\sin(x) + \cos(x)\leq\sqrt{2} < \pi/2$，所以 $\sin(\cos(x)) < \sin(\pi/2 - \sin(x)) = \cos(\sin(x))$
>
> 當 $x \in (\pi/2, \pi]$ 時，顯然 $\sin(\cos(x)) < 0 < \cos(\sin(x))$ 得證。

![cos(sin(x))>sin(cos(x))](https://i.imgur.com/uZIT5Bp.png)