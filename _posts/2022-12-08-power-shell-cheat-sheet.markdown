---
title:  "Power Shell cheat sheet"
tags:
  - tools
  - command-line
  - dotnet
---

I figured that I should keep track of some useful command-line tools that I am learning, so I'll write down them as blog posts and keep updating them.

## Benchmarking .NET 7

I got started by this video {% include video id="sa3XsvSiMtk" provider="youtube" %}

### Measure-Command

Default output of Measure-Command, using git.exe as a benchmark for a real-life native application:

    PS C:\> Measure-Command { git.exe --version | Out-Default }
    git version 2.35.1.windows.2


    Days              : 0
    Hours             : 0
    Minutes           : 0
    Seconds           : 0
    Milliseconds      : 47
    Ticks             : 476314
    TotalDays         : 5.51289351851852E-07
    TotalHours        : 1.32309444444444E-05
    TotalMinutes      : 0.000793856666666667
    TotalSeconds      : 0.0476314
    TotalMilliseconds : 47.6314

 we can limit the result to TotalMilliseconds only:

    PS C:\> ( Measure-Command { git.exe --version } ).TotalMilliseconds
    47.8714

comparing to a full C# command line application using .NET runtime, this time Plastic SCM

    PS C:\> ( Measure-Command { cm.exe version ).TotalMilliseconds
    395.9726

with a simple C# console app I get better results (note that in this instance the Release build doesn't run any faster):

    PS C:\Workspace\NETConsoleApp1> (Measure-Command {.\bin\Debug\net7.0\NETConsoleApp1.exe}).TotalMilliseconds
    83.2977

Then, publishing as a [Native application, Ahead Of Time (AOT) compilation of .NET 7.0][native-aot]:

    dotnet publish -r win-x64 -c Release -p:PublishAot=true

gives us a bigger application, but much faster to start:

    PS C:\Workspace\NETConsoleApp1> (Measure-Command {.\bin\Release\net7.0-windows7.0\win-x64\publish\NETConsoleApp1.exe}).TotalMilliseconds
    24.717

[native-aot]: https://learn.microsoft.com/en-us/dotnet/core/deploying/native-aot/
