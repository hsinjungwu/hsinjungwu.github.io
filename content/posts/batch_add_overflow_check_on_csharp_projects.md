---
title: "Batch add overflow check on csharp projects"
date: 2022-04-21T10:20:00+08:00
draft: false
dropCap: false
tags:
  - "HowTo"
---

因為需要一口氣調整一批 dll 並重新改版號，所以弄出以下暴力解法。基本上就手動作一次，看改了什麼再毫無美感的暴力硬寫。🙈

## Add Overflow Syntax

```cs
void AddOverflowSyntax(string projFile)
{
  string readText = File.ReadAllText(projFile);
  string syntaxDebugOpen = $"<PropertyGroup Condition=\"'$(Configuration)|$(Platform)'=='Debug|AnyCPU'\">\n";
  string syntaxReleaseOpen = $"<PropertyGroup Condition=\"'$(Configuration)|$(Platform)'=='Release|AnyCPU'\">\n";
  string syntaxData = $"<CheckForOverflowUnderflow>true</CheckForOverflowUnderflow>\n";
  string syntaxClosed = $"</PropertyGroup>\n";
  string search = "</Project>";
  string newText = syntaxDebugOpen + syntaxData + syntaxClosed + syntaxReleaseOpen + syntaxData + syntaxClosed + serach;
  File.WriteAllText(projFile, readText.Replace(search, newText));
}
```

## Update File Version

```cs
void UpdateFileVersion(string versionFile)
{
  string version = "2.0.0.0";
  string readText = File.ReadAllText(versionFile);
  readText = readText.Replace("[assembly: AssemblyVersion(", "//[assembly: AssemblyVersion(").Replace("[assembly: AssemblyFileVersion(", "//[assembly: AssemblyFileVersion(");
  readText += string.Format("\n[assembly: AssemblyVersion(\"{0}\")]\n[assembly: AssemblyFileVersion(\"{0}\")]", version);
  File.WriteAllText(versionFile, readText);
}
```

## Build dll

```cs
void BuildDll(string solutionFileName, string type)
{
  var process = new Process();

  var startInfo = new ProcessStartInfo
  {
    FileName = string.Format(@"{0}\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe", Environment.GetFolderPath(Environment.SpecialFolder.ProgramFilesX86)),
    Arguments = string.Format("{0} /nologo /t:Rebuild /p:Configuration={1} /v:q /clp:ErrorsOnly",
    solutionFileName, type),
    UseShellExecute = false,
    RedirectStandardOutput = true
  };

  process.StartInfo = startInfo;
  process.Start();
  Console.WriteLine("Building the solution {1}-[{0}]...", 
  Path.GetFileNameWithoutExtension(solutionFileName), type);
  process.WaitForExit();
  if (process.ExitCode != 0)
  {
    using (var sr = process.StandardOutput)
    {
      string error = sr.ReadToEnd();
      Console.WriteLine("Build failed with the following eorror message(s):");
      Console.WriteLine(error);
    }
  }
  else
  {
    Console.WriteLine("Build succeeded.");
  }
}
```

## Run

```cs
void Run()
{
  string rootFolder = @"D:\csharp\projs";
  string[] projFiles = Directory.GetFiles(rootFolder, "*.csproj", SearchOption.AllDirectories);
  foreach (var f in projFiles)
  {
    AddOverflowSyntax(f);
  }

  string[] versionFiles = Directory.GetFiles(rootFolder, "AssemblyInfo.cs", SearchOption.AllDirectories);
  foreach (var f in versionFiles)
  {
    UpdateFileVersion(f);
  }

  string[] slnFiles = Directory.GetFiles(rootFolder, "*.sln", SearchOption.AllDirectories);
  foreach (var f in slnFiles)
  {
    BuildDll(f, "Debug");
    BuildDll(f, "Release");
  }
  Console.ReadLine();
}
```