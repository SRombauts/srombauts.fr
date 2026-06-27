---
layout: single
title: Portfolio
permalink: /portfolio/
---

Showcase of a few of [my Github repositories](https://github.com/SRombauts)

## AI-assisted software engineering

A proeminent part of my recent work is about making AI coding agents useful on our big internal codebases: repository instructions ([`AGENTS.md`][agents] / `CLAUDE.md`), reusable skills, slash commands and MCP servers.
I learned and teached team member to treat the coding agent like new hire that we have to onboard, and then review thoroughly and iterate on both the code AND the skills!

This blog is a small example of that process. Have a look at its [`AGENTS.md`][agents]: it documents the repository instructions and the skills I rely on here, including the MIT-licensed `humanizer` skill I run on every post. A longer write-up series is in the works and will show up under the [ai tag][aitag].

For more advanced setup, see the following of my repositories.
My long-running [SQLiteC++][SQLiteCpp] library carries [a similar set of project skills][sqlitecppskills] for its builds, tests and releases.
[pong-sdl3-cpp][pong] is an in-progress C++/SDL3 Pong I built mainly to exercise the process, with its own [`.claude/skills/`][pongskills], a [roadmap][pongroadmap], CI and unit tests.

## Unreal Engine

* [UE Git Plugin][UEGitPlugin.io] ([repo][UEGitPlugin]): the official Unreal Engine Git Source Control Provider Plugin.
* [UE Plastic SCM Plugin][UEPlasticSCMPlugin.io] ([repo][UEPlasticSCMPlugin]): the official Unreal Engine Plastic SCM Source Control Provider Plugin.
![Submit Files to Source Control](https://raw.githubusercontent.com/SRombauts/UEPlasticPlugin/master/Screenshots/UEPlasticPlugin-SubmitFiles.png)

* [UE4 Procedural Mesh][UE4ProceduralMesh]: using the Unreal Engine 4 UProceduralMeshComponent. ![ProceduralMeshActor](https://raw.githubusercontent.com/SRombauts/UE4ProceduralMesh/master/ProceduralMesh.png "Proceduraly generated Mesh Actor")

* [UE4 Architecture Vis Demo][UE4ArchVisDemo.io] ([repo][UE4ArchVisDemo]): run a live demo in the browser using HTML5. [![ArchVis Demo screenshot](https://raw.githubusercontent.com/SRombauts/UE4ArchVisDemo/master/Screenshots/UE4ArchVisDemo.png)](https://srombauts.github.io/UE4ArchVisDemo/)
*Click the image for the HTML5/WebAssembly live demo*
* [UE4 Quick Start][UE4QuickStart]: a mix of various Unreal Engine 4 C++ Tutorials, based on the [Programming Quick Start](https://dev.epicgames.com/documentation/unreal-engine/unreal-engine-cpp-quick-start) guide.

## C++

* [SQLiteC++][SQLiteCpp.io] ([repo][SQLiteCpp]): a smart and easy to use C++ wrapper to the SQLite3 library. ![SQLite logo](https://www.sqlite.org/images/sqlite370_banner.gif)
* [SimplexNoise][SimplexNoise]: A Perlin’s Simplex Noise C++ Implementation (1D, 2D, 3D).
![2D Simplex fractal noise, 7 octaves](/assets/images/SimplexNoise-2D-7octaves.jpg) 2D image of fractal noise with 7 octaves of 2D Simplex Noise (from my [SimplexNoiseCImg example project](https://github.com/SRombauts/SimplexNoiseCImg))
* [shared_ptr][shared_ptr.io] ([repo][shared_ptr]): a minimal light and fast shared_ptr implementation designed to handle cases where boost/std::shared_ptr are not available. ![Shared Pointer UML](/assets/images/shared_ptr-uml.png)

* [LoggerC++][LoggerCpp.io] ([repo][LoggerCpp]): a simple, elegant and efficient C++ logger library.
* [HtmlBuilder][HtmlBuilder]: a simple C++ HTML DOM generator (used in a couple embedded webservice). ![HTML5 logo](https://upload.wikimedia.org/wikipedia/commons/6/61/HTML5_logo_and_wordmark.svg)

## Games and SDL

* [pong-sdl3-cpp][pong] ([roadmap][pongroadmap]): a Pong clone in modern C++ with SDL3 and CMake, built from scratch without a game engine. Work in progress: the window, game loop, playfield, paddles and keyboard input are in place; ball physics, scoring and the menus are still on the roadmap. It also doubles as the AI-assisted methodology sandbox described above.

## Other experiments

Smaller things I have played with over the years, some of which may get a fuller write-up later:

* [Entity Component Systems][ecs]: a small ECS experiment in Python.
* [SDL][sdl]: 2D game and prototype experiments (the SDL3 Pong above is the current one).
* OpenGL, including [gltext][gltext], a tiny OpenGL text-rendering helper.
* [Ogre 3D][Ogre3D].
* [ZeroMQ][ZMQCpp]: C++ bindings for the message-queue library.

[UEGitPlugin.io]: https://srombauts.github.io/UEGitPlugin
[UEGitPlugin]:    https://github.com/SRombauts/UEGitPlugin
[UEPlasticSCMPlugin.io]: https://srombauts.github.io/UEPlasticPlugin
[UEPlasticSCMPlugin]:   https://github.com/SRombauts/UEPlasticPlugin

[UE4ProceduralMesh]: https://github.com/SRombauts/UE4ProceduralMesh
[UE4ArchVisDemo.io]: https://srombauts.github.io/UE4ArchVisDemo
[UE4ArchVisDemo]: https://github.com/SRombauts/UE4ArchVisDemo
[UE4QuickStart]:  https://github.com/SRombauts/UE4QuickStart

[SQLiteCpp.io]: https://srombauts.github.io/SQLiteCpp
[SQLiteCpp]:    https://github.com/SRombauts/SQLiteCpp
[SimplexNoise]: https://github.com/SRombauts/SimplexNoise
[shared_ptr.io]:  https://srombauts.github.io/shared_ptr
[shared_ptr]:     https://github.com/SRombauts/shared_ptr

[pong]: https://github.com/SRombauts/pong-sdl3-cpp
[pongroadmap]: https://github.com/SRombauts/pong-sdl3-cpp/blob/main/docs/ROADMAP.md
[pongskills]: https://github.com/SRombauts/pong-sdl3-cpp/tree/main/.claude/skills
[sqlitecppskills]: https://github.com/SRombauts/SQLiteCpp/tree/master/.claude/skills

[LoggerCpp.io]: https://srombauts.github.io/LoggerCpp
[LoggerCpp]:    https://github.com/SRombauts/LoggerCpp
[HtmlBuilder]:  https://github.com/SRombauts/HtmlBuilder

[agents]: https://github.com/SRombauts/srombauts.fr/blob/master/AGENTS.md
[aitag]: https://srombauts.eu/tags/

[ecs]: https://github.com/SRombauts/ecs
[sdl]: https://www.libsdl.org/
[gltext]: https://github.com/SRombauts/gltext
[Ogre3D]: https://www.ogre3d.org/
[ZMQCpp]: https://github.com/SRombauts/ZMQCpp
