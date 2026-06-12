---
title: "Android 2.3 NativeActivity"
date: 2011-03-01 22:36:11 +0100
tags:
  - android
---

At each platform API revision, the C native APIs are growing, giving access to new native library, and bringing each time more functionalities to the low level world of C/C++. At this point, they are starting to look mature enough for me to want to dive into them.

As [discussed earlier](/2010/12/06/android-native-development-kit/), Android 2.3 (API-9) brings to the C/C++ developers a new Java Class called "[NativeActivity](http://developer.android.com/reference/android/app/NativeActivity.html)". This allow us to write an entire Android application without using the Java API, managing inputs, internal sensors and the application window entirely with the so called native C APIs of the platforms.

The provided "native-activity" sample ("**[android-ndk-r5/samples/native-activity](http://www.srombauts.fr/android-ndk-r5b/samples/native-activity/)**", or in the [online documentation of the NativeActivity Class](http://developer.android.com/reference/android/app/NativeActivity.html)) gives you an example of making use of this new API through a threaded "app-glue" helper. The [web page What is the NDK](http://developer.android.com/sdk/ndk/overview.html#samples) does explain how to create a project from sources of this sample, with or without Eclipse. I made it work flawlessly under the [emulator](http://developer.android.com/guide/developing/tools/emulator.html) (as I am currently stuck with Android 2.2, API level 8).

The "native_app_glue" wrapper ("**[android-ndk-r5/sources/android/native_app_glue](http://www.srombauts.fr/android-ndk-r5b/sources/android/native_app_glue/)**") is designed to abstract the complexity of creating a native pthread and synchronizing it with the NativeActivity Lifecyle callbacks. It thus manage for you most of the work needed to handle the complexity of the classical transition (onCreate, onStart, onSaveInstanceState, onResume...) but also more dirty tasks like managing the application window (onNativeWindowCreated...) or the input events looper (onInputQueueCreated...)

But if you want to really understand all the magic behind this app glue, if like me you want to make your own by yourself (for instance in C++), it will need time to dig in it, as there is no comments to help the reader ! I will update this post with a commented version of my C++ implementation, in a step by step process with explanations.
