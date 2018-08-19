---
layout: post
title:  "修正 Broadcast DVR Server 大量佔用記憶體"
date:   2018-06-21 12:51:54
categories: "HowTo"
tags:  
  - Broadcast_DVR_Server
  - Chrome
  - Vivaldi
  - Edge
  - Internet_Explorer
---

最近開瀏覽器一直很腿啊～ :sleeping:

<!-- more -->

用 [Chrome][c] 跑測試網頁時一直很腿，於是開 [edge][e] 跟 [ie][i] 來看測試結果。但因為公司的 RD 說有些功能是不支援這兩款，於是下載了 [Vivaldi][v]，結果狀況是有改善。不過公司前輩還是請了 MIS 來幫忙，看是否需要新電腦。

MIS 來了之後便開啟工作管理員一一詢問我安裝的軟體，這時發現了疑犯 *Broadcast DVR Server*。經過這篇 [Broadcast DVR Server是什么进程 ? 很占内存](https://www.zhihu.com/question/35497403) 的說明

> 可能使用过win+g屏幕录制功能，并选择了“是的，这是一个游戏”。 一旦将某程序设定为游戏，每次打开这个程序，该进程Broadcast DVR server就会自动开启，内存使用直至崩溃为止。

我才想起我當初的確在 [chrome][c] 下有用 `win + g` 錄製影片，所以一切謎題都解開了！ :+1:

依照慣例還是要備份一下解法：

> 打开任务管理器，点击进程--内存，使程序使用内存量从大到小排列，然后将常用的程序依次打开，一旦发现Broadcast DVR server出现了，使焦点在该程序窗口，再次win+g，设置里取消“将其记为游戏”的勾选。退出后，再次打开该程序，不会再有Broadcast DVR server进程了。如果还有，重复以上步骤。

[c]: https://www.google.com.tw/chrome/index.html
[v]: https://vivaldi.com/?lang=zh_TW
[e]: https://www.microsoft.com/zh-tw/windows/microsoft-edge
[i]: https://support.microsoft.com/zh-tw/help/17621/internet-explorer-downloads