---
title: "傅立葉展開"
date: 2024-07-08T20:25:00+08:00
draft: false
dropCap: false
tags:
  - "Note"
  - "Fourier series"
---

前幾天面試到一位剛畢業的新鮮人時，他提到了 [傅立葉級數](https://zh.wikipedia.org/wiki/%E5%82%85%E9%87%8C%E5%8F%B6%E7%BA%A7%E6%95%B0)，剛好前幾天有向圖書館線上借閱 [數學女孩物理筆記：波的疊加 (電子書)](https://www.books.com.tw/products/E050203731)，就剛好倚老賣老借花獻佛介紹它啦。

----

問 : 為什麼要用傅利葉表示將函數 $f(x)$ 寫成下面這種形式呢？

$$
f(x) = \sum\limits_{k=0}^{\infty}(a_k\cos \text{k}x+b_k\sin\text{k}x)
$$

答 : 因為想用單純的事物來表示複雜的事物。

> 傅利葉展開可以將特定函數表示成三角函數的線性組合，如此一來，便能清楚知道該函數性質，擁有什麼樣的對稱性，還可以當成三角函數的線性組合處理。