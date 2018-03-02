---
layout: post
title:  "修正 Windows 10 閒置一分鐘後自動進入螢幕保護程式"
date:   2018-02-22 12:07:54
categories: "HowTo"
tags:
  - Windows10
---

過完年回到公司，發現螢幕很快就變黑進入鎖定螢幕畫面。 :scream:　

<!-- more -->

上網查到這篇 [[問題] Win7閒置一分鐘後 螢幕會自動暗掉(非關閉](https://www.ptt.cc/bbs/Windows/M.1398429899.A.1BB.html) 裡面推文提到

> 就是螢幕保護程式阿 關掉或延長就不會這樣

我進入螢幕保護程式的設定[^1]，發現它設定成 1 分鐘，所以我改了 30 分鐘。結果 1 分鐘後又暗了，我打開螢幕保護程式設定，發現它還是 1 分鐘，想說該不會是要重開機吧！於是重設並重開機，結果還是一樣。 :expressionless:

後來找到 [Windows 10 Lock screen black after 1 minute](https://niallbest.com/windows-10-lock-screen-black-after-1-minute/) 這篇，我依樣畫葫蘆地按照他的解法，但看到裡面提到另一個登錄檔無效，所以我用該登錄檔當關鍵字查到了這篇 [windows 10 设置锁屏时间](https://partnersupport.microsoft.com/zh-hans/par_servplat/forum/par_winserv/windows-10/4994fbee-ef51-41c2-a90c-a853ed117701) 由於是 `microsoft.com` 裡的文章，我也按照他的方法修改。總之我的解法如下：

1. 修改登錄檔 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\238C9FA8-0AAD-41ED-83F4-97BE242C8F20\7bc4a2f9-d8fc-4469-b07b-33eb785aaca0` 跟 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\7516b95f-f776-4464-8c53-06167f40cc99\8EC4B3A5-6868-48c2-BE75-4F3044BE88A7` 為 2。
2. 設定螢幕保護程式的鎖定時間為 30 分鐘。
3. 重開機就好了。

----
[^1]: 題外話：我真心覺得 Windows 10 螢幕保護程式藏在很奇妙的地方，找不到的人可以參考這篇 [【教學】設定螢幕保護程式，鎖定電腦桌面自動登出預防他人使用](http://sky940811.pixnet.net/blog/post/338495222)