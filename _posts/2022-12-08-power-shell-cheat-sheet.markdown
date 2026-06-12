---
title:  "Power Shell cheat sheet"
tags:
  - tools
  - command-line
  - dotnet
---

I figured that I should keep track of some useful command-line tools that I am learning, so I'll write down them as blog posts and keep updating them.

*edit 2026-05-25: added a few commands around finding which executable is actually being used on Windows, and a couple of related `PATH` debugging tricks.*

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

    PS C:\> ( Measure-Command { cm.exe version } ).TotalMilliseconds
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

## ConvertFrom-Json

An equivalent to unix `| jq` Json reader/formatter in PowerShell

    curl.exe http://localhost:18104/api/xxx -X GET -H "content-type: application/json" --header "Authorization: <token>" | ConvertFrom-Json

## Find which executable is actually being used

In PowerShell, list **all** matches across `PATH`, in the order they would be resolved:

    Get-Command cmake.exe -All | Select-Object Source

Or, the `cmd.exe` equivalent (also works from PowerShell since it is just an `.exe`):

    where cmake

## Resolve the single path that *will* be executed

If you just want the one binary that would actually run:

    (Get-Command cmake.exe).Path

## Check the current PATH order

Useful right after the previous command, to understand *why* the wrong copy wins, listing one entry per line in resolution order:

    $env:Path -split ';'

To filter only the likely culprits:

    $env:Path -split ';' | Select-String -Pattern 'cmake'

And to do the same for the user-scoped or machine-scoped `PATH` :

    [Environment]::GetEnvironmentVariable('PATH', 'User')    -split ';'
    [Environment]::GetEnvironmentVariable('PATH', 'Machine') -split ';'

## List environment variables

PowerShell exposes environment variables as a drive:

    Get-ChildItem env:
    Get-ChildItem env:Path
