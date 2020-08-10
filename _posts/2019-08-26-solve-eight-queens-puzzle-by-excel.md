---
layout: post
title:  "使用 Excel 解決八皇后問題"
date:   2019-08-26 10:20:04
tags:  
  - Excel
  - Eight_Queens_Puzzle 
---

* content
{:toc}

剛好看到這篇 [用excel解决八皇后问题](https://zhuanlan.zhihu.com/p/43301962)，忍不住手癢。

<!-- more -->

一樣先介紹[八皇后問題](https://zh.wikipedia.org/wiki/%E5%85%AB%E7%9A%87%E5%90%8E%E9%97%AE%E9%A2%98)

> 八皇后問題是一個以西洋棋為背景的問題：如何能夠在8×8的西洋棋棋盤上放置八個皇后，使得任何一個皇后都無法直接吃掉其他的皇后？為了達到此目的，任兩個皇后都不能處於同一條橫行、縱行或斜線上。

該篇作者 [游戏人恩皮西](https://zhuanlan.zhihu.com/gamehacker) 的想法是每次挑選剩下的第 n 小的數字，然後把 `8!` 種組合全部列出來。他透過了 `字串` 與 EXCEL 內建函數 [MOD](https://support.office.com/zh-tw/article/mod-%E5%87%BD%E6%95%B8-9b6cd169-b6ee-406a-a97b-edf2a9dc24f3)、[VLOOKUP](https://support.office.com/zh-hk/article/vlookup-%E5%87%BD%E6%95%B8-0bbc8083-26fe-4963-8ab8-93a18ad188a1)、[MID](https://support.office.com/zh-hk/article/mid%E3%80%81midb-%E5%87%BD%E6%95%B8-d5f9e25c-d7d6-472e-b568-4ecb12433028) 等等完成。

我試著跟他的思路複刻了一份 [解法1](/files/eight_queens_puzzle/8QueensSol1.xlsx)，但檔案蠻大且使用起來也卡卡的。所以我調整了一下判斷方式。邏輯如下：

1. 從最左邊的 Col. 1 中列出可用的組合 1 ~ 8。
2. 接著 Col. 2 只剩下 7 種數字來搭配，因此有 8x7 = 56 種可用組合。
3. 縮減這 56 種組合為 42 種有效組合。
4. 接著再往 Col. 3 做，只剩下 6 種數字搭配，因此有 42x6 = 252 種可用組合。
5. 縮減這 252 種組合為 140 種有效組合。
6. 依此類推直到最後只剩下 92 種有效組合。

有興趣的可以參考 [解法2](/files/eight_queens_puzzle/8QueensSol2.xlsx)，檔案約小了 300 倍。 :smile:

另外在實做時有遇到下面兩個小問題，也附上參考解答。

1. [How to lookup first and last match](https://exceljet.net/how-to-lookup-first-and-last-match)。
2. [寫完公式不必下拉](http://forum.twbts.com/thread-3941-1-1.html)