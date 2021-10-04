---
title: "圖論兩三事"
date: 2020-10-01T04:59:00+08:00
draft: false
dropCap: false
categories:
  - "Math"
---

八年前跟朋友吃飯時有感而發寫的文章。

<!--more-->

---

前一陣子在吃晚餐時友人問我[圖論](http://en.wikipedia.org/wiki/Graph_theory)在講什麼，我瞬間尷尬了一下，然後不好意思地說這是我讀研究所時的主修科目，接着稍微想了一下開始介紹給友人聽。

## 起源

這門學問起源於[七橋問題](http://en.wikipedia.org/wiki/Seven_Bridges_of_K%C3%B6nigsberg)，然後大數學家 [Leonhard Euler](http://en.wikipedia.org/wiki/Leonhard_Euler) 就把它解了出來，於是就開啓了我的痛苦之路。 😨

## 簡介

它的「圖」跟我們傳統認知上的「圖」是不同的。

現在說的「圖」簡單說就是給你一堆「點」，而兩「點」之間可以有線相連。而我們稱這條線為「邊」一般而言，兩「點」之間最多只有一條「邊」相連，而這種「圖」，我們稱它為 _Simple Graph_，反之若是有超過一條「邊」相連，我們稱之為 _Multigraph_。至於更複雜的 [hypergraph](http://en.wikipedia.org/wiki/Hypergraph) 我就不介紹了。

而我當時在做研究時都只考慮 _Simple Graph_。

當給定「點」的數目時，我們幫不同種「邊」排列組合的結構而給了特定名字。如

- [path](https://en.wikipedia.org/wiki/Path_graph)
- [tree](<https://en.wikipedia.org/wiki/Tree_(graph_theory)>)
- [cycle](http://en.wikipedia.org/wiki/Cycle_graph)
- [bipartie graph](http://en.wikipedia.org/wiki/Bipartite_graph)
- [complete graph](http://en.wikipedia.org/wiki/Complete_graph)

## 著色

接着數學家開始考慮「點」可以塗上顏色，然後「邊」也可以開始著色，最後開啓了 [graph coloring](http://en.wikipedia.org/wiki/Graph_coloring) 這門學問！而在這方面最廣為人知的東西就是[四色定理](http://en.wikipedia.org/wiki/Four_color_theorem)。

在讀碩士班時雖然我的論文題目有使用 _coloring_ ，不過嚴格說起來跟正規的 _graph coloring_ 是不同的。我做的東西在經過[翁志文](http://jupiter.math.nctu.edu.tw/~weng/weng.htm)教授跟我正名過後，題目應該要改成「Lit-only $\sigma$-game」。

而在博一那年我整個人沈溺在 [total coloring conjecture](http://en.wikipedia.org/wiki/Total_coloring)，當然我是沒有好下場的。第一年資格考沒過後，我就直接休學，接著隔年沒去復學就被退學了。 🤣

## 其他

在講完上面這些後，晚餐也差不多結束了。其他的[專業術語](http://en.wikipedia.org/wiki/Glossary_of_graph_theory)，我也不想多提，因為我已經差不多快忘了！ 😉
