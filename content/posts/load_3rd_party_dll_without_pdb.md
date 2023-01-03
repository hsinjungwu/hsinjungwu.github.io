---
title: "免 PDB 載入第三方 lib"
date: 2023-01-03T20:25:00+08:00
draft: false
dropCap: false
tags:
  - "HowTo"
---

年紀到了，再更詳細記錄 [Visual Studio 技巧 - 深入第三方程式庫逐行偵錯](https://blog.darkthread.net/blog/vs-debug-3rdpty-lib/) 寫的方法，以免忘了。

### 如何開啟 Modules 視窗
+ 在偵錯時選取 ➡ 偵錯Windows ➡ 模組
+ 按 {{< kbd Ctrl >}} + {{< kbd Alt >}} + {{< kbd U >}}

### 如何 Decompile Source to Symbol File
+ 執行全部中斷(Break All)
+ 按 {{< kbd Ctrl >}} + {{< kbd Alt >}} + {{< kbd Break >}}[^1]

[^1]: [Break鍵](https://zh.m.wikipedia.org/zh-tw/Break%E9%8D%B5)