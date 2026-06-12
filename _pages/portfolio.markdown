---
layout: single
title: Portfolio
permalink: /portfolio/
---

Showcase of a few of [my Github repositories](https://github.com/SRombauts)

## AI-assisted software engineering

Most of my recent work is about making AI coding agents actually useful on real codebases: repository instructions ([`AGENTS.md`][agents] / `CLAUDE.md`), reusable skills, slash commands and MCP servers. I treat the agent like a junior dev I onboard and then review, not an oracle I argue with.

This very site is a small public example. Have a look at its [`AGENTS.md`][agents]: it documents the repository instructions and the skills I rely on here, including the MIT-licensed `humanizer` skill I run on every post. A longer write-up series is in the works and will show up under the [ai tag][aitag].

## Unreal Engine

* [UE Git Plugin][UEGitPlugin.io] ([repo][UEGitPlugin]): the official Unreal Engine Git Source Control Provider Plugin.
* [UE Plastic SCM Plugin][UEPlasticSCMPlugin.io] ([repo][UEPlasticSCMPlugin]): the official Unreal Engine Plastic SCM Source Control Provider Plugin.
![Submit Files to Source Control](https://raw.githubusercontent.com/SRombauts/UEPlasticPlugin/master/Screenshots/UEPlasticPlugin-SubmitFiles.png)

* [UE4 Procedural Mesh][UE4ProceduralMesh]: using the Unreal Engine 4 UProceduralMeshComponent. ![ProceduralMeshActor](https://raw.githubusercontent.com/SRombauts/UE4ProceduralMesh/master/ProceduralMesh.png "Proceduraly generated Mesh Actor")

* [UE4 Architecture Vis Demo][UE4ArchVisDemo.io] ([repo][UE4ArchVisDemo]): run a live demo in the browser using HTML5. [![ArchVis Demo screenshot](https://raw.githubusercontent.com/SRombauts/UE4ArchVisDemo/master/Screenshots/UE4ArchVisDemo.png)](https://srombauts.github.io/UE4ArchVisDemo/)
*Clic the image for the HTML5/WebAssembly live demo*
* [UE4 Quick Start][UE4QuickStart]: a mix of various Unreal Engine 4 C++ Tutorials, based on the [Programming Quick Start](https://dev.epicgames.com/documentation/unreal-engine/unreal-engine-cpp-quick-start) guide.

## C++

* [SQLiteC++][SQLiteCpp.io] ([repo][SQLiteCpp]): a smart an easy to use C++ wrapper to the SQLite3 library. ![SQLite logo](https://www.sqlite.org/images/sqlite370_banner.gif)
* [SimplexNoise][SimplexNoise]: A Perlin’s Simplex Noise C++ Implementation (1D, 2D, 3D).
![1 octave of 2D Simplex Noise](https://raw.githubusercontent.com/SRombauts/SimplexNoise/master/Screenshots/Simplex2D-7octaves.png) 2D image of fractal noise with 7 octaves of 2D Simplex Noise (from my [SimplexNoiseCImg example project](https://github.com/SRombauts/SimplexNoiseCImg))
* [shared_ptr][shared_ptr.io] ([repo][shared_ptr]): a minimal light and fast shared_ptr implementation designed to handle cases where boost/std::shared_ptr are not available. ![Shared Pointer UML](http://zhaoyan.website/xinzhi/cpp/html/pics/shared.png)

* [LoggerC++][LoggerCpp.io] ([repo][LoggerCpp]): a simple, elegant and efficient C++ logger library.
* [HtmlBuilder][HtmlBuilder]: a simple C++ HTML DOM generator (used in a couple embedded webservice). ![HTML5 logo](https://upload.wikimedia.org/wikipedia/commons/6/61/HTML5_logo_and_wordmark.svg)

## TODO

* Add references to my experiments with [Entity Component Systems (ecs)][ecs]
* Add references to my experiments with [SDL][sdl]
* Add references to my experiments with Open GL, including my little [gltext][gltext]
* Add references to my experiments with [Ogre 3D][Ogre3D]
* Add references to my experiments with [ZeroMQ (eg ZMQCpp)][ZMQCpp]

[UEGitPlugin.io]: http://srombauts.github.io/UEGitPlugin
[UEGitPlugin]:    https://github.com/SRombauts/UEGitPlugin
[UEPlasticSCMPlugin.io]: http://srombauts.github.io/UEPlasticPlugin
[UEPlasticSCMPlugin]:   https://github.com/SRombauts/UEPlasticPlugin

[UE4ProceduralMesh]: https://github.com/SRombauts/UE4ProceduralMesh
[UE4ArchVisDemo.io]: http://srombauts.github.io/UE4ArchVisDemo
[UE4ArchVisDemo]: https://github.com/SRombauts/UE4ArchVisDemo
[UE4QuickStart]:  https://github.com/SRombauts/UE4QuickStart

[SQLiteCpp.io]: http://srombauts.github.io/SQLiteCpp
[SQLiteCpp]:    https://github.com/SRombauts/SQLiteCpp
[SimplexNoise]: https://github.com/SRombauts/SimplexNoise
[shared_ptr.io]:  http://srombauts.github.io/shared_ptr
[shared_ptr]:     https://github.com/SRombauts/shared_ptr

[LoggerCpp.io]: http://srombauts.github.io/LoggerCpp
[LoggerCpp]:    https://github.com/SRombauts/LoggerCpp
[HtmlBuilder]:  https://github.com/SRombauts/HtmlBuilder

[agents]: https://github.com/SRombauts/srombauts.fr/blob/master/AGENTS.md
[aitag]: https://srombauts.eu/tags/

[ecs]: https://github.com/SRombauts/ecs
[sdl]: https://www.libsdl.org/
[gltext]: https://github.com/SRombauts/gltext
[Ogre3D]: https://www.ogre3d.org/
[ZMQCpp]: https://github.com/SRombauts/ZMQCpp
