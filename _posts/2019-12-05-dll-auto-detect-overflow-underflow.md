---
layout: post
title:  "dll 如何自動檢查溢位"
date:   2019-12-05 15:51:54
tags:  
  - C#
---

原本以為很麻煩，要到處寫 [checked](https://docs.microsoft.com/zh-tw/dotnet/csharp/language-reference/keywords/checked)，後來發現只要[調整設定](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/compiler-options/checked-compiler-option)就好。

![dll auto check overflow/underflow](/files/dll-check.png)