---
layout: post
title:  "從 .Net Framework 轉成 .Net Core"
date:   2019-06-27 10:20:04
tags:  
  - DotNet_Core 
---

* content
{:toc}

只是筆記讓其他同事之後要寫 `.Net Core` 的東西時可以快速轉換。

<!-- more -->

## 對 #if 顯示不支援

切換組建組態屬性時，程式碼 `#if DEBUG` 內的文字不像在 `.Net Framework` 時，會即時切換顯示顏色。這部分就看著辦吧 :satisfied:

不過還是建議不要寫 [#if](https://docs.microsoft.com/zh-tw/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) 改用 [ConditionalAttribute](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.conditionalattribute?view=netframework-4.8)。

## 預設沒有 Properties

簡單說在 `.Net Core` 中，這些設定都記在 *YourPoject.csproj* 中。沒寫的在建置時會自動幫你長出 `AssembleInfo.cs` 內的東西。如果想要複製之前 `.Net Framework` 寫好的設定的話，請參考[這篇](https://stackoverflow.com/questions/42138418/equivalent-to-assemblyinfo-in-dotnet-core-csproj/42183749)的步驟做：

1. 在該專案下新增資料夾，並命名為 *Properties*。
2. 在 *Properties* 下新增 *AssemblyInfo.cs*，把你的內容貼上去。
3. 用記事本打開 *YourPoject.csproj* 並在 `<PropertyGroup>` 與 `</PropertyGroup>` 中加上 `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` 即可。

## 沒有 exe

雖然說可以參考這篇[教學](http://dog0416.blogspot.com/2018/06/visual-studio-2017net-core-20-net-core.html)，但我覺得直接寫個 `batch` 檔比較快。

1. 新增 **Run.bat** 於 `dll` 所在資料夾。
2. 在 **Run.bat** 填入 `dotnet (YourProject).dll` 並存檔即可。
3. 之後從點擊 `exe` 改成點擊 `bat`。 :smile: