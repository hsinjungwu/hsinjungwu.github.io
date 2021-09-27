---
title: "用 Line 來通知上下班打卡紀錄"
date: 2021-09-27T10:20:00+08:00
draft: false
dropCap: false
categories:
  - "Line"
  - "GoogleAppsScript"
---

前幾天忘了自己下班有沒有打卡，除了回去補打之外不然就是要經過種種驗證登入公司信箱查詢。套句強者我學長說的 **幹壞事是進步最大的原動力**，於是開始了這段簡單旅程。

<!--more-->

原本想用 [ifttt](https://ifttt.com/home) 來處理

1. 收到信自動轉寄給 ifttt
2. ifttt 送給 Line Notify

但 gmail 應該是避免亂發郵件，所以自動轉寄的收信信箱要認證。但我又沒辦法跟 ifttt 拿認證碼，所以這條路就不行。

後來想到曾看過這篇 [LINE Notify：用 Google Apps Script 建立簡易網站監測機器人](https://www.letswrite.tw/line-notify-gas/)，於是就照抄他送通知的 code 其他則是看[官方文件](https://developers.google.com/apps-script/reference/gmail) 的內容拼湊。

至於遇到的問題大概就是在 `GmailApp.search` 的條件不知道有哪些關鍵字，但生命會自己找到出路。總之程式碼如下

```js
function run() {
  var msg = queryMail();
  if (msg.length > 0) {
    lineMessage(msg);
  }
}

var token = "xxx"; //your token

function lineMessage(msg) {
  var option = {
    method: "post",
    headers: { Authorization: "Bearer " + token },
    payload: {
      message: msg,
    },
  };
  UrlFetchApp.fetch("https://notify-api.line.me/api/notify", option);
}

function queryMail() {
  var rtnMsg = "";

  var condition = 'subject:"刷卡通知" is:unread';
  var threads = GmailApp.search(condition);
  var messages = GmailApp.getMessagesForThreads(threads);
  for (var i = 0; i < messages.length; i++) {
    for (var j = 0; j < messages[i].length; j++) {
      var mail = messages[i][j];
      rtnMsg +=
        "\n" +
        Utilities.formatDate(mail.getDate(), "GMT+8", "yyyy/MM/dd") +
        " " +
        mail.getPlainBody();
      mail.markRead(); //標為已讀
    }
  }
  for (var i = 0; i < messages.length; i++) {
    threads[i].moveToArchive(); //封存
  }

  return rtnMsg;
}
```
