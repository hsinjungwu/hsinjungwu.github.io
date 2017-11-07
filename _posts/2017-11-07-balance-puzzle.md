---
layout: post
title:  "稱球問題"
date:   2017-11-07 12:07:54
categories: Interview
tags:
  - Interview
  - algorithm
---

這題在大學時曾被問過，而最近在面試時或聽人面試過程時也出現，不知道這些面試官們為什麼這麼有志一同？ :expressionless:

<!-- more -->

題目如下

> 在 12 個球中有一個特殊球的重量與眾不同（不知道偏重還是偏輕），而其他球的重量全部相同，請用無砝碼的天平稱 3 次找出特殊球，並確定特殊球是偏輕還是偏重。

下面提供我的解法，如果對這個問題有更深的興趣的話可以參考 [Balance puzzle](https://en.wikipedia.org/wiki/Balance_puzzle)。不過就算解答出這題面試也不會上啊～哭哭 :sob:

### 前置作業：

一開始先將球分成 3 堆，以 <katex>\{ A_1, A_2, A_3, A_4 \}</katex>、<katex>\{ B_1, B_2, B_3, B_4 \}</katex> 與 <katex>\{ C_1, C_2, C_3, C_4 \}</katex> 記之。

接著有一個 **已知事實**：

> 已知三球其中一顆較重(輕)。任意取兩球相比，若一樣則沒秤到的球較重(輕)。若不同，則較重(輕)的球就是答案。

### 解法：

拿 <katex>\mathcal{L}_1 = \{ A_1, A_2, A_3, A_4 \}</katex> 與 <katex>\mathcal{R}_1 = \{ B_1, B_2, B_3, B_4 \}</katex> 進行第一次秤重，這時會有 3 種情形：

**Case 1：** <katex>\mathcal{L}_1 = \mathcal{R}_1</katex>

表示有問題的球在 <katex>\{ C_1, C_2, C_3, C_4 \}</katex> 裡。於是拿 <katex>\mathcal{L}_2 = \{ A_1, A_2, A_3 \}</katex> 與 <katex>\mathcal{R}_2 = \{ C_1, C_2, C_3 \}</katex> 進行第二次秤重，這時會有 3 種情形：

*Case 1.1：* 一樣重，表示有問題的是 <katex>C_4</katex>。所以拿 <katex>\mathcal{L}_3 = \{C_4\}</katex> 與 <katex>\mathcal{R}_3 = \{A_4\}</katex> 比就知道是輕還是重了。

*Case 1.2：* <katex>\mathcal{L}_2 > \mathcal{R}_2</katex>，表示 <katex>\{ C_1, C_2, C_3 \}</katex> 中有一顆比較輕。接著利用上面的 **已知事實**，我們秤第三次就能找到答案。

*Case 1.3：* <katex>\mathcal{L}_2 < \mathcal{R}_2</katex> 思路同 2。

**Case 2：** <katex>\mathcal{L}_1 > \mathcal{R}_1</katex> 

表示 <katex>\{ C_1, C_2, C_3, C_4 \}</katex> 是正常。於是我們拿 <katex>\mathcal{L}_2 = \{ A_1, A_2, A_3, B_4 \}</katex> 與 <katex>\mathcal{R}_2 = \{ C_1, C_2, C_3, A_4 \}</katex> 進行第二次秤重，這時會有 3 種情形：

*Case 2.1：* 一樣重，表示有問題的是 <katex>\{ B_1, B_2, B_3 \}</katex> 且其中有一顆比較輕。接著利用上面的 **已知事實**，我們秤第三次就能找到答案。

*Case 2.2：* <katex>\mathcal{L}_2 > \mathcal{R}_2</katex> 表示這裡面仍然有異常的球。又因為 <katex>A_4, B_4</katex> 交換位置不影響 **左大於右**，表示 <katex>\{ A_1, A_2, A_3 \}</katex> 有異常球且比較重。接著利用上面的 **已知事實**，我們秤第三次就能找到答案。

*Case 2.3：* <katex>\mathcal{L}_2 < \mathcal{R}_2</katex> 表示這裡面仍然有異常的球。又因為 <katex>A_4, B_4</katex> 交換位置影響 **左大於右**，表示這兩個有一個是異常球且 <katex>A_4 > B_4</katex>。所以拿 <katex>\mathcal{L}_3 = \{C_4\}</katex> 與 <katex>\mathcal{R}_3 = \{A_4\}</katex> 比，如果一樣則 <katex>B_4</katex> 異常為輕，反之則是<katex>A_4</katex> 異常為重了。

**Case 3：** <katex>\mathcal{L}_1 < \mathcal{R}_1</katex>

思路同上就不贅述了。