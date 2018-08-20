---
layout: post
title:  "C# 中一個 & 跟兩個 & 的差異"
date:   2018-03-02 12:07:54
tags:
  - C#
---

同事 A 看到同事 B 在寫判斷式時只用了一個 `&` 卻會 compile 過，跑來問我怎麼會這樣？ :open_mouth:

<!-- more -->

雖然我覺得是同事 B 少打一個 `&` 啦～ :sweat_smile: 但這個用法確實有在 [& 運算子 (C# 參考)](https://docs.microsoft.com/zh-tw/dotnet/csharp/language-reference/operators/and-operator) 中提到：

> 不論第一個運算子的值為何，& 運算子都會評估兩個運算子。

所以如果採用了下面的範例

``` cs
private static void Main(string[] args)
{    
    if (HelloAmpersand() & HelloAmpersand()) Console.WriteLine("single");
    Console.WriteLine("================");
    if (HelloAmpersand() && HelloAmpersand()) Console.WriteLine("double");
    Console.ReadLine();
}

private static bool HelloAmpersand()
{
    Console.WriteLine("ampersand!!");
    return false;
}
```

回傳的結果將是下面這樣，同理 `|` 也是一樣。

``` text
ampersand!!
ampersand!!
================
ampersand!!
``` 