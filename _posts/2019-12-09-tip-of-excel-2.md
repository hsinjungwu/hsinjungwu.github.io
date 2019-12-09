---
layout: post
title:  "Excel 的 If {0,1} 奇技"
date:   2019-12-09 14:51:54
tags:  
  - Excel

---

有時候在拉表格的時候，因為某些原因會需要從右往左執行 `VLOOKUP`。然後看到這篇 [How To Vlookup Values From Right To Left In Excel?](https://www.extendoffice.com/documents/excel/2453-excel-vlookup-right-to-left.html) 神奇的方法。

簡單對它的重點公式翻譯一下

> =VLOOKUP(F2,IF({1,0},$D$2:$D$9,$B$2:$B$9),2,0)

它其實是把 EXCEL 中的 [B, C, D] 透過 `IF(1, $D$2:$D$9,$B$2:$B$9)` 跟 `IF(0, $D$2:$D$9,$B$2:$B$9)` 合併獲得一個陣列 [D, B]，然後再用 `VLOOKUP` 查找。

不過在這篇 [IF({1,0}...结构（图解）](https://zhuanlan.zhihu.com/p/34845553) 提到

> 不过因为数组公式影响运算速度，所以现实中的反向查找更建议使用Index套Match结构

再加上這公式太奇葩了，所以還是用 `Index` + `Match` 解決吧！

> =INDEX($B$2:$B$9,MATCH(F2,$D$2:$D$9,0))