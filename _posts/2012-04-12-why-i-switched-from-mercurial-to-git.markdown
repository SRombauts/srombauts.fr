---
title:  "Why I switched from Mercurial to Git"
date:   2012-04-12 22:57:00 +0200
tags:
  - tools
  - vcs
  - SQliteCpp
---

After a few month using Mercurial (see my blog post [Mercurial to replace SVN][SwitchToMercurial] from a year ago) I switched to [Git][Git].

I’ve always been tempted to use Git, since this Tech Talk by Linus Torvalds in May 3, 2007:
{% include video id="4XpnKHJAok8" provider="youtube" %}

I even tried it a few times, but Mercurial commands seem more familiar to a Subversion user, and at this time, Mercurial GUI was more user friendly.

But then half a year ago, I wanted to convert to Mercurial our SVN code base at work, which is something like 15 man-years of C++.
I used the [Mercurial ConvertExtension](http://mercurial.selenic.com/wiki/ConvertExtension#Converting_from_Subversion). The process took hours, used a few gigabytes on disk, but **failed after using too much memory**.

![Old Git Logo](/assets/images/Git-logo-300x109.png)

This failure was a clear signal: I started with the [Git – SVN Crash Course](http://git-scm.com/course/svn.html).

![New Git Logo](/assets/images/git-logo-2color-lightbg%402x.png)

I used the [git-svn clone](https://git-scm.com/book/en/v2/Git-and-Other-Systems-Migrating-to-Git) command, which also took a few hours to run, but succeeded after a shorter time, only using 600 megabytes. This was not even twice the size of the SVN working copy, but with the full history of our project!

Since then, I started using git for all my private repositories: I converted losslessly my private repositories, thanks to the marvelous [Hg-Git Mercurial plugin](https://hg-git.github.io/).

I also registered to [Github][Github], and discovered a whole new dimension to open-source development!

![Github Logo](/assets/images/github_logo.png)

There I truly discovered the power of a typical open-source [Git workflow: A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/) or more recently [Github flow](https://docs.github.com/en/get-started/quickstart/github-flow): the way to clone (fork) a repository, to make a correction, and then to make a pull request, fully integrated in the issue tracker.

Now, I am beginning to use the hosting facilities of the [GitHub Pages](https://pages.github.com/), and I must say that I am perfectly happy with their automatic Pages Generator that helps me [advertise my own open source work (SQLiteCpp)](http://srombauts.github.io/SQLiteCpp/) (see [SQLiteC++, a smart and easy to use C++ SQLite3 wrapper][SQLiteCpp]).

![Tortoise Git Logo](/assets/images/TortoiseGit-logo.png)

And for the tools? GitHub help a lot creating, cloning and merging repositories. Under Linux I’ve become used to the good git command line. Under Windows, I am using the wonderful [TortoiseGit][TortoiseGit] GUI that I would recommend to you, at least to start.

![SmartGit Logo](/assets/images/smartgit_logo.png)

I have also started testing other tools that would help the transition at my workplace, where some developer used the popular [SmartSVN (pro)][SmartSVN]. So I have played a bit with [SmartGit][SmartGit] and made some feedback to the awesome 2 developers behind it, it sounds promising!

Now I can tell you: if you try Git, and take the time to learn it subtleties, you will love it!

[Git]: https://git-scm.org/
[Github]: https://github.com/
[TortoiseGit]: https://tortoisegit.org/
[SmartSVN]: https://www.smartsvn.com/
[SmartGit]: https://www.syntevo.com/smartgit/

[SwitchToMercurial]: /2011/02/20/mercurial-to-replace-svn/
[SQLiteCpp]: /2012/04/04/SQLiteCpp-0.1.0/
