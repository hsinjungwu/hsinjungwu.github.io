---
layout: post
title:  "如何批次建置 DLL"
date:   2018-08-06 12:51:54
categories: "HowTo"
tags:  
  - MSBuild
  - Batch
---

因為工作需要，寫了個批次執行檔。

<!-- more -->

檔案內容如下

{% gist 80f69e9ff8e7bed94b3616ae7d9f9f05 %}

主要是參考強者我前同事 @kirbyninja 寫的 [sw-build-packer](https://github.com/kirbyninja/sw-build-packer)裡這段

``` cs
startInfo.FileName = string.Format(@"{0}\MSBuild\12.0\Bin\MSBuild.exe", Environment.GetFolderPath(Environment.SpecialFolder.ProgramFilesX86));
startInfo.Arguments = string.Format("{0} /nologo /t:Rebuild /p:Configuration=Debug /v:q /clp:ErrorsOnly",solutionFileName);
```

其中 Visual Studio 2015 的路徑是 `C:\Program Files (x86)\MSBuild\14.0\Bin\MSBuild.exe` 而 2017 版則是放在 `C:\Program Files (x86)\Microsoft Visual Studio\2017\{你的版本類型}\MSBuild\15.0\Bin`。另外可以參考這篇 [MSBuild Command-Line Reference](https://msdn.microsoft.com/zh-tw/library/ms164311.aspx) 來調整參數。

最後 batch 的迴圈執行沒有想像中的容易，我參考了這篇 [How to Use Array in Windows Batch Programming?](https://helloacm.com/how-to-use-array-in-windows-batch-programming/) 來調整。