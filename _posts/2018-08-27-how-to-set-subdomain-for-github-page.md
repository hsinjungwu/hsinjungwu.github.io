---
layout: post
title:  "如何在 Github Page 上設定子網域"
date:   2018-08-27 11:51:54
tags:  
  - GitHub
  - Goddady
---

**原文已更新**

<!-- more -->

### UPDATE @ 20190210

今天發現 [game.hjwu.me](https://game.hjwu.me) 跳出不安全的網站認證，點進去 Repositories 設定頁面發現出現 **Domain does not resolve to the GitHub Pages server.**

查了一下應該是增加子網域的方式有誤，後來調整如下：

> 新增一筆 CNAME 紀錄，其中【名稱】填上 `game`，【值】填上 `hsinjungwu.github.io` 就好

另外也看到這篇 [GitHub 透過 Let's Encrypt 提供自訂網域的 HTTPS 服務](https://blog.gslin.org/archives/2018/05/02/8295/github-%E9%80%8F%E9%81%8E-lets-encrypt-%E6%8F%90%E4%BE%9B%E8%87%AA%E8%A8%82%E7%B6%B2%E5%9F%9F%E7%9A%84-https-%E6%9C%8D%E5%8B%99/) 提到

> 不過目前只支援 CNAME record (標準) 或是 ALIAS record 的方式 (非標準，也稱為 ANAME，有些 DNS provider 有支援，主要用在網域本身 (i.e. root domain) 無法使用 CNAME)。

我想應該是這個原因造成認證失效，後來修正完後隔一陣子就變安全認證了。 :+1:

### oringinal post

這個糾結我一下子。

最近在整理之前收集到的曹操傳單機版文章，原本想單純用 `www.hjwu.me/CaoCao-Mods`, 但看到這篇[網址 URL 英文大小寫是否有差別？](https://blog.gtwang.org/web-development/url-lower-and-upper-case/)後，決定把它改成 `game.hjwu.me` 吧！

我是在 [Goddady](https://tw.godaddy.com/) 買的網域，增加子網域的方式如下

> ~~新增一筆 CNAME 紀錄，其中【主機】填上 `game`，【指向】填上 `@` 就好~~

至於在 GitHub 這篇則是按照以下方式即可

1. 新增 CNAME 檔案，內容是 `game.hjwu.me`
2. 調整 _config.yml

``` diff
- baseurl: "/CaoCao-Mods"
- url: "https://hjwu.github.io/"
+ baseurl: ""
+ url: "https://hjwu.github.io/CaoCao-Mods"
```
