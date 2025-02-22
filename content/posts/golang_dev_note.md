---
title: "golang 開發備忘"
date: 2023-11-17T10:20:00+08:00
draft: false
dropCap: false
tags:
  - "HowTo"
---

最近在新團隊開始使用 golang，備份一下可能會踩的雷。

## 環境建置前

1. `GO111MODULE` 設定成 `ON`
2. 將公司 git server 設定到 `GOPRIVATE`。

其中這篇 [私有化仓库的 GO 模块使用实践](https://juejin.cn/post/6977261480425029662) 有整理以下變數說明：

> + GONOPROXY，基于前缀的匹配方式运行，上图中指定了gitlab.com，也就是所有 gitlab.com 上的代码，不从 GOPROXY 服务器上去获取，全部通过传统 VCS 方式，直接去原代码服务器上拉取；
> + GONOSUMDB，可以让前缀匹配上的模块跳过安全性检查；
> + GOPRIVATE，相当于前面两个环境变量的集合，配置了 GOPRIVATE 就相当于把前面的两个环境变量一起配置了；

{{< tabgroup align="right" >}}
{{< tab name="Windows" >}}
設定系統變數
+ `GO111MODULE` = *on*
+ `GOPRIVATE` = *git server host*
{{< /tab >}}
{{< tab name="MacOS" >}}
1. vim ~/.zshrc
2. 加上下面兩行
	+ `export GO111MODULE=on`
	+ `export GOPRIVATE={git server host}`
3. source ~/.zshrc 
{{< /tab >}}
{{< /tabgroup >}}

## 設定 Go Mod

1. go mod init "your project"
2. go mod tidy
3. 第一次加入 plugin `go get "your plugin"`
4. 更新 plugin `go get -u "your plugin"`

## 語法與指令

1. [How can I "go run" a project with multiple files in the main package?](https://stackoverflow.com/questions/28081486/how-can-i-go-run-a-project-with-multiple-files-in-the-main-package) : `go run .`
2. 使用 `json:"omitempty"` 會跳出 *struct field xxx repeats json tag "omitempty" also at...* 應該是把它認成 *name* 所以才會重複，改成 `json:",omitempty"` 就可以
3. go get xxx 遇到 `panic: internal error: net token acquired but not released` 時請更新 go 版本。我從 *1.21.0* 升到 *1.21.5* 就解決了