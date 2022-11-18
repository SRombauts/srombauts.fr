---
layout: single
title:  "Unreal Engine 4.11 Plastic SCM Source Control Provider"
date:   2016-04-25 22:00:00 +0200
---
I have been working hard for the past month to develop a new [Unreal Engine 4 Source Control plugin (Github)][UEPlasticPlugin] for [Plastic SCM][plasticscm.com] (think modern Perforce with efficient and understandable GUI and very powerful branching management, with some Git interoperability).

I’ve been using [my previous work (blog)][UE41GitPlugin] on the [Git Plugin for Unreal Engine 4 (Github)][UEGitPlugin]: ([now officially integrated in Engine (blog)][UE47GitPlugin]) to get the infrastructure work in a short time. Then I had to refactor a lot of it since the workflow of Plastic SCM is nothing like Git.

So here I am with [a third alpha release (Github)][0.3-alpha], now already stable and useful:

* status icons for assets
* check-out files
* add, rename, delete asset files
* check-in
* history log of an asset
* Visual Diff of Blueprints

![CreateWorkspace](https://github.com/SRombauts/UEPlasticPlugin/raw/1.0.0/Screenshots/UE4PlasticPlugin-CreateWorkspace.png)

Disclaimer: I’ve done this work for Codice Software, the company behind Plastic SCM.

Edit: [Announcement post in the Community Content section of Unreal Engine forums (UE forums)][ForumPlasticPlugin]. This thread has been updated with each subsequent releases of the plugin.

[UEPlasticPlugin]:    https://github.com/SRombauts/UE4PlasticPlugin
[UEGitPlugin]:        https://github.com/SRombauts/UEGitPlugin
[plasticscm.com]:     https://plasticscm.com/
[UE41GitPlugin]:      /2014/05/10/unreal-engine-4-1-git-plugin-alpha/
[UE47GitPlugin]:      /2015/02/25/unreal-engine-4-7-released-with-my-git-source-control-plugin/
[0.3-alpha]:          https://github.com/SRombauts/UEPlasticPlugin/releases/tag/0.3.0-alpha
[ForumPlasticPlugin]: https://forums.unrealengine.com/community/community-content-tools-and-tutorials/80750-plastic-scm-source-control-provider?108688-Plastic-SCM-Source-Control-Provider
