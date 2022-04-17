---
title: "Treasure Dash"
date: 2021-10-01T10:20:00+08:00
draft: false
dropCap: false
categories:
  - "Arcade game"
tags:
  - "橫向捲軸"

libraries:
  - katex
---

類似 [超級瑪利(Super Mario Bros.)](https://zh.wikipedia.org/wiki/%E8%B6%85%E7%BA%A7%E9%A9%AC%E5%8A%9B%E6%AC%A7%E5%85%84%E5%BC%9F) 的遊戲。

{{< youtube t5O3S5UrsWc >}}

<!--more-->

## 遊戲封包

回傳的內容看起來像是 1 次回傳多個贏分結果。

```xml
<!--base game-->
<Games>
    <Game clientTag ="2" state="1" hp="1" distance="0" bestRecord="63" requiredPlayAmount="200" cumulativePlayAmount="26" remainingFreePlayAmount="0">
        <Multiplier latest="1" totalWin="10" freeBonusTotalWin="1"></Multiplier>
    </Game>
    <Game clientTag="1" state="1" hp="1" distance="0" bestRecord="63" requiredPlayAmount="200" cumulativePlayAmount="26" remainingFreePlayAmount="0">
        <Payout latest="1100" totalWin="1100" freeBonusTotalWin="0"></Payout>
    </Game>
</Games>

<!--free game-->
<Games>
    <Game clientTag="1" state="2" hp="1" distance="0" bestRecord="63" requiredPlayAmount="200" cumulativePlayAmount="0" remainingFreePlayAmount="5">
        <Payout latest="1200" totalWin="20740" freeBonusTotalWin="1200" />
    </Game>
    <Game clientTag="2" state="2" hp="1" distance="0" bestRecord="63" requiredPlayAmount="200" cumulativePlayAmount="0" remainingFreePlayAmount="4">
        <Multiplier latest="1" totalWin="2" freeBonusTotalWin="7" />
    </Game>
</Games>
```

## 觀察

1. 吃到 **倍數球** 會回傳 `<Multiplier/>`
   - latest = 當次 spin 增加的倍數
   - totalWin = 累計的倍數(已加上 latest)
2. 吃到 **分數球** 會回傳 `<Payout/>`。
   - latest = 倍數球累計的倍數轉成分數並加上分數球的分數
   - totalWin = 累計的贏分(已加上 latest)
3. 如果腳色死掉，累計的 spin 數會保留，不會歸零
   - 起始累計的 spin 數似乎是隨機
4. 切 bet 會重置累積次數
5. ClientTag:
   - for `<Payout/>` : NoWin = 0, Win = 1.
   - for `<Multiplier/>` : 2 ~ 9 (1x, 2x, 3x, 5x, 9x, 15x, 20x 跟 25x)
6. State:
   - 1: baseGame
   - 2: freeGame
   - 4: dead
