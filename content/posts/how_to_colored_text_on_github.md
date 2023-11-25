---
title: "如何在 github 幫文字上色"
date: 2023-11-25T10:20:00+08:00
draft: false
dropCap: false
tags:
  - "HowTo"
---

最近想把 HACKMD 的文件搬到 github private repo，有些暫定的想法想放在 issue，但它不支援

+ `<code style="color: red;">Hello</code>`
+ `<font color="blue">World</font>`

後來看到這篇 [Colored text to markdown](https://github.com/orgs/community/discussions/31570#discussioncomment-3571340) 提出了解法

> Find a way to colorfy text in Github in the best way now (Since May 2022)!
>
> If i use the `\color{nameColor}` code from LATEX inside `$$$$`, now that github can support

沒想到居然是用 $\LaTeX$ 解決 👍
