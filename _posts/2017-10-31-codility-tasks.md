---
layout: post
title:  "Codility 面試 3 題"
date:   2017-10-31 12:51:54
categories: Interview
tags:
  - Codility
  - algorithm
  - LeetCode
  - ProjectEuler
---

* content
{:toc}

面試信上寫 **Before 2017-10-30** 結果我發現時已經是 **2017-10-31 凌晨** 了... :sweat:

<!-- more -->

由於已經遲繳了，因此看到 [Codility][C] 題目只要求 **正確性** 後我對時間 / 空間複雜度也就不太在意了。

總共是 3 題兩小時，下面列出我理解後的內容與解答，但程式碼可能跟我交付的有差。 :weary:

## 第一題

> 給定一字串 S (只有數字與英文字母)，找出最長子字串滿足內容沒有數字且至少有一大寫字母。如果存在回傳該子字串長度，否則回傳 -1

看著倒數計時的數字，我還是有點緊張。所以我直接暴力這題

``` cs
int Solution(string S)
{  
  if (string.IsNullOrWhiteSpace(S)) return -1;

  var longestSub = S.Split(new char{'0', '1', '2', '3', '4', '5', '6', '7', '8', '9'})
                    .Where(s => s.Any(c => char.IsUpper(c)))
                    .OrderByDescending(s => s.Length)
                    .FirstOrDefault();
  return longestSub == null ? -1 : longestSub.Length;              
}
```

等醒來後才想到也可以不用 `Linq` 這樣寫

``` cs
int Solution(string S)
{  
  int ans = -1;
  int sum = 0;
  bool hasUpper = false;
  foreach (char c in S)
  {
    if (Char.IsDigit(c))
    {
        if (hasUpper) ans = Math.Max(ans, sum);
        sum = 0;
        hasUpper = false;
        continue;
    }
    hasUpper |= Char.IsUpper(c);
    sum++;
  }
  if (hasUpper) ans = Math.Max(ans, sum);
  return ans;              
}
```

## 第二題

> 給定 `POP`, `DUP`, `+`, `-` 跟 `數字` 組成的字串算出結果。請依下表計算答案，若答案為負或是無法計算請回傳 `-1`。

| 指令 | 意思 | 
|-----|------|
| POP | POP |
| DUP | DUPLICATE |
|  +  | ADD |
|  -  | Subtract |
| 數字 | PUSH |


> 例如給 `4 5 DUP 2 + 8 - POP` 答案為 `5`。

| 指令 |結果 |
|-----|-----|
|  4  | 4 |
|  5  | 4, 5 |
| DUP | 4, 5, 5 |
|  2  | 4, 5, 5, 2 |
|  +  | 4, 5, 7 | 
|  8  | 4, 5, 7, 8 |
|  -  | 4, 5, 1 |
| POP | 4, 5 |

這題基本上用 `Stack` 加暴力法就解決了。雖然題目很長，但卻很簡單。

``` cs
int Solution(string S)
{
  string[] ops = S.Split(' ');
  object[] o = new object[ops.Length];
  for (int i = 0; i< ops.Length; i++)
  {
    int v;
    if (int.TryParse(ops[i], out v)) o[i] = v;
    else o[i] = ops[i];
  }

  Stack<int> stack = new Stack<int>();
  try
  {
    foreach (object op in o)
    {
      if (op is int) stack.Push((int)op);
      else
      {
        if (op.ToString() == "POP") stack.Pop();
        else if (op.ToString() == "DUP") stack.Push(stack.Peek());
        else if (op.ToString() == "+") stack.Push(stack.Pop() + stack.Pop());
        else if (op.ToString() == "-") stack.Push(stack.Pop() - stack.Pop());
        else return -1;
      }
    }
    int ans = stack.Pop();
    return ans < 0 ? -1 : ans;
  }
  catch
  {
    return -1;
  }
}
```

## 第三題

> 給定一非負整數，試將其位數重排，回傳有效相異整數個數。例：123 回傳 6, 223 回傳 3, 120 回傳 4, 100 回傳 1

這題基本上就是數學題。但我稍微卡了一下，一直打結在 [錯排問題(Derangement)](https://en.wikipedia.org/wiki/Derangement) 上，浪費了一些時間。另外由於題目數字範圍，我一度想把階乘的函數直接寫死。 :smirk:

``` cs
int Solution(int N)
{
  int[] counts = new int[10];

  while (N > 0)
  {
    counts[N % 10]++;
    N /= 10;
  }
  int product = 1;
  for (int i = 1; i<10; i++) product *= GetFactorial(counts[i]);

  int digitCount = counts.Sum();
  
  int ans = GetFactorial(digitCount) / (GetFactorial(counts[0]) * product);
  if (counts[0] > 0) ans -= GetFactorial(digitCount-1) / (GetFactorial(counts[0]-1) * product);

  return ans;
}

int GetFactorial(int n)
{
  if (n == 0) return 1;
  else return n * GetFactorial(n-1);
}
```

## 結論

沒看到三題的分數，不知道是不是因為逾期所以拿到缺考。另外不知道是不是祖先保佑，我覺得 [Codility][C] 給的這三題比 [LeetCode][LC] 跟 [Project Euler][PE] 都簡單很多。 :grimacing:

[C]: https://codility.com
[PE]: https://projecteuler.net/
[LC]: https://leetcode.com/