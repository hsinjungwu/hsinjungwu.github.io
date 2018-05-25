---
layout: post
title:  "讓我誤解的屬性設定(2)"
date:   2018-05-25 12:51:54
categories: "Syntax"
tags:  
  - "C#"

---

一樣雷。 :bomb:

<!-- more -->

早上同事的程式被測試部門退回來，但同事跑他的測試是沒有問題。猛一看同事的程式與測試也很合理，但沒辦法拿到測試部門的程式，只好自己來找碴，結果又是同樣的問題。 :sweat_smile:

同事的程式如下，基本上是要讓 `PB` 的 `X` 小於 2。

``` c#
public class A
{
    private B pb = new B();

    public B PB
    {
        set
        {
            if (value.X < 2)
            {
                pb = value;
            }
        }
    }

    public void Show()
    {
        Console.WriteLine($"X = {pb.X}");
    }
}

public class B
{
    public int X;
}
```

他寫的測試如下，讓 `X = 30`，接著測出來的結果是對的，然後就交了。

``` c#
private static void Test()
{
    A a = new A();
    B b = new B();
    b.X = 30;
    a.PB = b;
    a.Show();
    Console.ReadLine();
    //SHOW : X = 0
}
```

而我寫的測試如下：

``` c#
private static void MyTest()
{
    A a = new A();
    B b = new B();
    for (int i = 0; i < 5; i++)
    {
        b.X = i;
        a.PB = b;
        a.Show();
    }    
    Console.ReadLine();
    /* SHOW :
     ************
     * X = 0
     * X = 1
     * X = 2
     * X = 3
     * X = 4
     ************
     */
}
```

跑完看到 `X` 的值奔放了 :laughing: 原因其實很簡單：

1. `b` 的 `X` 小於 2，所以 `b` 順利塞(?)進 `a.PB`，這時 `pb` 跟 `b` 就是同一個東西(可用 `b.Equals(a.PB)` 確認)。
2. 跑到 `i = 3` 執行 `b.X = 2` 時 `pb.X` 也變成 2。
3. 接著執行 `a.PB = b` 時，因為 `b` 的 `X` 等於 2 所以塞(?)不進 `a.PB`。

因此雖然在第 3 步塞不進 `a.PB`，但 `pb.X` 已經在第 2 步就變了，所以呼叫 `Show()` 時還是顯示 **我們認為是錯誤** 的結果。而用同樣的道理去思考迴圈逆序(由4到0)，則顯示結果會是 **我們期望看到** 的值。