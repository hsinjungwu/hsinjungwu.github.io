---
title: "The Complete Python Pro Bootcamp for 2021"
date: 2021-03-28T10:20:00+08:00
draft: false
dropCap: false
categories:
  - "為自己學習"
tags:
  - "100DaysOfCode"
  - "Python"
---

在 [Udemy](https://www.udemy.com/) 買了 [100 Days of Code - The Complete Python Pro Bootcamp for 2021](https://www.udemy.com/course/100-days-of-code/) 讓自己認真學 `Python`，畢竟花了錢不學習，心會比較疼。 🤭

<!--more-->

這篇文章會持續紀錄學習歷程中覺得有意思的內容。而完整練習的程式碼放在 [這裡](https://github.com/hsinjungwu/self-learning/tree/main/100_Days_of_Code-The_Complete_Python_Pro_Bootcamp_for_2021)

## Day 6

今天的課程重點應該是 **邏輯** 😆

老師使用 [Reeborg's World](https://reeborg.ca/index_en.html) 搭配機器人的基本指令讓學生能夠玩中學。課程中有兩個任務

1. 跳欄：
   - [Hurdle 1](https://reeborg.ca/reeborg.html?lang=en&mode=python&menu=worlds%2Fmenus%2Freeborg_intro_en.json&name=Hurdle%201&url=worlds%2Ftutorial_en%2Fhurdle1.json)
   - [Hurdle 2](https://reeborg.ca/reeborg.html?lang=en&mode=python&menu=worlds%2Fmenus%2Freeborg_intro_en.json&name=Hurdle%202&url=worlds%2Ftutorial_en%2Fhurdle2.json)
   - [Hurdle 3](https://reeborg.ca/reeborg.html?lang=en&mode=python&menu=worlds%2Fmenus%2Freeborg_intro_en.json&name=Hurdle%203&url=worlds%2Ftutorial_en%2Fhurdle3.json)
   - [Hurdle 4](https://reeborg.ca/reeborg.html?lang=en&mode=python&menu=worlds%2Fmenus%2Freeborg_intro_en.json&name=Hurdle%204&url=worlds%2Ftutorial_en%2Fhurdle4.json)
2. 走迷宮：[Maze](https://reeborg.ca/reeborg.html?lang=en&mode=python&menu=worlds%2Fmenus%2Freeborg_intro_en.json&name=Maze&url=worlds%2Ftutorial_en%2Fmaze1.json)

其中走迷宮算有點難度，原本要套用 Hurdle 4 的解法，但在老師給的 Test Case 會造成無窮迴圈。所以有稍微花了一點時間調整。解完後有獲得成就感～ 🤭

## Day 16

因為沒裝 [pycharm](https://www.jetbrains.com/pycharm/)，打算用 [vscode](https://code.visualstudio.com/) 打遍天下，因此遇到下面的問題

- 引用 [Turtle](https://docs.python.org/3/library/turtle.html) 時畫範例時會跳錯誤 `ModuleNotFoundError: No module named 'tkinter'`。
  - 使用 `sudo apt-get install python3-tk` 即可解決。
- 無法引用 [prettytable](https://pypi.org/project/prettytable/)
  1. 先用 `sudo apt-get install python3-pip`
  2. 接著 `pip3 install prettytable`
  3. 重開 [vscode](https://code.visualstudio.com/)

## Day 17

在排版 [OpenTriviaDatabase](https://opentdb.com/) API 給的檔案，發現 Python 有 3 種 formatting provider : autopep8, black 跟 yapf。最後參考這篇 [python 代码格式化工具只懂 autopep8？这里有更好的](https://zhuanlan.zhihu.com/p/203307235) 選擇使用 black。然後也順手安裝了 [tabnine](https://www.tabnine.com/) 😎

## Day 19

在執行 `screen.onkey` 時一直沒有反應，後來才知道要加 `sudo`

> sudo python3 day19/start.py

另外 <kbd>enter</kbd> 跟 <kbd>esc</kbd> 是使用 `Return` 與 `Escape`
