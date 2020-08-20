---
title: "數學求救信"
date: 2020-08-20T12:25:00+08:00
draft: false
dropCap: false
categories:
    - "Math"
---

之前(2017年)在刷 Email 看有沒有人寄面試邀請函時居然看到了數學求救信 😑

<!--more-->

題目是這樣的：

> A set $S$ is dense in $\mathbb{R}$ if and only if every number $x$ is the limit of a sequence in $S$.

老實說我連 [dense set](https://en.wikipedia.org/wiki/Dense_set) 的定義是什麼都忘了啊～ 🤣

## Definition

言歸正傳，根據 [Walter Rudin](https://en.wikipedia.org/wiki/Walter_Rudin) 寫的 *Principle of Mathematical Analysis 3rd edition* 裡提到的定義：

Let $X$ be a metric space.
+ A *neighborhood* of a point $p$ is a set $N_r(p)$ consisting of all points *q* such that $d(p, q) < r$. The number $r$ is called *radius* of $N_r(p)$.
+ A point $p$ is a *limit point* of the set $E$ if *every* neighborhood of $p$ contains $q \neq p$ such that $q \in E$.
+ A set $ E $ is *dense in* $X$ if every point of $X$ is a limit point of $E$, or a point of $E$(or both).

另外 *limit of a sequence* 的定義這個就不需贅述了。

## Proof

If $S$ is dense in $\mathbb{R}$ then every point $x \in \mathbb{R}$ is a limit point of $S$, or a point of $S$(or both).

If $x \in S$, then it is trivial that $x$ is the limit of sequence $\{ x \}$. 

Otherwise choose sequence $\{ q_i \mid q_i \in S, d(x, q_i) < 1/i, i = 1, 2, \dots \}$. For every $\epsilon > 0$ choose an integer $N = \lceil\frac{1}{\epsilon}\rceil \geq \frac{1}{\epsilon} $ such that $n \geq N$ implies 

$$
d(x, q_n) < \frac{1}{n} \leq \frac{1}{N} \leq \epsilon.
$$

Then $x$ is the limit of a sequence in $S$.

Conversely, consider $x$ is the limit of a sequence $\{q_i\}$ in $S$ and $x \notin S$, then given arbitrary radius $r$, there exists some integer $N$ such that $d(x, q_N) < r$, i.e. $x$ is a limit point of $S$. Since every point is either in $S$ or a limit point of $S$(or both), then $S$ is dense in $\mathbb{R}$. $\blacksquare$

## 結論

因為這題根據定義就能做出來！所以沒有回信給這位求救的朋友，但還是手癢把它寫出來。如果有緣的話在茫茫 Google 海中自會再相見。 😂