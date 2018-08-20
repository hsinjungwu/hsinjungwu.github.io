---
layout: post
title:  "Elements Of Slot Design"
date:   2017-12-26 12:07:54
categories: SlotDesign
tags:
  - math
  - combination
---

最近剛好 Google 到這篇 [Elements of Slot Design](http://slotdesigner.com/wp/wp-content/uploads/Elements-of-Slot-Design-2nd-Edition.pdf)，內容是關於 Slot Game 的設計，感覺可以拿來當高中機率、排列組合期中考題。 :laughing:

<!-- more -->

## Base Game

所謂的 *Base Game* 是指一般玩遊戲的情況。

* 一開始先介紹什麼叫做 *RTP (Return To Player)*，簡單說就是每投注 1 塊的期望值 * 100%。
* 既然提到了期望值，那勢必要算出每種 winning combination 的機率。由於最終的組合數結果眾多，與其用 *機率* 不如用 *次數* (這樣就會是整數而非分數) 來看會比較舒服。
* Hit Rate 跟 Hit Frequency，我自己的理解是數字小於 1 表示每場比賽出現這個事件的機率，大於 1 表示要多少場比賽會出現這個事件。
* 特殊牌 : **SCATTER**，只要出現就算中獎。當然這在實際遊戲中的規則會更加多樣化，這樣才會吸引人。
* 特殊牌 : **WILD**，就跟撲克牌中的鬼牌一樣，可替代任意牌。在實務中有些規則是 **WILD** 無法取代 **SCATTER**。
* 優先權。當遇到 `{W, W, A}` 的組合時，你可以把它看做 `{A, A, A}` 也可以看成是 `{B, B, #B}` 的情況。這時如果你很佛心的話，你可以兩種賠金都給。不過基本上都是挑高的賠，也因此在計算時要扣掉這種情形。
* 通常我們只考慮一種 winning combination。這是因為它的數量對 *RTP* 的影響相當小，所以當組合增加了，那只要增加每次最小投注金額單位即可。例如增加成 9 種 winning combinations，那只要讓每次投注最小單位變成 9 元，這樣可以讓 *RTP* 幾乎不被影響。

## Free Game

所謂的 *Free Game* 是指在玩 *Base Game* 時觸發的免投注遊戲。而這時的 *RTP* 計算方式(基於投注 1 塊的情形)也很簡單

<katex centred="true">\frac{M_b + M_f\times N_b\times P_b\times\frac{1}{1-N_f\times P_f}}{1}\times 100\%</katex>

其中 <katex>M_b(M_f)</katex> 表示在 *base(free) game* 贏得的錢期望值，<katex>N_b(N_f)</katex> 表示 *base(free) game* 下觸發幾場 *free game*。至於 <katex>P_b(P_f)</katex> 表示在 *base(free) game* 下觸發 *free game* 的機率。

至於為什麼有 <katex>1-N_f\times P_f</katex>，因為在 *free game* 下也可能觸發 *free game*，這時就會碰到無窮級數啊～ :cry:

## 小結

作者在第五章 *ANALYSIS OF GAME* 有提供範例，但是它文中的計算部份寫得不那麼詳細也有些錯誤，所以我就直接把[範例](/files/sample.xlsx)寫出來，有興趣的人可以參考。

另外這回是走馬看花的翻過，文中提到的 *Virtual Reel*、*243 WAYS GAMES* 等等都還沒詳細研究，或許等之後有機會接觸時再鑽研。