---
layout: post
title:  "讓我誤解的屬性設定"
date:   2018-03-13 12:07:54
categories: "Syntax"
tags:
  - C#
---

今天踩到了雷。 :bomb:

<!-- more -->

程式碼如下：

``` cs
class A
{
  private int[] _c = { 10 };

  public int[] C
  {
    get
    {
      int[] tmp = new int[1];
      tmp[0] = _c[0];
      return tmp;
    }

    set
    {
      int[] tmp = value;
      _c[0] = tmp[0];
    }
  }

  public void ResetC()
  {
    C[0] = 5;
  }

  public void Reset_c()
  {
    _c[0] = -7;
  }
}
```

我一開始很理所當然的認為 `ResetC` 會讓 `C[0] = 5`，但跑出來結果卻沒有被改到。仔細想了一下才發現：

> 當我拿 `C` 的時候，它先將`_c` 標籤的這顆球的內容塞給貼有 `tmp` 標籤的這顆球，接著再把 `tmp` 球給我。因此我執行 `ResetC` 時是改 `tmp` 的內容，`_c` 球沒有改到內容，所以值永遠不會變。

而 `Reset_c` 因為是直接改 `_c` 所以結果是正確的。

另外如果寫成下面這樣就不會有這種問題了。

``` cs
class A
{
    private int[] _b = { 1 };

    public int[] B
    {
        get { return _b; }
        set { _b = value; }
    }

    public void ResetB()
    {
        B[0] = 7;
    }

    public void Reset_b()
    {
        _b[0] = 4;
    }
}
```