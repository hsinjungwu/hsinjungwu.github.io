---
title: "Build Your Own Custom Short URL"
date: 2023-01-18T10:25:00+08:00
draft: false
dropCap: false
tags:
  - "HowTo"
  - "Line"
  - "Google Apps Script"
  - "Github Issue"
---

最近在幫老婆做小工具時突然的靈感，可以透過 *Line Bot* + *Google Apps Script* + *Github Issue* 完成屬於自己的短網址服務。

## 實作

### 設定 Line Bot 讀訊息

參考 [實作 LINE 聊天機器人 ( Google Apps Script )](https://www.oxxostudio.tw/articles/201804/line-bot-apps-script.html) 或 [兩小時打造簡單 Line Chatbot — 使用 Google Apps Script & Google Sheet API](https://medium.com/%E6%8A%80%E8%A1%93%E7%AD%86%E8%A8%98/%E5%85%A9%E5%B0%8F%E6%99%82%E6%89%93%E9%80%A0%E7%B0%A1%E5%96%AE-line-chatbot-%E4%BD%BF%E7%94%A8-google-apps-script-google-sheet-api-8fff7372ff3d) 就可以。

{{< notice warning >}}
記得在 `回應功能` 中關掉 `聊天` 跟 `自動回應`，不然你的機器人不會自動已讀。
{{< /notice >}}

### 產生短網址

想法來自於用 Github Issue 寫 Blog，可以 fork [這份專案](https://github.com/casualjavascript/blog)，再參考 [這篇](https://stackoverflow.com/questions/5411538/redirect-from-an-html-page) 在 *index.html* 加入下面這段即可。

```html
<meta http-equiv="refresh" content="0; url=http://example.com/" />
```

然後再於 Google Apps Script 內透過 [API 產生 Issue](https://docs.github.com/en/rest/issues/issues?apiVersion=2022-11-28#create-an-issue) 獲得短網址並讓 Line Bot 回傳。

```js
function getShortUrl(r) {
  let url = 'https://api.github.com/repos/{OWNER}/{REPO}/issues';

  let data = {
    "title": r.title,
    "body": r.link,
  }

  let token = PropertiesService.getScriptProperties().getProperty('<YOUR-TOKEN-KEY>');

  let requestOptions = {
    method: 'post',
    headers: {
      'Accept': 'application/vnd.github+json',
      'Authorization': 'Bearer ' + token,
    },
    payload: JSON.stringify(data),
    muteHttpExceptions: true,
    followRedirects: true
  };
  let n = JSON.parse(UrlFetchApp.fetch(url, requestOptions)).number;
  return 'https://{OWNER}.github.io/{REPO}/?' + n;
}
```

{{< notice tip >}}
1. 在執行 `POST` issue 遇到問題，參考了 [How to post via API from google scripts](https://community.airtable.com/t5/other-questions/how-to-post-via-api-from-google-scripts/td-p/136323)，加入 `muteHttpExceptions: true,`。
2. 參考 [How to define global variable in Google Apps Script](https://stackoverflow.com/questions/24721226/how-to-define-global-variable-in-google-apps-script) 的作法，其中設定位置在 `齒輪 => 指令碼屬性`。
{{< /notice >}}

## 後記

1. 沒使用 GCP(Google Cloud Platform) debug，而是用土炮法建立一個 debug 用的 google sheet，然後訊息寫進去。
   ```js
   function debug(cell, value) {
      let ss = SpreadsheetApp.openById("<sheet id>");
      let rs = ss.getSheetByName("<sheet name>");  
      rs.getRange(cell).setValue(value);
   }
   ```
2. 這篇 [Google App Script到底是什麼？](https://medium.com/@dustfantasy/google-app-script-%E5%88%B0%E5%BA%95%E6%98%AF%E4%BB%80%E9%BA%BC-6a37a06a85a8) 提供了新手會踩的雷。 😝
   + `doGet`,`doPost` 背就對了！
   + Latest Version (Head) 的 API 是測試部屬作業，但 Messaging API 的 Webhook 套用它測試會失敗。
3. 其實 Line Bot 只要能完成 **回傳你打的字**，剩下的就是創造力！🥂