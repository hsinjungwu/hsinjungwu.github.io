---
title: "When is sin(x) rational?"
date: 2020-10-01T09:05:00+08:00
draft: false
dropCap: false
categories:
  - "Math"
---

很久很久以前在學弟那看到一個問題：$\sin1^{\circ}$ ~ $\sin89^{\circ}$ 中只有 $\sin30^{\circ}$ 為有理數。

<!--more-->

原本想可能跟證明 $\sin1^\{\circ}$ 為無理數類似的手法，不過後來查到了這個 [Niven's theorem](http://mathworld.wolfram.com/NivensTheorem.html)

> Niven's theorem states that if $x/\pi$ and $\sin{x}$ are both rational, then the sine takes values 0, $\pm\frac{1}{2}$ , and $\pm 1$.

所以套這個定理就秒殺了。 😆

如果不要用定理秒殺的話，那就玩假裝不知道的遊戲吧！

---

為了方便起見，我把原問題轉到 $\cos$ 跟擴大成有理數角度。

令 $\alpha = \frac{m}{n}2\pi$，其中 $\frac{m}{n}$ 為一最簡有理數。

假設 $2\cos\alpha$ 為一最簡有理數 $\frac{q}{p}$，其中 $p>0$。

由二倍角公式可得

<div>
$$
\begin{aligned}
2\cos2\alpha &= (2\cos\alpha)^2 - 2\\
&= (\frac{q}{p})^2 - 2\\
&= \frac{q^2-2p^2}{p^2}
\end{aligned}
$$ 
</div>

我們可以透過簡單的證明得到 $\frac{q^2-2p^2}{p^2}$ 一樣是最簡分數。

假設 $p\neq 1$，那麼我們發現 $\\{ 2\cos2^k\alpha \mid \forall k \in \mathbb{N}\\}$ 彼此都不相同，因為分母呈現遞增狀態。

但是我們知道 $\cos(\frac{m}{n}2\pi)$ 最多只有 $n$ 個不同的值。故矛盾，所以 $p=1$。

由 $-1\leq\cos\alpha = \frac{q}{2}\leq 1$，且 $q$ 為整數，可得 $q=0, \pm1, \pm2$。

所以 $\cos\alpha$ 為有理數的可能值為 $0, \pm\frac{1}{2}, \pm1$。

---

另外 [也有人提供了下面的證法](http://math.stackexchange.com/questions/87756/when-is-sinx-rational)

> Find all rational multiples of $\pi$ so that $\sin(\pi p/q)$ is rational.
>
> If $p/q\in\mathbb{Q}$, then $e^{\pm i\pi p/q}$ is an algbraic integer since $(e^{\pm i\pi p/q})^q−(−1)^p=0.$
>
> Thus, $$2\sin(\pi p/q)=−i(e^{i\pi p/q}−e^{−i\pi p/q})$$ is the difference and product of algebraic integers, and therefore an algebraic integer.
>
> However, the only rational algebraic integers are normal integers. Thus, the only values of $\sin(\pi p/q)$ which could be rational, are those for which $2\sin(\pi p/q)$ is an integer, that is $$\sin(\pi p/q)\in \\{−1,−1/2,0,1/2,1\\}.$$
