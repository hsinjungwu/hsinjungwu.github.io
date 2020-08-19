---
title: "面試題目一"
date: 2020-08-19T10:20:00+08:00
draft: false
dropCap: false
categories:
    - "Interview"
---

前同事的同事去某間公司被問的題目

<!--more-->

## 題目

給定正整數 $n$，找出位數總和與它相同，而且大於它的最小正整數。例如

+ 772 => 781
+ 293 => 329
+ 100 => 10000

## 解法

### 初始作法

+ 對於末兩位數字小於 90，且非 10 的倍數的數字，`+9` 就結束。
+ 剩下的數字，我是先推出至少要加幾個 9，搭配 `+9` 迴圈檢查 **digit sum** 是否相同。

### 改善解法

做出來之後，我測試了一下剩餘的例子，發現有規律性，所以改成以下寫法。但沒有也沒空證明是對的 😆

``` go
package main

import (
	"fmt"
	"time"
)

func main() {
	t := time.Now()
	data := 998
	ans := getAns(data)
	elapsed := time.Since(t)
	fmt.Printf("Elapsed time: %v, data = %d, ans = %d", elapsed, data, ans)
}

func getAns(data int) int {
	r := data % 100
	q := data / 100

	step := 0
	if r == 0 {
		b0 := 100
		for q%10 == 0 {
			b0 *= 10
			q /= 10
		}
		s0 := q % 10
		step = (b0-1)*(10-s0)/9 + 1
		q /= 10
		for q%10 == 9 {
			step += s0
			s0 *= 10
			q /= 10
		}
	} else if r > 90 {
		b9X := 10
		s9X := r % 10
		for q%10 == 9 {
			b9X *= 10
			q /= 10
		}
		step = (b9X-1)*s9X/9 + 1
	} else if r%10 == 0 {
		sX0 := r / 10
		step = 11 - sX0

		for q%10 == 9 {
			step += sX0
			sX0 *= 10
			q /= 10
		}
	} else {
		step = 1
	}

	return data + step*9
}
```

## 結論

不知道我前同事的同事是在什麼情況下被問。如果是白板題，我差不多就用初始解法打發，因為我數學不好也缺乏敏銳度。如果是考線上我才會用觀察法重新改寫。