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

## 前置

先把要證明的問題稍微複雜點吧！ 🤓

1. 當 $n=3^r$ 是解答且 $n\mid\overbrace{11\dots11}^{n}$ 但 $3n\nmid\overbrace{11\dots11}^{n}$。
2. 其他數字不滿足。

## 證明情形一

對 $r$ 使用數學歸納法：

**Step 1 : $r=1$ 易證成立。**

**Step 2 : $r=k$ 成立，考慮 $r=k+1$ 的情況**

令 $N_0=3^{k}, N_1=3^{k+1}$。

如果 $N_1$ 不是解答，表示存在一組 $1\leq b < a\leq N_1$ 使得 

<div>
$$
\begin{aligned}
\overbrace{11\dots11}^{a}-\overbrace{11\dots11}^{b} &=\overbrace{11\dots11}^{a-b}\times1\overbrace{00\dots00}^{b}\\ 
&\equiv \overbrace{11\dots11}^{a-b} \equiv 0 \pmod{N_1}
\end{aligned}
$$
</div>

如果 $a-b\equiv 0 \pmod{N_0}$ 可整理得到 $\overbrace{11\dots11}^{N_0} \equiv 0 \pmod{3N_0}$，矛盾。

如果 $a-b\equiv z>0 \pmod{N_0}$，原式可以改寫成 

$$
\overbrace{11\dots11}^{a-b} \equiv 0 \pmod{N_0}
$$

那麼可以從前方逐次刪除 $\overbrace{11\dots11}^{N_0}$，可得到

<div>
$$
\overbrace{\underbrace{\cancel{11\dots11}}_{N_0\text{ 或 }2N_0\text{ 項}}\underbrace{11\dots11}_{z\text{ 項}}}^{a-b} \equiv \overbrace{11\dots11}^{z} \equiv0 \pmod{N_0}
$$
</div>

但 $z< N_0$，矛盾。所以 

$$
\tag{*1} N_1\text{ 是一組解答。}
$$

----

因為 $N_1$ 是一組解答，所以易證 

$$
\tag{*2}N_1\mid\overbrace{11\dots11}^{N_1}
$$

----

最後如果 $3N_1\mid\overbrace{11\dots11}^{N_1}$，表示它至少有 $r+2$ 個因數 $3$。但 

$$
\overbrace{11\dots11}^{N_1}=\overbrace{11\dots11}^{N_0}\times1\overbrace{00\dots00}^{N_0-1}1\overbrace{00\dots00}^{N_0-1}1
$$

前項 $\overbrace{11\dots11}^{N_0}$ 只有 $r$ 個因數 $3$，後項 $1\overbrace{00\dots00}^{N_0-1}1\overbrace{00\dots00}^{N_0-1}1$ 只有 $1$ 個因數 $3$[^1]，所以矛盾，故

$$
\tag{*3}3N_1\nmid\overbrace{11\dots11}^{N_1}
$$

----

根據 `*1`、`*2` 與 `*3`，已證完下面 3 件事。

- [x] $n=3^r$ 是解答
- [x] $n\mid\overbrace{11\dots11}^{n}$ 
- [x] $3n\nmid\overbrace{11\dots11}^{n}$

## 證明情形二

$n$ 為偶數或 $5$ 的倍數，顯見不成立。

考慮其他跟 $9$ 互質的數字 $n$，可透過[^2] [輾轉相除法](https://zh.wikipedia.org/wiki/%E8%BC%BE%E8%BD%89%E7%9B%B8%E9%99%A4%E6%B3%95) 或 [貝祖定理](https://zh.wikipedia.org/wiki/%E8%B2%9D%E7%A5%96%E7%AD%89%E5%BC%8F) 得到存在整數 $a,b$ 滿足 $9a+nb=-1$。

然後要證明下面這件事：

> 對於所有的 $k$ 使得 $ \overbrace{11\dots11}^{n}\neq a \pmod{n}$。

如果存在某個 $k$ 滿足，則 $\frac{10^k-1}{9} \equiv a \pmod{n}$，換句話說存在某個整數 $t$ 使得 

$$
10^k = 9(tn+a)+1 = 9tn+9a+1 = 9tn+bn = n(9t+b)
$$

因此 $n\nmid 10$，矛盾。 

然後我們可以透過 [鴿籠定理](https://zh.wikipedia.org/wiki/%E9%B4%BF%E5%B7%A2%E5%8E%9F%E7%90%86) 知道存在 $k_n< n$ 使得 $n\mid \overbrace{11\dots11}^{k_n}$

因此對於 $\gcd(n,9) = 3$ 的 $n$，可找到 $k_{\frac{n}{3}}$ 使得 

$$
\frac{n}{3}\mid \overbrace{11\dots11}^{k_{\frac{n}{3}}}
$$

於是找到 $k_n < n$ 滿足

$$
n\mid \overbrace{11\dots11}^{k_{\frac{n}{3}}}\overbrace{11\dots11}^{k_{\frac{n}{3}}}\overbrace{11\dots11}^{k_{\frac{n}{3}}} = \overbrace{11\dots11}^{k_n}
$$

同樣的手法也可以用在 $\gcd(n,9) = 9$ 的 $n$ 上。

因此對於非偶數或 $5$ 的倍數 $n$ 都能找到一個 $k_n+1\leq n$ 獲得以下結果，所以它們都不是解答。$\blacksquare$ 

$$
\overbrace{11\dots11}^{k_n+1}\equiv 1\pmod{n}
$$

## 觀察

假設 $\mathcal{L}(n)=k$ 定義為 **最少** 要 $k>0$ 個 1，才可以整除 $n$。那麼這題就是在找出哪些 $n$ 滿足 $\mathcal{L}(n)=n$。

我一開始是用程式檢查，然後觀察到一些有趣的性質(可能)[^3]： 🤔

1. 如果 $n$ 為大於 5 的質數 $p$，則 $\mathcal{L}(n)\mid n-1$。換句話說 $\mathcal{L}(n)< n$。
2. 如果 $n=p^k$，其中 $p$ 為非 $2, 5$ 的質數。則 $\mathcal{L}(n)=\mathcal{L}(p)\times p^{k-1}$。
3. 如果 $n_i=p_i^{k_i}$，其中 $p_i$ 為非 $2, 5$ 的質數。則
<div>
$$
\mathcal{L}(n_1\times\cdots\times n_m)\mid\mathcal{L}(n_1),\cdots,\mathcal{L}(n_m)\text{ 的最小公倍數}
$$
</div>

如果上面的性質都正確，那麼原題瞬間秒解。

1. $\mathcal{L}(3^k)=\mathcal{L}(3)\times 3^{k-1} = 3^k$
2. 對於其他的 $n$ 則是 
$$
\mathcal{L}(n)\leq\prod_i\mathcal{L}(n_i)=\prod_i\mathcal{L}(p_i)\times p_i^{k_i-1}< \prod_i p_i^{k_i}=n
$$

----

另外在解這題也找到一些相關資訊：

+ [循环单位](https://baike.baidu.com/item/%E5%BE%AA%E7%8E%AF%E5%8D%95%E4%BD%8D)
> 循环单位还有一个规律，就是：如果要让一个循环单位能除进一个质数，那这个质数必须大于6，而且，“1”的个数要比那个质数少1。
+ [Repunit](https://en.wikipedia.org/wiki/Repunit)

:::

----
[^1]: [倍數檢驗法](https://zh.wikipedia.org/wiki/%E5%80%8D%E6%95%B8)
[^2]: 由 [強者我同學](https://sites.google.com/view/ft-tu/home) 指點。
[^3]: 敬待有緣人協助。😎 