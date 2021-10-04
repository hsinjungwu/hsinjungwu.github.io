---
title: "[解答] 森棚教官數學題－全數出動"
date: 2020-09-10T10:20:00+08:00
draft: false
dropCap: false
categories:
  - "Math"
---

今天又是個被問數學的早晨～ 😆

<!--more-->

大學同學問我 [森棚教官數學題－全數出動](https://www.ntsec.edu.tw/LiveSupply-Content.aspx?a=6829&fld=&key=&isd=1&icop=10&p=1&lsid=16288)，也給了提示 $n=3^r$ 應該是解答。

## 前置作業

先定義對於每一個 $n$ 我們最少需要 $\mathcal{L}(n)$ 個 $1$，使得 $n\mid\overbrace{1\dots\dots\dots1}^{\mathcal{L}(n)}$。

有一些簡單的特性可以很快看出

1. $\mathcal{L}(n)\leq n$。
2. 如果正整數 $k$ 也滿足 $n\mid\overbrace{1\dots\dots\dots1}^{k}$，那麼 $\mathcal{L}(n)\mid k$。
3. 如果 $n\mid m$ 則 $\mathcal{L}(n)\mid\mathcal{L}(m)$。
4. 如果 $n$ 是解答，表示 $\mathcal{L}(n)=n$

然後先把要證明的問題稍微複雜點吧！ 🤓

- $n=3^k$ 是解答且 $\overbrace{1\dots\dots\dots1}^{3^k}$ 恰好有 $k$ 個質因數 $3$。
- 其他數字不滿足。

## 證明 $n=3^k$

**Step 1 : $k=1$**

因為 $\mathcal{L}(3)=3$ 所以是解答，且 $111$ 恰好只有 $1$ 個質因數 $3$

**Step 2 : 假設 $k=r$ 成立，試證 $k=r+1$ 也成立。**

由於 $\overbrace{1\cdots\cdots\cdots1}^{3\mathcal{L}(3^r)}$ 可以寫成 $\overbrace{1\cdots1}^{\mathcal{L}(3^r)}$ 與 $1+10^{\mathcal{L}(3^r)}+10^{2\mathcal{L}(3^r)}$ 的乘積。前者由歸納法得知恰有 $k$ 個質因數 $3$，後者由 [倍數檢驗法](https://zh.wikipedia.org/wiki/%E5%80%8D%E6%95%B8) 知道恰有 $1$ 個質因數 $3$。所以它恰有 $k+1$ 個質因數 $3$，即

<div>
$$
3^{k+1}\mid\overbrace{1\cdots\cdots\cdots1}^{3\mathcal{L}(3^r)}
$$
</div>

於是根據 **特性 2** 跟 **特性 3** 知道

<div>
$$
\mathcal{L}(3^r)\mid\mathcal{L}(3^{r+1})\mid3\mathcal{L}(3^r)
$$
</div>

所以 $\mathcal{L}(3^{r+1})$ 等於 $\mathcal{L}(3^r)$ 或 $3\mathcal{L}(3^r)$。但根據歸納法知道 $\overbrace{1\dots\dots\dots1}^{3^r}$ 恰好有 $r$ 個質因數 $3$，所以 $3^{r+1}\nmid\overbrace{1\dots\dots\dots1}^{3^r}$

於是

<div>
$$
\mathcal{L}(3^{r+1})=3\mathcal{L}(3^r)=3\times3^r=3^{r+1}
$$
</div>

## 證明其他情況

$n$ 為偶數或 $5$ 的倍數，顯見不成立。

先考慮 $\gcd(n,9) = 1$ 的 $n$，透過 [歐拉定理](<https://zh.wikipedia.org/wiki/%E6%AC%A7%E6%8B%89%E5%AE%9A%E7%90%86_(%E6%95%B0%E8%AE%BA)>) 知道 $10^{\varphi(n)}\equiv1\pmod{n}$ 且 $10^{\varphi(n)}\equiv1\pmod{9}$

因此 $n\mid\overbrace{1\dots\dots\dots1}^{\varphi(n)}$，換句話說 $\mathcal{L}(n)\leq\varphi(n)< n$ 所以這類的 $n$ 不成立。

接著對於 $\gcd(n,9) = 3$ 的 $n$，令 $m=\frac{n}{3}$。則 $\gcd(m,9)=1$ 那麼

<div>
$$
\begin{aligned}
&n=3m\mid(1+10^{\varphi(m)}+10^{2\varphi(m)})\times\overbrace{1\dots\dots\dots1}^{\varphi(m)}\\
\implies & \mathcal{L}(n)\leq3\varphi(m)< 3m=n
\end{aligned}
$$
</div>

最後 $\gcd(n,9) = 9$ 的 $n$，令 $m=\frac{n}{9}$。則 $\gcd(m,9)=1$ 那麼

<div>
$$
\begin{aligned}
&n=9m\mid(1+10^{\varphi(m)}+\cdots+10^{8\varphi(m)})\times\overbrace{1\dots\dots\dots1}^{\varphi(m)}\\
\implies & \mathcal{L}(n)\leq9\varphi(m)< 9m=n
\end{aligned}
$$
</div>

於是證明全部完成。 $\blacksquare$

---

## 觀察

我一開始是用程式檢查，然後觀察到一些有趣的性質(可能)： 🤔

1. 如果 $n=p^k$，其中 $p$ 為非 $2, 5$ 的質數。則 $\mathcal{L}(n)=\mathcal{L}(p)\times p^{k-1}$。
2. 如果 $n=\prod\limits_{i=1}^{m}p_i^{k_i}$，其中 $p_i$ 為非 $2, 5$ 的質數。則
<div>
$$
\mathcal{L}(n)\mid \{\mathcal{L}(p_1^{k_1}),\cdots,\mathcal{L}(p_m^{k_m})\}\text{ 的最小公倍數}
$$
</div>

如果上面的性質都正確，那麼原題瞬間秒解。

1. $\mathcal{L}(3^k)=\mathcal{L}(3)\times 3^{k-1} = 3^k$
2. 對於其他的 $n$ 則是
   $$
   \mathcal{L}(n)\leq\prod_i\mathcal{L}(p_i)\times p_i^{k_i-1}< \prod_i p_i^{k_i}=n
   $$

---

## 後記

1. 原來這個東西有名字叫 [Repunit](https://en.wikipedia.org/wiki/Repunit)。

2. [強者我同學](https://sites.google.com/view/ft-tu/home) 提供了 [輾轉相除法](https://zh.wikipedia.org/wiki/%E8%BC%BE%E8%BD%89%E7%9B%B8%E9%99%A4%E6%B3%95) 的思路來解 $n\neq 3^r$ 的情形

> 對於 $\gcd(9,p)=1$ 存在 $a,b\in\mathbb{Z}$ 使得 $a,b$ 滿足 $9a+np=-1$。
>
> 然後證明對於所有的 $k$ 都不會滿足以下式子。
>
> <div>
> $$
> \overbrace{1\dots1}^{k}\neq a \pmod{p}
> $$
> </div>

3. 在解這題時看到 [這篇文章](https://baike.baidu.com/item/%E5%BE%AA%E7%8E%AF%E5%8D%95%E4%BD%8D) 寫的性質，其實就是 [費馬小定理](https://zh.wikipedia.org/wiki/%E8%B4%B9%E9%A9%AC%E5%B0%8F%E5%AE%9A%E7%90%86) 的應用

   > 循环单位还有一个规律，就是：如果要让一个循环单位能除进一个质数，那这个质数必须大于 6，而且，“1”的个数要比那个质数少 1。

4. 觀察到的 **性質 1** 如果是對的，應該(?)能用 **證明 $n=3^3$** 一樣的手法證明。😕
