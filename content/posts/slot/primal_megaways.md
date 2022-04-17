---
title: "[Blueprint Gaming] Primal Megaways"
date: 2020-03-06T10:20:00+08:00
draft: false
dropCap: false
categories:
  - "MegaWays"
tags:
  - "All Win Multiplier"
  - "Mystery Symbol"
  - "Size 6+0"
libraries:
  - katex
---

遊戲試玩：[Primal Megaways](https://ogs-gcm-eu-prod.nyxop.net/gcm/gcm-launcher/launcher.html?currency=EUR&device=desktop&gameUrl=https%3A%2F%2Fnyxmaltargs.blueprintgaming.com%2Floader%2F%3Fenvid%3Deur&gameid=BP_Primal&lang=en-us&lobbyurl=&mode=demo&ogsgameid=380089&operatorid=405&sessionid=Free%3Aur49jihk66mn0nb5iaig5pbndij)

{{< youtube rts49cuyjmM >}}

<!--more-->

## 基本資料

1. RTP 96.76%
2. Payouts (total bet 1)
   ![paytable](https://i.imgur.com/GxsWEz9.jpg)

## 遊戲特色

1. 有 mystery symbol，但不會變成 `F` 跟 `W`
2. 進 FG 保證 10x 以上出來，如果沒有就一直加當次進入的 spin 數。
3. 3 ~ 6 顆 `F` 進 FG 給 10, 15, 20 跟 30 場，然後 Wild 倍數為 2 ~ 3(,4,5,6)，倍數採相乘。贏分計算方式有點奇妙。
4. FG 中 `2` 顆以上 `F` 就 retrigger。2 顆 5 場，其他的跟 BG 觸發場次一樣。

{{< expand "倍數計算範例" >}}
![倍數計算](https://i.imgur.com/JFuiASX.jpg)

它的百搭倍數是畫面有出現就相乘，所以是 `All Win x20`。接著 Way 的組合數為 `3x2x2x1x1x1=12`，所以結算為 `20x12 = 240` ways。原本以為是有經過走線才算倍數，且 Ways 採 `3x(4+1)x2x1x5x1` 計算方式有很大的落差。

計算上來說假設每滾輪出現 $x_i$ 個賠付圖標，每滾輪出現 $w_i < 2$ 個 `W` 且倍數為 $m_i > 1$。由於

<div>
$$
\prod{(x_i+m_i*w_i)} < \prod{(m_i(x_i+w_i))}
$$
</div>

所以賠付比我想的計算方式還要強！
{{< /expand >}}

## 遊戲體驗

1. FG 倍數採 All Win 是蠻好的，避免看的到吃不到的厭惡感，只是演繹方式可以調整，讓算分方式更明確。
2. 玩了 6、700 場進了 4 次 FG，其中有一次玩到 retrigger 4、5 次，最後 spin 了快 50 場，感覺蠻爽的。不知道是手氣好還是遇到腳本。 😏 另外試玩上結束的倍數都 100+ 倍感覺蠻甜的。![fg win](https://i.imgur.com/n56ZG7j.jpg)
3. 圖標有堆疊，畫面滿滿的爆分或卡線都蠻有記憶點。透過堆疊有在 BG 拿到 200+ 倍的高分，也算是一個爆點。![bg stack win](https://i.imgur.com/HcsYQ9l.jpg)
4. 沒有 Big Win 以上的大獎提示，但用爪痕跟左右兩側的圖騰發光算是蠻有氣勢的。
5. 保證 10x 離開的特色讓心情有點矛盾。尤其場次剩越少時，反而會期待不要中獎或是怕中太多超過 10x 的門檻。
6. 透過 `Mystery Symbol` 增加連線長度與廣度的期待，感覺蠻好的。

## 試算評估

{{< alert theme="danger" dir="ltr" >}}
目前沒有想到比較好的做法做出保證 10x 離開的特色。
{{< /alert >}}

## 結論

{{< boxmd >}}
我自己設計不會做保證 10x 離開的特色，會朝著 **把 RTP 放在提高倍數的權重** 方向去走。
{{< /boxmd >}}
