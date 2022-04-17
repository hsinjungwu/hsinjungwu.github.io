---
title: "[Hacksaw Gaming] Chaos Crew"
date: 2021-03-11T02:13:00+08:00
draft: false
dropCap: false
categories:
  - "Line Game"
tags:
  - "Multiplier Wild"
  - "Lightning Cash"
libraries:
  - katex
---

遊戲試玩：[Chaos Crew](https://www.hacksawgaming.com/games/chaos-crew)

{{< youtube pDwDO4j7uqs >}}

<!--more-->

## 基本資料

1. RTP : Normal 96.3%，buy 95.92%
2. Hit Rate 23.4%
3. Max Win : 10000x
4. 5x5 15 線
5. Payouts (total bet 1)
   ![payouts](https://i.imgur.com/XWbuBl0.png)

## 遊戲特色

1. Base Game : 隨機倍數百搭，倍數有 2x, 3x 跟 5x。如果同一條線上有多個倍數，倍數計算為**相乘**。
2. Free Game : R1, R3 跟 R5 的 3 顆 Scatter 觸發。玩法同 Lightning Cash。
   - 每個滾輪初始倍數都為 +1
   - 每個滾輪上都有 x2, x3, x5, x10, x20, +1, +2, +5, +10, +20，影響範圍為單一滾輪或所有滾輪。
   - 計算方式為先從 R1-1 ➟ R1-5 ➞ R2-1 ➟ R5-5

## 大獎截圖

{{< img src="https://i.imgur.com/XiglQ1v.jpg" caption="BG 72x" alt="72x"  position="center" >}}

{{< img src="https://i.imgur.com/2vj4ImS.jpg" caption="FG 1510x Epic Win!!" alt="1510x"  position="center" >}}

{{< img src="https://i.imgur.com/yP8d1BH.png" caption="FG 2420x Epic Win!!" alt="2420x"  position="center" >}}

## 遊戲體驗

1. 畫面 5x5 只有 15 線感覺很少見，像是因為 FG 需要 5x5 才讓 BG 也是這樣大小。
2. 走線的設計除了 2 條對角線之外，其他沒有跨越 3 列。因此圖標的堆疊反而是擋路，有時會有種畫面很多但分數普普的感覺。
3. 免費遊戲進場頻率覺得還行，沒有到太硬。

## 試算評估

{{< expand "計算方式" >}}
定義每次回滿血為一個回合

- 在第 $k$ 回合開始，每個滾輪起始值為 $n_{i,k}$，其中 $n_{i,1}=1$。
- 影響自己滾輪的函數為 $f_i$ 且 $f_i$ 為線性。
- 影響其他滾輪的為函數 $g_i$ 且 $g_i$ 為線性。
- 盤面完全不中的的機率為 $P$。

則第 $k$ 回合死掉結算期望值為

<div>
$$
(n_{1,k}+n_{2,k}+n_{3,k}+n_{4,k}+n_{5,k})\times P^3 \times (1+P+P^2)^{k-1}
$$
</div>

其中

<div>
$$
\begin{aligned}
n_{1,k+1} &= g_5\circ g_4\circ g_3\circ g_2\circ f_1(n_{1,k})-P\times n_{1,k}\\
n_{2,k+1} &= g_5\circ g_4\circ g_3\circ f_2\circ g_1(n_{2,k})-P\times n_{2,k}\\
n_{3,k+1} &= g_5\circ g_4\circ f_3\circ g_2\circ g_1(n_{3,k})-P\times n_{3,k}\\
n_{4,k+1} &= g_5\circ f_4\circ g_3\circ g_2\circ g_1(n_{4,k})-P\times n_{4,k}\\
n_{5,k+1} &= f_5\circ g_4\circ g_3\circ g_2\circ g_1(n_{5,k})-P\times n_{5,k}
\end{aligned}
$$
</div>
{{< /expand >}}

{{< alert theme="info" dir="ltr" >}}
FG 計算是可以透過 Excel 直接求出，但調性可能不太容易直接使用自然機率調整，或許要利用一些條件計加以控制玩家體驗。
{{< /alert >}}

## 結論

{{< boxmd >}}
這種 FG 只看倍數的規則簡單，追求目標也很明確。在 [Relax Gaming](https://relax-gaming.com/) 的 [Money Train 2](https://relax-gaming.com/products/casino/moneytrain2)、[Nolimit City](https://www.nolimitcity.com/) 的 [FIRE IN THE HOLE XBOMB](https://www.nolimitcity.com/games/fire-in-the-hole-xbomb/) 等等都有出現且成績也算不錯，或許可以實做這個特色。
{{< /boxmd >}}
