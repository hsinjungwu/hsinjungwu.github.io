---
title: "Getting .Net Framework version of a DLL using Powershell"
date: 2023-01-03T23:25:00+08:00
draft: false
dropCap: false
tags:
  - "HowTo"
---

工作需求要辨識別部門送來的 dll 使用的 `.Net FrameWork` 是哪一種版本。參考了這篇 [Getting .Net Framework version of a DLL using Powershell](https://social.technet.microsoft.com/Forums/en-US/567fbeb3-d868-41b3-af5e-bea1e4036600/getting-net-framework-version-of-a-dll-using-powershell?forum=winserverpowershell) 裡面提的 :

```ps1
$dllfile = 'SevenZipSharp.dll'
$sb = {$_.AttributeType.Name -eq 'TargetFrameworkAttribute'}
[Reflection.Assembly]::ReflectionOnlyLoadFrom($dllfile).CustomAttributes.Where($sb).ConstructorArguments.Value
```

另外蠻多文章都跟這篇 [Get .NET Framework Version of a DLL](https://www.c-sharpcorner.com/blogs/get-net-framework-version-of-a-dll1) 的解法一樣 :

```ps1
[Reflection.Assembly]::ReflectionOnlyLoadFrom("C:\SomeTest.dll").ImageRuntimeVersion 
```

但這個回傳的是 `CLR` 的版本[^1]。😵

[^1]: [釐清 CLR、.NET、C#、Visual Studio、ASP.NET 各版本之間的關係](https://blog.miniasp.com/post/2015/07/28/Clarify-the-versions-between-CLR-NET-CSharp-Visual-Studio-and-ASPNET)