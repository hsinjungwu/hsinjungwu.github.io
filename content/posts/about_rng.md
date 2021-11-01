---
title: "關於亂數產生器"
date: 2021-11-01T10:20:00+08:00
draft: false
dropCap: false
categories:
  - "WHY"
tags:
  - "Random Number Generator"
---

剛好看到 [亂數產生器：Random 與 RNGCryptoServiceProvider](https://blog.miniasp.com/post/2008/05/13/Random-vs-RNGCryptoServiceProvider)，想到當年回台中面試 [新博](http://www.simbo.com.tw/) 有被問類似的題目。 

<!--more-->

文中的 **產生亂數** 的寫法會有一點不均勻的亂，他的做法跟下面的例子是一樣的。

> 當你中午有四家餐廳想吃，但不知該選那家。於是想用一顆六面骰來幫你決定，你的策略是超過 4 的取餘數。
> 
> 結果你發現你很常選到第 1, 2 家，因為他們的機率比選 3, 4 的還高。

而原文中的程式碼就出現了這個問題。雖然在指定範圍小的時候，這個誤差可以忽略，但當取值範圍夠大時問題就浮出來。

建議 **產生一個非負數的亂數** 調整為

```cs
public static int Next()
{
    rngp.GetBytes(rb);
    int value = BitConverter.ToInt32(rb, 0);
    if (value < 0) value -= int.MinValue;
    return value;
}
```

而 **產生一個非負數且最大值 max 以下的亂數** 調整如下。這部分的數學就不特別解釋了。🤭

```cs
public static int Next(int max)
{
    if (max == int.MaxValue) {
        return Next();
    }

    int bound = int.MaxValue - int.MaxValue % (max + 1);

    int value;
    do
    {
        value = Next();
    } while (value >= bound);

    value %= (max + 1);
    return value;
}
```