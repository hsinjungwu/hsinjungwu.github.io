---
title: "Fibonacci numbers"
date: 2021-05-20T10:20:00+08:00
draft: false
dropCap: false
categories:
    - "Project Euler"

---

從國中開始就認識 [費氏數列](https://en.wikipedia.org/wiki/Fibonacci_number) 了～　維基百科上也出現各種[程式參考解](https://zh.wikipedia.org/wiki/%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91%E6%95%B0%E5%88%97#%E7%A8%8B%E5%BC%8F%E5%8F%83%E8%80%83) 🙄

<!--more-->

----

[Project Euler](https://projecteuler.net/) 中第一個讓我糾結的題目是第 104 題，簡述如下

> 找出第 $n$ 個費氏數，滿足前 9 位數字與後 9 位數字包含了 1 ~ 9 

我是採用了 `golang` 的 [bigint](https://golang.org/pkg/math/big/) 暴力跑解 (`charp` 應該是引用 [BigInteger](https://docs.microsoft.com/zh-tw/dotnet/api/system.numerics.biginteger?view=net-5.0)) 結果這個數字長這樣 

$$
245681739\cdots\cdots\cdots352786941
$$

位數總共有 68855 啊！ 🍻 

我參考了其他人的解法[^1]後快速得到下面的結果 

+ $F_{3890} = 4096713285\cdots$ 是第一個前 10 位數包含了 0~9
+ $F_{10592} = \cdots1380567429$ 是第一個後 10 位數包含了 0~9 
+ $F_{4151451} = 3968427150\cdots\cdots\cdots351908674$ 是第一個前後 10 位數包含了 0~9

[^1]: 速度大概差 1000 倍啊～ 哭哭