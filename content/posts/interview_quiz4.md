---
title: "面試題目四"
date: 2020-09-14T10:20:00+08:00
draft: false
dropCap: false
tags:
  - "Interview"
---

前同事今天面試的題目，我稍微改了題目敘述。😁

> 給定 5 張撲克牌，判斷它是否是順子。如果不是，顯示出有幾個不同的數字, 最長的長度為何，有著這個長度的數字是哪些？

我前同事是用 `map` + `sort` 去處理。但我選擇了另一個路子來解這題。當然，一些細節(如果它是用一副撲克牌發的話、長度可以開到 14 不用 15)我就先跳過。總之程式碼如下：

```go
package main

import (
	"fmt"
	"strconv"
)

func main() {
	names := make([]string, 15)
	for i := 2; i < 11; i++ {
		names[i] = strconv.Itoa(i)
	}
	names[1] = "A"
	names[14] = "A"
	names[11] = "J"
	names[12] = "Q"
	names[13] = "K"

	data := []int{1, 12, 12, 12, 11}
	s, c, m, ids := getRank(data)
	if s > 0 {
		fmt.Printf("順子：%s,%s,%s,%s,%s\n", names[s], names[s-1], names[s-2], names[s-3], names[s-4])
	} else {
		fmt.Printf("有 %d 個不同的數字, 最長的長度為 %d，有著這個長度的數字是 %v\n", c, m, ids)
	}
}

func getRank(data []int) (int, int, int, []int) {
	m := make([]int, 15)
	for _, d := range data {
		m[d]++
		if d == 1 {
			m[14]++
		}
	}

	for i := 14; i >= 5; i-- {
		t := 1
		for j := 0; j < 5; j++ {
			t *= m[i-j]
		}
		if t == 1 {
			return i, 0, 0, nil
		}
	}

	cnt := 0
	max := 0
	var maxID []int
	for i := 13; i >= 1; i-- {
		if m[i] > 0 {
			cnt++
			if m[i] > max {
				max = m[i]
				maxID = []int{i}
			} else if m[i] == max {
				maxID = append(maxID, i)
			}
		}
	}
	return 0, cnt, max, maxID
}
```
