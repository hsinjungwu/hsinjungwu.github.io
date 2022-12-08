---
title: "關於 EXCEL 內的浮點數儲存內容"
date: 2021-10-06T10:20:00+08:00
draft: false
dropCap: false
tags:
  - "IEEE754"
  - "EXCEL"
---

遇到 [Issue when importing float as string from Excel. Adding precision incorrectly](https://stackoverflow.com/questions/51025969/issue-when-importing-float-as-string-from-excel-adding-precision-incorrectly) 跟 [Excel importation may misinterpret fractional numbers](https://community.claris.com/en/s/question/0D50H00006ezK2L/excel-importation-may-misinterpret-fractional-numbers) 提到的問題，細細研究才發現水很深啊～ 😏

## 問題重現

1. 建立一個 Excel 檔案，並在工作表 1 的 _A1_ 儲存格寫上 **0.0004**
2. 使用 [excelize](https://github.com/qax-os/excelize) 讀取 _A1_ 的值獲得 **4.0000000000000002E-4**
3. 接著使用 [decimal](https://github.com/shopspring/decimal) 解析這個值得到 **0.00040000000000000002**

然後改用 _C#_ 利用 `Microsoft.Office.Interop.Excel` 跟 [ExcelDataReader](https://github.com/ExcelDataReader/ExcelDataReader) 解析出來卻是正確的 **0.0004**。

原以為是 [excelize](https://github.com/qax-os/excelize) 的 bug，於透過解壓縮 _\*.xlsx_ 的方式找到 `\xl\worksheets\sheet1.xml` 發現裡面真的是存 **4.0000000000000002E-4** 😵

## 差異原因

基本上這篇 [從 IEEE 754 標準來看為什麼浮點誤差是無法避免的](https://medium.com/starbugs/see-why-floating-point-error-can-not-be-avoided-from-ieee-754-809720b32175) 已經講得蠻清楚的。另外也可以透過這個 [Double (IEEE754 Double precision 64-bit) Converter](https://www.binaryconvert.com/convert_double.html) 來得到

> **0.0004** Most accurate representation = **4.00000000000000019168694409544E-4**

目前測試的結果看起來 Excel 會依照小數點位數採取不同方式來記錄數字<small>(原因不明)</small>

- 1 位：直接存
- 2 位<small>(不知道為什麼有這兩種差異)</small>：
  + $0.07 = 7.0000000000000007\mathrm{E}{-2}$
  + 其他則直接用浮點換算的 `0.XXXXXXXXXXXXXXXXXX(共18位)` 紀錄。
- 超過 2 位：以科學符號紀錄浮點換算的值，並保留 **17** 個數字，然後第 18 個數字四捨五入。

所以原本的問題

$$
0.0004 \approx 4.00000000000000019168694409544\mathrm{E}{-4} \approx 4.0000000000000002\mathrm{E}{-4}
$$

## 後記

1. 參考 [Read Excel File in C#](https://coderwall.com/p/app3ya/read-excel-file-in-c) 使用 `Microsoft.Office.Interop.Excel` 抓的 [Value2](https://docs.microsoft.com/zh-tw/office/vba/api/excel.range.value2) 型態是 `Double` 所以轉換出的結果就是畫面上看到的那樣。
2. 對於 [Office Open XML](https://zh.wikipedia.org/wiki/Office_Open_XML) 有興趣可以參考這幾篇：
    - [OOXML：Excel(xlsx)是什么](https://insutanto.net/code-notes/2021-05/ooxml/what-is-excel-xlsx)
    - [OOXML：详解 Excel 工作表(worksheet)](https://insutanto.net/code-notes/2021-05/ooxml/what-is-excel-worksheet)
    - [OOXML：详解 Excel 共享字符串(sharedStrings)](https://insutanto.net/code-notes/2021-05/ooxml/what-is-excel-sharedstrings)
3. [安裝 ExcelDataReader](https://www.nuget.org/packages/ExcelDataReader/) 記得也 [安裝 ExcelDataReader.DataSet](https://www.nuget.org/packages/ExcelDataReader.DataSet/) 不然沒法使用範例的 `var result = reader.AsDataSet();`。
4. 找到這篇 [Excel 技巧整理](https://komotonekobox.blogspot.com/search/label/%28A-c%29Excel%E6%8A%80%E5%B7%A7)，雖然現在工作不太接觸 Excel 但還是有備無患。
5. 也找到微軟官方提供的 [Office 產品疑難排解](https://docs.microsoft.com/zh-tw/office/troubleshoot/office-client-welcome)。
