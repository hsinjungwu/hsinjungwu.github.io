---
title: "Pok Deng(博丁)"
date: 2021-10-01T13:14:00+08:00
draft: false
dropCap: false
categories:
  - "Banking game"
tags:
  - "Cards"
libraries:
  - katex
---

[ป๊อกเด้ง(Pok Deng)](https://en.wikipedia.org/wiki/Pok_Deng)為泰國知名遊戲，玩法[^1]類似[推筒子](https://zh.wikipedia.org/wiki/%E6%8E%A8%E7%AD%92%E5%AD%90)。

試玩連結：[Pok Deng](https://m13.ns86.kingmakergames.co/games/pok-deng/index.html?&lang=en)

{{< youtube -bV7TDTmXUY >}}

<!--more-->

## 流程

假設遊戲有 4 人：甲、乙、丙、莊家:

1. 依序由甲、乙、丙、莊家發牌，先各發 2 張手牌。
2. 甲、乙、丙根據自己的手牌決定是否再要第 3 張牌。
   - 如果有人的前兩張手牌點數低於 4 點，則必須自動補牌。
3. 莊家可隨機找甲、乙、丙來比牌。假設先找甲、乙分別比牌。
4. 莊家再補 1 張牌，然後跟還沒比牌的人(也就是丙)來比牌。
5. 最後：莊家看對甲(乙、丙)各輸贏多少錢，然後結算。

## แต้ม/taem/點數

1. A = 1; 2 ~ 9 = 自己的點數, 10,J,Q,K = 0
2. 牌型點數 = 全部加總後的個位數。

## 牌型

由大到小排序：

1. ป๊อก/Pok
   - ป๊อกแปด/Pok Kao/博九(兩張和 = 9)
   - ป๊อกเก้า/Pok Paet/博八(兩張和 = 8)
2. ตอง/Tong/三條
   - KKK > QQQ > JJJ > ... > 222 > AAA
3. สามเหลือง/Sam lueang/三公
   - KKQ > KKJ > KQQ > KQJ > KJJ > QQJ > QJJ
4. Normal/其他

## เด้ง/deng/倍數

- สองเด้ง/Song deng(2x) : 同花兩張, 一對
- สามเด้ง/Sam deng(3x) : 同花三張, 三張順子
  - 順子的順序為 `2-3-4-5-6-7-8-9-10-J-Q-K-A`
  - 沒有 KA2, A23
- 其他
  - 三公：3x
  - 三條：5x
  - 其他：1x

## 比牌

1. 先比牌型，贏家拿 [贏家的牌型倍數 x bet]
2. 如果牌型一樣，比點數，贏家拿 [贏家的牌型倍數 x bet]
3. 點數一樣，比倍數，贏家拿 [(贏家的牌型倍數-輸家的牌型倍數) x bet]
4. 如果還是一樣，就平手。

---

[^1]: [Pok Deng rule](https://uat.supports.kingmakergames.co/supports/games/pok-deng/rules?language=en)
