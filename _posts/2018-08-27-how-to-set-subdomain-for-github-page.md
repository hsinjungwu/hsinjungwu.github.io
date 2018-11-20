---
layout: post
title:  "如何在 Github Page 上設定子網域"
date:   2018-08-27 11:51:54
tags:  
  - GitHub
  - Goddady
---

這個糾結我一下子。

<!-- more -->

最近在整理之前收集到的曹操傳單機版文章，原本想單純用 `www.hjwu.me/CaoCao-Mods`, 但看到這篇[網址 URL 英文大小寫是否有差別？](https://blog.gtwang.org/web-development/url-lower-and-upper-case/)後，決定把它改成 `game.hjwu.me` 吧！

我是在 [Goddady](https://tw.godaddy.com/) 買的網域，增加子網域的方式如下

> 新增一筆 CNAME 紀錄，其中【主機】填上 `game`，【指向】填上 `@` 就好

至於在 GitHub 這篇則是按照以下方式即可

1. 新增 CNAME 檔案，內容是 `game.hjwu.me`
2. 調整 _config.yml

``` diff
- baseurl: "/CaoCao-Mods"
- url: "https://hjwu.github.io/"
+ baseurl: ""
+ url: "https://hjwu.github.io/CaoCao-Mods"
```
