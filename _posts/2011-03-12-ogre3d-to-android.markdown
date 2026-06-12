---
title: "Ogre3D to Android"
date: 2011-03-12 21:54:05 +0100
tags:
  - android
  - gamedev
---

![Ogre3D logo](/assets/images/ogre3d_logo.gif)

I've started to read a lot about Ogre3D, the open-source Object Oriented 3D Engine, which I've always considered to be a really interesting subject. This was triggered by a comment about ongoing effort to port of Ogre3D to Android !

This interest is going far beyond what I expected... I've begun by following the **[Ogre Basic Tutorials](http://www.ogre3d.org/tikiwiki/Basic+Tutorials)**, and I've already done some tests with elements from the **[more advanced Tutorials](http://www.ogre3d.org/tikiwiki/Tutorials)**, regarding the in-code mesh generation, and then terrain management and [paging management](http://www.ogre3d.org/tikiwiki/Paging+Scene+Manager)! I've followed this path into looking to environment generators, like [Ogre SkyX (sky)](http://www.ogre3d.org/tikiwiki/SkyX&structure=Libraries) and [Hydrax (water)](http://www.ogre3d.org/tikiwiki/Hydrax). I was sorry not to found any open-source outstanding project for plants, foliage and vegetation management :(

I was disappointed to see that the Ogre port to Android does not seems to be in a good shape; a least there was not much discussion on this recently, and there is no good documentation on how to proceed with the Android NDK :

- <http://www.ogre3d.org/tikiwiki/Ogre+Android&structure=Development>
- <http://www.ogre3d.org/forums/viewtopic.php?t=37608>
- <http://www.ogre3d.org/forums/viewtopic.php?f=21&t=63302>

For me, its kind of a very interesting challenge: I would like to improve the documentation on all this, a least to the point where I can bring it (I do not have much time for this).

First of all, I needed to read some more about the standard process for building Ogre with CMake:

- <http://www.ogre3d.org/tikiwiki/Building+Ogre>
- <http://www.ogre3d.org/tikiwiki/Building+Ogre+With+CMake>
- <http://www.ogre3d.org/tikiwiki/CMake+Quick+Start+Guide>

My first step will be to compile a minimal (monothreaded without Boost) Ogre 1.8 (unstable) from source for Linux:

- <http://www.ogre3d.org/developers/mercurial>
- <https://bitbucket.org/sinbad/ogre/>
