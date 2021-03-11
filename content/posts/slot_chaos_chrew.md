---
title: "[Hacksaw Gaming] Chaos Crew"
date: 2021-03-11T02:13:00+08:00
draft: false
dropCap: false
categories:
    - "Slot"
tags:
    - "Line Game"
    - "5x5"
    - "Multiplier Wild"
    - "Lightning Cash"
    
---

試玩連結 : https://www.hacksawgaming.com/games/chaos-crew

{{< youtube pDwDO4j7uqs >}}

<!--more-->

## Info

1. RTP : Normal 96.3%，buy 95.92%
2. Hit Rate 23.4%
3. Max Win : 10000x
4. 5x5 15 線

## Payouts (total bet 1)
![payouts](https://i.imgur.com/XWbuBl0.png)

## Feature
1. Base Game : 隨機倍數百搭，倍數有 2x, 3x 跟 5x。如果同一條線上有多個倍數，倍數計算為**相乘**。
2. Free Game : R1, R3 跟 R5 的 3 顆 Scatter 觸發。玩法同 Lightning Cash。
    + 每個滾輪初始倍數都為 +1
    + 每個滾輪上都有 x2, x3, x5, x10, x20, +1, +2, +5, +10, +20，影響範圍為單一滾輪或所有滾輪。
    + 計算方式為先從 R1-1 ➟ R1-5 ➞ R2-1 ➟ R5-5

## 大獎畫面

+ BG 單把 72x
![72x](https://i.imgur.com/XiglQ1v.jpg)
+ FG 離開 1510x **Epic Win**
![1510x](https://i.imgur.com/2vj4ImS.jpg)
+ FG 離開 2424x **Epic Win**
![2424x](https://i.imgur.com/yP8d1BH.png)

## FG 計算

定義每次回滿血為一個回合

+ 在第 $k$ 回合開始，每個滾輪起始值為 $n_{i,k}$，其中 $n_{i,1}=1$。 
+ 影響自己滾輪的函數為 $f_i$ 且 $f_i$ 為線性。
+ 影響其他滾輪的為函數 $g_i$ 且 $g_i$ 為線性。
+ 盤面完全不中的的機率為 $P$。

則第 $k$ 回合死掉結算期望值為

<div>
$$
(n_{1,k}+n_{2,k}+n_{3,k}+n_{4,k}+n_{5,k})\times P^3 \times (1-P^3)^{k-1}
$$
</div>

其中

<div>
$$
\begin{aligned}
n_{1,k+1} &= \big(g_5\circ g_4\circ g_3\circ g_2\circ f_1(n_{1,k})\big)-P\times n_{1,k}\\
n_{2,k+1} &= \big(g_5\circ g_4\circ g_3\circ f_2\circ g_1(n_{2,k})\big)-P\times n_{2,k}\\
n_{3,k+1} &= \big(g_5\circ g_4\circ f_3\circ g_2\circ g_1(n_{3,k})\big)-P\times n_{3,k}\\
n_{4,k+1} &= \big(g_5\circ f_4\circ g_3\circ g_2\circ g_1(n_{4,k})\big)-P\times n_{4,k}\\
n_{5,k+1} &= \big(f_5\circ g_4\circ g_3\circ g_2\circ g_1(n_{5,k})\big)-P\times n_{5,k}
\end{aligned}
$$
</div>