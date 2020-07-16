---
layout: post
title:  "執行 Go Run 跳錯"
date:   2020-07-16 14:22:54
tags:  
  - Golang
  - Kaspersky
  - ProjectEuler
---

莫名雷。 :bomb:

<!-- more -->

最近看到 [Project Euler](https://projecteuler.net/) 很多答案都已經外流 :smirk: 所以想說乾脆也把之前寫的 `C#` 版程式改成 `Golang` 版放出來，也順便練習 `Golang`。

然後寫到第 4 題時 [Kaspersky](https://www.kaspersky.com.tw/) 就跳警告了。

``` go
bound := 1000
ans := 0
for i := 101; i < bound; i++ {
    if i%10 == 0 {
        continue
    }
    for j := i; j < bound; j++ {
        if j%10 == 0 {
            continue
        }
        k := i * j

        // 判斷 k 的值
        if k%11 > 0 {
            continue
        }
    
        //判斷迴文
        isPalindrome := k/100000 == k%10 && k/10000%10 == k%100/10 && k/1000%10 == k%1000/100

        if isPalindrome && ans < k {
            ans = k
        }
    }
}
fmt.Printf("%v", ans)
```

原本在判斷迴文部份，我寫成下面這樣跳錯

``` go
if k/100000 == k%10 && k/10000%10 == k%100/10 && k/1000%10 == k%1000/100 && ans < k
```

然後過沒多久上面的寫法又沒問題，但我改成下面這樣也跳錯...

``` go
if k%10 == 0 {
  continue
}
```

總之錯誤內容大致為以下兩類型：

1. open C:\Users\CFRANK~1\AppData\Local\Temp\go-build312492534\b001\exe\main.exe: Access is denied.
2. fork/exec C:\Users\CFRANK~1\AppData\Local\Temp\go-build954551902\b001\exe\main.exe: Access is denied.

後來用 `go run -x main.go` 看歷程，發現沒問題的跟有問題的只差在 `Temp\go-buildXXXXX` 的 `XXXXX`。所以我猜測是 [Kaspersky] (https://www.kaspersky.com.tw/) 對於 `Temp` 資料夾的亂數有黑名單，造成這種有時可用有時不能用的奇葩情況。