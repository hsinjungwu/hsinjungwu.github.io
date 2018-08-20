---
layout: post
title:  "Tips of Excel"
date:   2018-04-26 12:51:54
categories: Excel
tags:  
  - Excel
  - ArrayFomula
  - Indirect
---

* content
{:toc}

**Excel** 真的是博大精深啊！ :grimacing: 

<!-- more -->

工作上遇到下面兩個問題，可參考[解答範例][sample]。

## Question 1

> 隨機給定 10 個正整數，試判斷是否有連續 3 個 5。

基本上是可以暴力寫再搭配下拉兩步驟算出。但如果不要下拉的話，我在[解答範例][sample]中 Sheet *Answer 1* 套用 [Array Formula][AF] 以下面的寫法完成。

``` text
=SUM((A1:A8=5)*(A2:A9=5)*(A3:A10=5))
```

而這段公式翻譯就是

<katex centred="true"> \sum_{i=1}^{8}(A_i == 5 ? 1 : 0)*(A_{i+1} == 5 ? 1 : 0)*(A_{i+2} == 5 ? 1 : 0)</katex>

但如果題目的數字不只 10 個，該如何寫會更方便？

這時就需要 [INDIRECT](https://support.office.com/en-us/article/indirect-function-474b3a3a-8a26-4f44-b491-92b6306fa261) 改寫

``` text
=SUM((A1:INDIRECT("A"&N8)=$D$1)*(A2:INDIRECT("A"&N7)=$D$1)*(A3:INDIRECT("A"&N6)=$D$1))
```

## Question 2

> 給定正整數 x, y, z, a, b, c 以指定機率方式將 x, y, z 中任意兩數的值改為 a, b, c。即 x(y, z) 變成 a(b, c)，試算改變後三數相乘期望值。

數學式子可以直接列出來 <katex>P_{xy}abz+P_{xz}ayc+P_{yz}xbc</katex> 很簡單，但如果個數變多還要用 Excel 來做就稍微有點難度了。

於是我想到 `[a, b, z]` 可以看成是 `([a, b, c] <乘> [1, 1, 0]) <加> ([x, y, z] <乘> [0, 0, 1])`，其中的 `<加>`, `<乘>` 效果如下：

> `[i,j k] <加> [p, q, r] = [i+p, j+q, k+r]`    
> `[i,j k] <乘> [p, q, r] = [i*p, j*q, k*r]`

有了這個想法就可以透過 [Array Formula][AF] 來做事。我在[解答範例][sample]中 Sheet *Answer 2* 的公式如下

``` text
=I3*PRODUCT((1-F3:H3)*(A2:C2)+(F3:H3*A5:C5))
+I4*PRODUCT((1-F4:H4)*(A2:C2)+(F4:H4*A5:C5))
+I5*PRODUCT((1-F5:H5)*(A2:C2)+(F5:H5*A5:C5))
```

[sample]: /files/sample2.xlsx
[AF]: https://support.office.com/en-us/article/guidelines-and-examples-of-array-formulas-7d94a64e-3ff3-4686-9372-ecfd5caa57c7
