---
title:  "Mercurial to replace SVN"
date:   2011-02-20 22:31:00 +0100
tags:
  - tools
  - vcs
---

For what I’ve seen in the last few month, it seems that [Mercurial (Hg)][Mercurial], a Distributed Version Control System (DVCS, or Distributed Source Code Management) is becoming to replace [Subversion (SVN)][Subversion] in many Open Source projects… at least when [Git][Git] is not already in the place!

![Mercurial Logo](/assets/images/mercurial_logo.png) 

While I am in it, Hg and Git have both been started on april 2005, shortly after the announcement that the free version of BitKeeper will be stopped.

![TorsoiseHg](/assets/images/TortoiseHg_logo.png)

Google Project and SourceForge are providing Mercurial as a choice of DVCS, and many tools are compatible with it. I’am using [TortoiseHg][TortoiseHg], as I’ve used [TortoiseSVN][TortoiseSVN] for many years now (in the same way, there is [TortoiseGit][TortoiseGit]).

For Android development, what I appreciate in Mercurial is that it does not cluster the working copy of my projects with “.svn” subdirectories like Subversion ! Instead, there is a single “.hg” directory, and this help a lot when working with Eclipse (no need to exclude explicitly “.svn” in the “src/” directory) as well as for performance/responsiveness!

I’ve quickly learned to use Mercurial with the famous [“Hg Init” Mercurial tutorial][HgInit], which start by a “***Subversion Reeducation***“!

Here you can find some articles I’ve read about Hg and Git (and choosing among them) :

- [stevelosh: The real difference between mercurial and git](http://stevelosh.com/blog/2010/01/the-real-difference-between-mercurial-and-git/) "I personally find Mercurial's philosophy easier to work with."
- [importantshock: Git vs Mercurial](http://importantshock.wordpress.com/2008/08/07/git-vs-mercurial/) "Git is MacGyver", "Mercurial is James Bond"
- [extracheese: why i switched to git from mercurial](https://web.archive.org/web/20180218130746/http://blog.extracheese.org/2010/05/why-i-switched-to-git-from-mercurial.html) "Mercurial is bad at handling large amounts of data.", "Mercurial is not safe."

Please note that I did NOT really make a choice: I only started to use Hg because its used on some open source projects I am following!

Edit: for installation instruction, see [Hg installation on a webserver (HgWebDirStepByStep)](http://mercurial.selenic.com/wiki/HgWebDirStepByStep) and in my case, installation for Debian 5.0. I use a simple “.htaccess” file to restrict access to my server.

Edit 2: please, have a look at my newer post [Why I switched from Mercurial to Git][SwitchToGit]

[Mercurial]: https://www.mercurial-scm.org/
[Subversion]: https://subversion.apache.org/
[Git]: https://git-scm.org/
[TortoiseHg]: https://tortoisehg.bitbucket.io/
[TortoiseSVN]: https://tortoisesvn.net/
[TortoiseGit]: https://tortoisegit.org/
[HgInit]: https://hginit.github.io/

[SwitchToGit]: /2012/04/12/why-i-switched-from-mercurial-to-git/
