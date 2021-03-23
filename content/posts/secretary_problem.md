---
title: "秘書問題(Secretary problem)"
date: 2020-10-01T19:28:00+08:00
draft: false
dropCap: false
categories:
    - "Math"
---

很久以前高中同學宜佑問我的一個問題[^1]

<!--more-->

> 要聘請一名秘書，有 $n$ 個應聘者。每次面試一人，面試後就要馬上決定是否聘他，如果當時決定不聘他，他便不會回來。面試後總能清楚了解應聘者的合適程度，並能和之前的每個人做比較。問什麼樣的策略，才使最佳人選被選中的機率最大。 

當然因為時間關係，我只說明選擇的策略為：先直接放棄前面 $r$ 個人，然後在這 $r$ 個人中選出一個最好的人，我們稱他為 $M$，並以 $M$ 當作基準點，遇到第一個比 $M$ 小姐好的就直接錄用，不好的就淘汰。 

----

那如何求最佳的 $r$ 呢？我試著用簡單的概念但是很複雜的計算來寫。 🤓

為了方便起見，我們將這 $n$ 個人打上編號從 **#1** 到 **#n**, 其中號碼越大代表他越優秀。如果 **#n** 在第 $r+i$ 的位置，而且我們要選到他，代表前面 $r+i-1$ 個數字，最大的落在前面 $r$ 個內。

所以我們在 **#1** 到 **#n-1** 中先選出 $r+i-1$ 個數字，然後令這之中最大的為 **#M**，那 **#M** 有 $r$ 個位置可以選，剩下來的數字就隨便排，接着再放 **#n** 在第 $r+i$ 的位置，最後的數字再隨便排。所以算式如下： 

$$
{n-1 \choose r+i-1} \times r\times (r+i-2)!\times 1\times (n-r-i)! = \frac{(n-1)!r}{r+i-1}
$$ 

由於 $i$ 可以是 $1, \dots, n-r,$ 所以能選到 **#n** 的全部的排列組合數為 

$$
\sum\limits_{i=1}^{n-r}\frac{(n-1)!r}{r+i-1}
$$ 

因此選到的機率為 

$$
\frac{\sum\limits_{i=1}^{n-r}\frac{(n-1)!r}{r+i-1}}{n!} = \sum\limits_{i=1}^{n-r}\frac{r}{n(r+i-1)} = \frac{r}{n}\sum\limits_{i=r}^{n-1}\frac{1}{i}
$$ 

如果當 $n$ 趨近 $\infty$ 時，且令 $x = \lim\limits_{n\to\infty}\frac{r}{n}$ 則上式可近似下列積分形式 

$$
\frac{r}{n}\sum\limits_{i=r}^{n-1}\frac{n}{i}\frac{1}{n} \approx x\int\limits_{t=x}^{1}\frac{1}{t}dt = -x\log(x)
$$ 

那麼我們可以解出 $x = 1/e$，其中 $e$ 就是大家熟知的 [Euler's number](http://en.wikipedia.org/wiki/E_(mathematical_constant))。因此最佳的策略是放棄前 $n/e$ 個人，之後才開始選。

[^1]: [秘書問題](https://zh.wikipedia.org/wiki/%E7%A7%98%E6%9B%B8%E5%95%8F%E9%A1%8C)