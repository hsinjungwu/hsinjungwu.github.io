---
layout: post
title:  "重啟"
date:   2016-02-28 19:51:54
categories: Jekyll
tags:
  - Jekyll
  - theme
  - KaTeX
---

* content
{:toc}

既然交了女朋友，重啟 blog 也是理所當然的事吧！ :couple_with_heart_woman_man:

<!-- more -->

## 改頭換面

部落格上方的標語 **流浪的種子** 與 **人生就是無限的延遲** 來自於 [伍佰](http://wubai.com) 新歌「種子」

> 我是一粒流浪的種子 人生就是無限的延遲

<iframe width="560" height="315" src="https://www.youtube.com/embed/V2Q1Y3q2rzo" frameborder="0" allowfullscreen></iframe>

而下方的 **前面的世界會更精彩** 則是某次在聽 [罗辑思维](https://www.youtube.com/channel/UCYpYY4G4T1PI-Jug8q6lNGA) 聽到，覺得很喜歡就拿來用。

曾選過 [Stack Problems](https://github.com/agusmakmun/agusmakmun.github.io)、[DevJournal](https://github.com/hemangsk/DevJournal) 與 [Freshman21](https://github.com/yulijia/freshman21) 但總覺得不對味。後來在 [GitHub](https://github.com) 上搜尋關鍵字 `topic:jekyll-theme` 終於選到自己喜歡的 theme [Gaohaoyang/gaohaoyang.github.io](https://github.com/Gaohaoyang/gaohaoyang.github.io)

## 引用 KaTeX

blog 中當然還是要寫數學，所以需要 [KaTeX](https://github.com/Khan/KaTeX)，原本寫的 `KatexTag.js` 如下，

``` js
(function(){
  $("katex").each(function(){
    var m = $(this).text();
    var c = $(this).attr("centred");
    if (!c) c = "false";
    var r;
    if (c.toLowerCase() == "true"){
      r = "<p class='mathblock'>" + katex.renderToString(m, { displayMode: true }) + "</p>";
    }
    else {
      r = katex.renderToString(m);
    }
    $(this).replaceWith(r);
  });
})();
```

但因為 theme 作者的這篇 [对这个 jekyll 博客主题的改版和重构](https://gaohaoyang.github.io/2016/03/12/jekyll-theme-version-2.0/) 裡提到

> 去掉 jQuery 和 BootStrap

所以就改寫成純 *JavaScript* 版。

``` js
(function(){
    var ka = document.querySelectorAll("katex");
    ka.forEach(function(k){
      var m = k.innerText || k.textContent;
      if (k.hasAttribute("centred")){
        k.innerHTML = "<p class='mathblock'>" + katex.renderToString(m, { displayMode: true }) + "</p>";
      }
      else {
        k.innerHTML = katex.renderToString(m);
      }
  });
})();
```

## 中文排版

在搜尋 theme 中找到這篇 [中文文案排版指北（简体中文版）](http://mazhuang.org/wiki/chinese-copywriting-guidelines/) 內容真的是於我心有戚戚焉！ :+1:
