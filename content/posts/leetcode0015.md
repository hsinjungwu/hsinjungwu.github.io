---
title: "LeetCode 0015－3Sum"
date: 2020-09-24T23:20:00+08:00
draft: false
dropCap: false
categories:
    - "LeetCode"

---

題目如下：

> Given an array `nums` of n integers, are there elements *a, b, c* in nums such that *a + b + c = 0*? Find all unique triplets in the array which gives the sum of zero.
>
> Notice that the solution set must not contain duplicate triplets.

<!--more-->

只求 pass 的解答。

```go
func threeSum(nums []int) [][]int {
   var ans [][]int
	if len(nums) < 3 {
		return ans
	}

	var nbs []int
	var nb2s []int
	cnt0 := 0
	table := make(map[int]int)
	for _, n := range nums {
		if n == 0 {
			cnt0++
		}

		_, has := table[n]
		if has {
			table[n]++
			if table[n] == 2 {
				nb2s = append(nb2s, n)
			}
		} else {
			table[n] = 1
			nbs = append(nbs, n)
		}
	}

	if cnt0 > 2 {
		ans = append(ans, []int{0, 0, 0})
	}

	for _, n1 := range nb2s {
        if n1 == 0 {
			continue
		}
		n2 := -2 * n1
		_, ok2 := table[n2]
		if ok2 {
			ans = append(ans, []int{n1, n1, n2})
		}
	}

	sort.Ints(nbs)
	for i1 := 0; i1 < len(nbs)-1; i1++ {
		n1 := nbs[i1]
		if n1 > 0 {
			break
		}
		for i2 := i1 + 1; i2 < len(nbs); i2++ {
			n2 := nbs[i2]
			if n1+n2 > 0 {
				break
			}
			n3 := -n1 - n2
			if n1 >= n3 || n2 >= n3 {
				continue
			}
			_, ok := table[n3]
			if ok {
				ans = append(ans, []int{n1, n2, n3})
			}
		}
	}

	return ans
}
```