---
title: "[PE 筆記] Pythagorean Triplet"
date: 2024-02-24T10:20:00+08:00
draft: false
dropCap: false
tags:
  - "Project Euler"
---

記憶中在 [Project Euler](https://projecteuler.net/) 遇到 [Pythagorean triple(畢氏三元數)](https://en.wikipedia.org/wiki/Pythagorean_triple) 相關題目時，都會優先使用以下生成方式解題


{{< notice tip >}}
當正整數 $m$ 與 $n$ 滿足 $m>n$, 互質且一奇一偶

+ $a = m^2-n^2$
+ $b = 2mn$
+ $c = m^2+n^2$

則 $a,b,c$ 為素畢氏三元數。
{{< /notice >}}