---
layout: post
title:  "Difference between const and readonly"
date:   2018-05-15 12:51:54
categories: Syntax
tags:  
  - C#

---

又踩到了雷。 :bomb:

拿同事建置的共用工具 dll 來執行時跳錯，稍微看了一下發現是 `const` 與 `readonly` 搞的鬼。

基本上在 *Microsoft Docs* 裡的 [常數 (C# 程式設計手冊)](https://docs.microsoft.com/zh-tw/dotnet/csharp/programming-guide/classes-and-structs/constants) 就寫得很清楚

> 當您參照其他程式碼中所定義的常數值 (例如 DLL) 時，請小心。 如果新版本的 DLL 定義常數的新值，則除非對新版本重新編譯新值，否則您的程式仍會保留舊常值。

而這篇討論 [What is the difference between const and readonly?](https://stackoverflow.com/questions/55984/what-is-the-difference-between-const-and-readonly) 的回答更詳細

> `AssemblyB` references `AssemblyA` and uses these values in code. When this is compiled,
>
> + in the case of the const value, it is like a find-replace, the value 2 is 'baked into' the `AssemblyB`'s IL. This means that if tomorrow I'll update `I_CONST_VALUE` to 20 in the future. `AssemblyB` would still have 2 till I recompile it.
> + in the case of the readonly value, it is like a ref to a memory location. The value is not baked into `AssemblyB`'s IL. This means that if the memory location is updated, `AssemblyB` gets the new value without recompilation. So if `I_RO_VALUE` is updated to 30, you only need to build `AssemblyA`. All clients do not need to be recompiled.

所以這篇結論翻譯成中文就是除非你能保證這個數字不會變，不然還是用 `readonly` 啊～ (這篇根本在騙文章數 :smoking: