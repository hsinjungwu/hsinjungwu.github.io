---
title: "又重啟"
date: 2020-08-20T02:13:00+08:00
draft: false
dropCap: false
categories:
  - "Site"
---

既然結婚了，重啟 blog 也是理所當然的事吧！ 💏

<!--more-->

## 換系統

原本計畫採用 [Jekyll](https://jekyllrb.com/) 的 [collection](https://jekyllrb.com/docs/step-by-step/09-collections/) 收集 [Project Euler](http://projecteuler.net/) 的解答，程式也改好了(基本上就模仿原本 theme 的 layout、page)。但還是覺得彆扭，於是就逛了一下 [Hugo theme](https://themes.gohugo.io/)，結果發現 90% 以上[^1]都有支援 [katex](https://katex.org/)。於是我二話不說直接選擇 [Hugo](https://gohugo.io/) 並試著在 [gitlab](https://about.gitlab.com/) 上安裝。

基本上 [如何安裝 Hugo](https://gohugo.io/getting-started/installing/) 跟 [如何發佈在 gitlab](https://gohugo.io/hosting-and-deployment/hosting-on-gitlab/)，在官網都寫得很清楚，我就不贅述。而如何發佈在 github 上，我建議參考 [使用 Github Actions 來自動化部署 Hugo 到 Github Pages](https://blog.puckwang.com/post/2020/use-github-actions-deploy-hugo/) 這篇就可以。

## 分類分群

想了很久，決定將跟工作有關的文章移到 [這裡](https://hsinjungwu.gitlab.io)，這裡還是放自己平常的文章。另外透過不同的資料夾我將一般的文章放在 `posts` 並只用 `categories` 分類，而 Project Euler 的文章則放在 `pe` 並透過 `tag` 分群。

[^1]: 我不知道是不是內建 100%
