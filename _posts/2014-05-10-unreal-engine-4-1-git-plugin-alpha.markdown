---
layout: single
title:  "Unreal Engine 4.1 Git Plugin alpha"
date:   2014-05-10 12:40:00 +0200
---

So at last I’ve started implementing an [open source C++ Git Source Control Plugin (Github)][UEGitPlugin] for Unreal Engine 4.1.

![Git Logo](https://git-scm.com/images/logos/2color-lightbg@2x.png){: width="250" }

For know it is barely a Windows-only “pre-alpha v0.0” version. It does only provide overlay icons to show status of your project content assets.

But it’s a start, and it will soon become more useful, [I’ll keep you informed on the forums (UE forums)][ForumSourceControl].

1. Edit 2014/05/17: [UE4 Git Plugin alpha v0.1 released (Github)][0.1-alpha], with history log, revert, add and delete. Still no diff (next step) nor commit.
2. Edit 2014/05/20: [UE4 Git Plugin alpha v0.2 released (Github)][0.2-alpha], with diff fully working. Still no commit (next/last big step) but know really useful for anyone using Git.
3. Edit 2014/05/21: [UE4 Git Plugin alpha v0.3 released (Github)][0.3-alpha], with commit working for small batch of files.
As its quickly reaching completion, I’ve started a [dedicated new thread on the “Engine Source & GitHub” section (UE forums)][ForumGitPlugin] (still not ready for the more general “Tools” section I think).
4. Edit 2014/05/30: [UE4 Git Plugin alpha v0.4 released (Github)][0.4-alpha], with many bug fixes and improvements to usability.
I’ve started to use it “for real” in my own small projects.
As I see it, I will move on “Beta” for the next version, to reflect this increased stability.
Please let me know if you try it, an report any bug or missing feature.
5. Edit 2015/02/25: [Now **officially integrated in UE4.7**! (blog)][UE47GitPlugin]

![SourceControlLogin_Init](https://github.com/SRombauts/UEGitPlugin/raw/master/Screenshots/SourceControlLogin_Init.png)

[UEGitPlugin]:    https://github.com/SRombauts/UEGitPlugin
[ForumSourceControl]: https://forums.unrealengine.com/unreal-engine/feedback-for-epic/615-additional-source-control-providers-support?p=167837#post167837
[0.1-alpha]:      https://github.com/SRombauts/UE4GitPlugin/releases/0.1-alpha
[0.2-alpha]:      https://github.com/SRombauts/UE4GitPlugin/releases/0.2-alpha
[0.3-alpha]:      https://github.com/SRombauts/UE4GitPlugin/releases/0.3-alpha
[ForumGitPlugin]: https://forums.unrealengine.com/showthread.php?6809-Git-Source-Control-Provider-Plugin
[0.4-alpha]:      https://github.com/SRombauts/UE4GitPlugin/releases/0.4-alpha
[UE47GitPlugin]:  /2015/02/25/unreal-engine-4-7-released-with-my-git-source-control-plugin/
