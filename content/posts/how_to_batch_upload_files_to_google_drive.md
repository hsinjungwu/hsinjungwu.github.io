---
title: "How To Batch Upload Files To Google Drive"
date: 2021-03-10T20:25:00+08:00
draft: false
dropCap: false
categories:
    - "HowTo"
---

協助公司同仁處理日常工作。🤓

<!--more-->

## 建置
1. Fork from [原版 gdrive](https://github.com/prasmussen/gdrive)
2. 參考 [如何在終端機介面使用 Google Drive (gdrive cmd)](https://hiraku.tw/2020/01/5894/) 裡的說明修改 **ClientId** 跟 **ClientSecret**。
3. 執行 `CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build` 產生執行檔 *gdrive.exe*
    + 要執行 `go mod init`
    + *go.mod* 裡面的 `golang.org/x/oauth2` 版號要調整

## 安裝
1. 將 `gdrive.exe` 放到 `C:\Windows`
2. 參考 [Google Drive in Command Line](https://sunxiaoshan.medium.com/google-driver-in-command-line-426c8d4031fb) 的圖解教學即可。

## 使用
可透過以下語法執行批次操作，其他使用 `gdrive help` 查詢。

``` bat
SET fileName=上傳檔案
gdrive upload -p 指定資料夾的ID %fileName%

REM -r 表示遞迴
SET folderName=上傳資料夾
gdrive upload -r -p 指定資料夾的ID %folderName%
```

### 需要多帳號
我採用暴力法 😎
1. 修改 `handlers_drive.go`
    ``` diff
    - const TokenFilename = "token_v2.json"
    + const TokenFilename = "token_xx.json"
    ```
2. 重新建置並命名為 `gdrive_xx.exe` 放到 `C:\Windows`
3. 語法變為 `gdrive_xx help`

## 發生錯誤
+ 檔名路徑有空格：可以使用雙引號 <kbd>"</kbd> 把檔名路徑夾起來。
+ **invalid_grant**：到 `C:\Users\UserName\AppData\Roaming\.gdrive` 刪掉對應的 `token_xx.json`，然後重新輸入 `gdrive list` 再次驗證即可。或是使用下列語法。
```bat
@echo off
REM token 檔名
SET TOKEN="token_v2"
REM 使用者名稱
SET USERNAME="User"
SET CONFIG="C:\Users\%USERNAME%\AppData\Roaming\.gdrive\%TOKEN%.json"
IF EXIST %CONFIG% DEL /F %CONFIG%
gdrive list
PAUSE
```
