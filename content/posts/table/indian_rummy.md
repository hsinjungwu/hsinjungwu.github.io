---
title: "Indian Rummy(印度拉米)"
date: 2021-09-30T10:20:00+08:00
draft: false
dropCap: false
categories:
  - "Melding game"
tags:
  - "Rummy"
  - "Cards"
libraries:
  - katex
---

一般來說有 13 張牌跟 21 張牌的玩法，目前最流行的為 13 張牌。以下內容都以 13 張牌玩法為主。

<!--more-->

## 基本規則

主要參考[這裡](https://www.rummycircle.com/how-to-play-rummy/rummy-rules.html)

### 流程

1. 玩家 2 ~ 6 人以內，使用 2 副 (52+1) 張牌。
2. 每人發 13 張。剩餘牌稱為 Closed Deck。
3. 將 Closed Deck 上的第一張牌放在 Open Deck 上，並隨機抽選 Closed Deck 裡的一張牌，與它相同點數的牌做為 Wild。
   - 如果 Wild 是鬼牌，則所有的 A 都是 Wild。
   - 被選到的牌無法被使用
4. 玩家抽取(_draw_) Open 或 Closed Deck 的第一張牌至手中並理牌(_meld_)，想辦法湊成 2 組以上有效的牌型組合，總張數需為 13 張。
   - 如果 Open Deck 的第一張牌是 Wild，不能選。
5. 理牌完成。
   - 若完成目標，丟棄多餘的牌至完成區(_Show_)上，並攤開組合好的手牌，成為贏家。
   - 否則丟棄(_discard_)不要的牌至 Open Deck 上。
6. 輸家將根據自己的手牌內容，決定懲罰點數。

### 牌型

- Pure Sequence：即同花順，數字順序為 A > K > Q > J > 10 > ~ > 2 > A，張數至少 3 張。
- Impure Sequence：混同花順，即可以加入 Wild, Joker 組合。數字順序跟 Pure Sequence 一樣，張數至少 3 張。
- Set：相同點數但花色不能相同，可以加入 Wild, Joker 組合。張數為 3 或 4 張。

{{< alert theme="info" dir="ltr" >}}
有效牌型組合至少要有：1 Pure Sequence(_First Life_) + 1 Sequence(_Second Life_)。
{{< /alert >}}

### 懲罰點數

點數計算規則如下：

- A, K, Q, J 十點。
- 2 ~ 10，則是跟牌面點數一樣
- Wild, Joker 不計點數。

當有人贏牌了，累計所有無效牌點數，但上限為 80(_Full Count_)。

- 有 _First Life_ 跟 _Second Life_：無法湊成有效牌組的牌都是無效牌。
- 有 _First Life_ 但沒有 _Second Life_：除了 _First Life_ 之外的牌都是無效牌。
- 沒有 _First Life_：所有牌都是無效牌。

特殊情況：

1. 還沒摸牌即投降(aka _First Drop_)：20 點。
2. 還沒有人贏牌即投降(aka _Middle Drop_)：40 點。
3. 炸胡：80 點。
4. Consecutive Misses：如果有玩家連續三次失誤(我猜是沒拿牌？)，即判定為 _Middle Drop_
5. 離桌(_Leave Table_)也視為 _Middle Drop_。

## 遊戲種類

### [Points Rummy](https://www.rummycircle.com/rummy-variations/points-rummy.html)

先規定每一個懲罰點數為多少錢，當玩家輸多少點就要賠付對應的金額。

<div>
$$
\text{贏家獲勝金額}= \sum\limits_{i=1}^{6}\min(80, \text{對手 i 輸的點數})\times\text{每點的金額} - \text{抽水}
$$
</div>

### [Pool Rummy](https://www.rummycircle.com/rummy-variations/pool-rummy.html)

1. 遊戲開始前每個玩家丟入固定金額至獎池，並規定懲罰上限(一般為 101 或 201)。
2. 每回比賽玩家累計懲罰點數。當有人點數累計達到上限即出局。
3. 最後留下來的玩家為贏家。
4. 201 的 First Drop, Middle Drop 懲罰點數分別改為 25, 40

<div>
$$
\text{贏家獲勝金額} = \text{彩池所有錢} - \text{抽水}
$$
</div>

### [Deal Rummy](https://www.rummycircle.com/help/deals-rummy/format.html)

玩法像是 Points Rummy 跟 Pool Rummy 混合。

1. 先決定玩多少局(通常為 2~3 局)，並且每人攜帶 (玩家人數 x 80) 的籌碼入場，並丟固定金至彩池。
2. 每局玩法跟 Pool Rummy 一樣，只是是用籌碼做為賠付。
3. 所有局數都完成後，擁有最多籌碼的人為最後贏家。

<div>
$$
\text{贏家獲勝金額} = \text{彩池所有錢} - \text{抽水}
$$
</div>
