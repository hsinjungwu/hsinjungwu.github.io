---
layout: post
title:  "如何批次處理 git pull"
date:   2019-01-03 11:51:54
tags:  
  - Git
---

* content
{:toc}

專案一多就會有各種需求啊！

<!-- more -->

## 作法

首先假設你的專案資料夾叫 **Projects** 且結構如下：

![project folder structure](/files/projectFolderStructure.png)

接著複製以下語法[^1]另存為 **batchpull.bat**，並放置於資料夾 **Projects**。

{% gist 1e4f81cb29a90d4f5abb806176c250a2 %}

然後執行 **batchpull.bat**。如果有跳出下面這張圖的內容，就乖乖按 `yes` 三個字就可以了。

![batch pull](/files/batchPull.png)

## 可能會遇到的問題

+ 'Git' 不是內部或外部命令、可執行的程式或批次檔。 

請參考這篇[“git 不是内部或外部命令，也不是可运行的程序 ”解决方案](https://blog.csdn.net/c20081052/article/details/78418858)即可。

另外如果是安裝 [GitKraken](https://www.gitkraken.com/) 的話根據它的 [FAQ](https://support.gitkraken.com/faq/)，你也需要安裝 [Git](https://git-scm.com/)

> Unlike other Git GUI clients, GitKraken is not a front-end GUI for your command line. It works directly with your repositories with no dependencies, which means a separate Git installation isn’t required.

+ 輸入了密碼還是無法登入

如果 remote url 是用 SSH(內容長的像 `git@gitHost:group/repo.git`)，檢查你的 `~/.ssh`(Windows 的位置是 `C:\Users\[yourname]\.ssh` ) 有沒有 *id_rsa*，如果沒有的話，記得補上。

----

[^1]: 參考自 [Windows下git pull批处理](http://www.jheng.top/post/47539.html)