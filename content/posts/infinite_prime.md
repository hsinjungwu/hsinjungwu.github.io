---
title: "試證明質數有無限多個"
date: 2020-10-01T10:20:00+08:00
draft: false
dropCap: false
categories:
  - "Math"
---

經典 FAQ！　 🤓

<!--more-->

最有名的莫過於 [Euclid](https://en.wikipedia.org/wiki/Euclid) 在幾何原本(Elements) 中 [Book IX, Proposition 20](https://mathcs.clarku.edu/~djoyce/java/elements/bookIX/propIX20.html) 提出的方法：

> 假設質數是有限個, 全部由小到大依序列出 $p_1, p_2, \cdots, p_n$, 考慮 $q = 1 + \prod\limits_{i=1}^{n} p_i$. 如果 $q$ 是質數，那麼我們找到比 $p_n$ 還大的質數, 矛盾！如果 $q$ 是合數, 那麼所有的質數 $p_i$ 都無法整除 $q$, 矛盾！於是質數有無限多個。 Q.E.D.

---

另外我之前也看過另一個證法，首先先證明下面這件事：

> Give an integer $n\geq 3$, Claim there exists a prime number $p$ such that $n < p < n!$

證明過程如下：

Consider $a = n!-1$, then there must be some prime number $p < n!$ such that $p \mid a$.

If $p \leq n$, then $p \mid n!$, thus we have $p \mid (n!-a)$, that is $p \mid 1$, contradiction. Hence $n < p < n!$.

然後利用這件事，就可證明質數有無限多個。

Take $\{a_i \mid a_1 = 3, a_{i+1} = (a_i)!, \forall i\geq 1\}$, given positive integer $i$, there exists some $p_i$ s.t. $a_i < p_i < a_{i+1} = (a_i)!$, and $\{p_i\}$ is strictly increasing, then we are done.

---

而之前也拜讀了 [Euler](https://en.wikipedia.org/wiki/Leonhard_Euler) 的證法，祂也同樣是用反證法。

假設質數是有限個, 全部由小到大依序列出 $p_1, p_2, \cdots, p_n$, 然後我們考慮下面這個式子

$$
\tag{*A}\prod\limits_{i=1}^{n}\sum\limits_{j=0}^{\infty}\frac{1}{p_i^j} = \prod\limits_{i=1}^{n}\frac{1}{1-1/p_i}
$$

可以知道 `*A` 的值會收斂。接着把 `*A` 的前項展開得到

$$
\tag{*B}\prod\limits_{i=1}^{n}\sum\limits_{k=1}^{\infty}\frac{1}{p_i^j} = \sum\limits_{j=0}^{\infty}\frac{1}{p_1^{r_1}}\times\frac{1}{p_2^{r_2}}\times\cdots\times\frac{1}{p_n^{r_n}}
$$

其中 $r_1 + r_2 + \cdots + r_n = k.$

而每一個正整數 $k$ 我們都可以找到唯一一種以 $p_1^{r_1}\times p_2^{r_2}\times\cdots\times p_n^{r_n}$ 表示的質因數分解法，於是 `*B` 可改寫為

$$
\tag{*C}\prod\limits_{i=1}^{n}\sum\limits_{j=0}^{\infty}\frac{1}{p_i^j} = \sum\limits_{k=1}^{\infty}\frac{1}{k}
$$

而 `*C` 的值卻是發散。於是我們得到矛盾，因此質數有無限多個。
