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

## 證明

1. $n$ 不會是 $2$ 或 $5$ 的倍數。
2. $n=3^r$ 滿足。
3. 其他數字也都不滿足。

### 第一項

這個很直觀，跳過。

----

### 第二項

為了方便起見，我定義 $a_k = \overbrace{11\dots1}^{k}$。然後我要用數學歸納法同時證明下面三件事情：

1. $n = 3^k$ 滿足題目條件：$a_1\cdots a_n$ 模 $n$ 的數字都不相同。
2. $n \mid a_k$ 若且唯若 $k = n$。
3. $3n \nmid a_n$。

**step 1 : $n=3$，易證。**

**Step 2 : 假設 $n=3^k$ 成立，考慮 $3n=3^{k+1}$**

#### 第 1 點：滿足題目條件

假設存在 $a_x \equiv a_y \pmod{3n}$ 其中 $x>y$，那表示

$$
\overbrace{11\dots1}^{x} - \overbrace{11\dots1}^{y} = \overbrace{11\dots1}^{x-y}\overbrace{00\dots0}^{y} \equiv 0 \pmod{3n}
$$

但 $3n\nmid10$，所以上面可以簡化成

$$
\overbrace{11\dots1}^{x-y} = a_{x-y} \equiv 0 \pmod{3n}
$$

**Case 1 : $x-y \equiv 0 \pmod{n}$**

換句話說 $a_{x-y} = a_n$ 或 $a_{2n}=a_n\times1\overbrace{0\dots0}^{n}1$。

但由 **第 3 點** 的歸納法知道 $3n\nmid a_n$ 且根據 [3 的倍數檢驗法](https://zh.wikipedia.org/wiki/%E5%80%8D%E6%95%B8)[^1] $3n\nmid1\overbrace{0\dots0}^{n}1$，所以這個 case 不可能。

**Case 2 : $x-y \equiv z > 0 \pmod{n}$**

我們可以先將原式調整成 $a_{x-y} \equiv 0 \pmod{n}$。又因為 $a_n\equiv 0 \pmod{n}$ 所以 

$$
a_{x-y} \equiv a_z \equiv 0 \pmod{n}
$$

這表示 $z < n$ 且 $n\mid a_z$ 跟 **第 2 點** 矛盾。

總上所述 $a_1,\cdots,a_{3m}$ 模 $n$ 的數字都不相同。$\blacksquare$

#### 第 2 點

承 **第 1 點**，所以只要證 $3n\mid a_{3n}$。

假設存在 $i<3m$ 使得 $3m\mid a_i$，則會得到以下矛盾。 $\blacksquare$

$$
ａ_{i+1}＝10\times ａ_i+1\equiv 1\equiv ａ_1\pmod{3n}
$$

#### 第 3 點

這只要證明 $m\mid a_m$ 但 $3\nmid \frac{a_m}{m}$ 就好。

<div>
$$
\begin{aligned}
\frac{a_{3n}}{3n} &=\frac{a_n\times1\overbrace{0\dots0}^{n}1\overbrace{0\dots0}^{n}1}{3n}\\\\
&=\frac{a_n}{n}\times\frac{1\overbrace{0\dots0}^{n}1\overbrace{0\dots0}^{n}1}{3}
\end{aligned}
$$
</div>

由歸納法 **第 2 點** 知道 $n\mid a^n$ 及 $3\nmid \frac{a^n}{n}$。

且根據 [倍數檢驗法](https://zh.wikipedia.org/wiki/%E5%80%8D%E6%95%B8)[^2] 知道 $1\overbrace{0\dots0}^{n}1\overbrace{0\dots0}^{n}1$ 是 $3$ 的倍數，但不是 $9$ 的倍數

所以得證。$\blacksquare$

----

### 第三項

由強者我同學贊助證明。

考慮其他可能的數字 $n$，由於它跟 $9$ 互質，可透過 [輾轉相除法](https://zh.wikipedia.org/wiki/%E8%BC%BE%E8%BD%89%E7%9B%B8%E9%99%A4%E6%B3%95) 或 [貝祖定理](https://zh.wikipedia.org/wiki/%E8%B2%9D%E7%A5%96%E7%AD%89%E5%BC%8F) 得到存在整數 $x,y$ 滿足 $9x+ny=-1$。

然後要證明下面這件事：

> 對於所有的 $k$ 使得 $a_k \neq x \pmod{n}$。

如果存在某個 $k$ 滿足，則 $a_k = \frac{10^k-1}{9} \equiv x \pmod{n}$，換句話說 

$$
10^k = 9tn+9x+1 = 9tn+ny = (9t+y)n
$$

但 $n\nmid 10^k$，所以矛盾。 $\blacksquare$

## 觀察

我一開始是用程式檢查，然後觀察到一些有趣的性質(可能)：

假設 $l(n) = k$ 定義為 **最少** 要 $k$ 個 1，可以整除 $n$。那麼這題就是在找出 $l(n)=n$。

如果 $n=\prod p_i^{k_i}$，其中 $p_i$ 為非 $2, 5$ 的質數。則

$$
l(n)\mid \prod l(p_i)\times p_i^{k_i-1}
$$

又根據 [鴿籠定理](https://zh.wikipedia.org/wiki/%E9%B4%BF%E5%B7%A2%E5%8E%9F%E7%90%86) 可知 $l(n)\leq n$，所以可以輕鬆找出滿足條件的 $n$？ 🤔 

另外在解這題也找到一些相關資訊：

+ [循环单位](https://baike.baidu.com/item/%E5%BE%AA%E7%8E%AF%E5%8D%95%E4%BD%8D)
> 循环单位还有一个规律，就是：如果要让一个循环单位能除进一个质数，那这个质数必须大于6，而且，“1”的个数要比那个质数少1。
+ [Repunit](https://en.wikipedia.org/wiki/Repunit)

:::

----
[^1]: 若數字和是3的倍數，則此整數為3的倍數。
[^2]: 若數字和是9的倍數，則此整數為9的倍數。