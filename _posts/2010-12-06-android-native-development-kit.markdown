---
title: "Android Native Development Kit"
date: 2010-12-06 21:41:49 +0100
tags:
  - android
---

[Android 2.3 Gingerbread](http://developer.android.com/sdk/android-2.3.html) has been announced, and what I find the most interesting in it is related to the [Native Development KIT (NDK)](http://developer.android.com/sdk/ndk/index.html) coming with it; the NDK r5.

![Android Native Development Kit](/assets/images/Android-NDK.jpg)

The new [API level](http://developer.android.com/guide/appendix/api-levels.html) 9 of Android 2.3 brings with it a "Native access to Activity lifecycle" : it allows developers to write an Android Application with absolutely no Java coding, by the use of a provided Java Class "[NativeActivity](http://developer.android.com/reference/android/app/NativeActivity.html)". A "native-activity" sample gives you an example of making use of it through the "native_app_glue", a C-only wrapper (see also [my experiments on NativeActivity](/2011/03/01/android-2-3-nativeactivity/)).

At the same time this revision r5 of the NDK is becoming interesting for me, with the first official support of **C++ exception and RTTI**. There is also a way to get a "standalone toolchain" with GCC 4.3, which give the ability to use only standard cross-compiler command (*make*) instead of the specific Android.mk files.

All this is not really well documented... You get plenty of example and sources, but there is not much *in-code* comments nor any "Native API Reference" available. In fact, even the documentation is not available directly on Internet: it is only provided on the NDK archive!

I share it on this web server : [here is the NDK-r5b HTML documentation](http://www.srombauts.fr/android-ndk-r5b/documentation.html) ([http://www.srombauts.fr/android-ndk-r5b/](http://www.srombauts.fr/android-ndk-r5b/))

Edit: look at this Android Developer [Blog post about Gingerbread NDK](http://android-developers.blogspot.com/2011/01/gingerbread-ndk-awesomeness.html)
Edit2: there is also a [android-ndk Google group](http://groups.google.com/group/android-ndk)
Edit3: some other people [share my enthusiasm about Gingerbread and the new NDK](http://www.badlogicgames.com/wordpress/?p=1315) revision !
