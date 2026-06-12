---
title: "CMake for Android"
date: 2011-03-15 20:09:32 +0100
tags:
  - android
  - tutorial
---

[Last time, we've seen how to install and test the standalone toolchain of the NDK](/2011/03/06/standalone-toolchain/) to build a native shared library with a **standard Makefile & make command** under Linux.

![CMake Logo](/assets/images/cmake_logo.png)

But nowadays, many open source libraries and projects does not directly come with a Makefile, instead using a build system to automate its generation. CMake is becoming more and more used for those kind of jobs, so being able to use it for Android is really interesting. And easy!

A CMake configuration file for Android (*android.toolchain.cmake*) is provided by the [**android-cmake** Google project](http://code.google.com/p/android-cmake/) hosted on Mercurial ([see my previous post on Mercurial](/2011/02/20/mercurial-to-replace-svn/)). Let's clone its repository in the home directory with the following commands:

```
hg clone https://android-cmake.googlecode.com/hg/ android-cmake
```

Then, add to your .bashrc the ANDROID_NDK_TOOLCHAIN_ROOT and ANDTOOLCHAIN environment variables pointing to NDK and to the cmake config file. I also added a simple alias for later use:

```shell
PATH=$PATH:$HOME/android-sdk-linux_x86/tools
PATH=$PATH:$HOME/android-sdk-linux_x86/platform-tools
PATH=$PATH:$HOME/android-ndk-r5b/standalone-toolchain-api5/bin/

ANDROID_NDK_TOOLCHAIN_ROOT=$HOME/android-ndk-r5b/standalone-toolchain-api5
ANDTOOLCHAIN=$HOME/android-cmake/toolchain/android.toolchain.cmake

alias cmake-android='cmake -DCMAKE_TOOLCHAIN_FILE=$ANDTOOLCHAIN'
```

Ok, let's try to compile the "hello-cmake" sample provided by the Google project ([see hello-cmake documentation](http://android-cmake.googlecode.com/hg/docs/hello-cmake.html)):

```shell
cd ~/android-cmake/samples/hello-cmake/
mkdir build
cd build
export ANDROID_NDK_TOOLCHAIN_ROOT
cmake -DCMAKE_TOOLCHAIN_FILE=$ANDTOOLCHAIN ..
```

We can simplify the last command by using our alias, so next type we will use "cmake-android .." instead.
At this stage, CMake has generated the **Makefile** for you. Use it to build the sample:

```
make
```

Here you are, the shared library has been build and is ready for integration in an Application. You can find it here:

```
~/android-cmake/samples/hello-cmake/libs/armeabi-v7a/libhello-cmake.so
```

Now we want to invoke this native library from a Java Application, using JNI. This is documented in the next provided sample, "[hello-android-cmake](http://android-cmake.googlecode.com/hg/docs/hello-android-cmake.html)", which is the Java counterpart of the C application we've build.

Copy the above "libs" directory to `~/android-cmake/samples/hello-android-cmake`. Then open Eclipse and start a "File->New...->Project...->Android Project". Select "create project from existing source" and give it the `~/android-cmake/samples/hello-android-cmake` path.

Build the application, and launch it on an emulator or an actual device. You should see an activity showing the multi-line text starting by "JNI — pi = 3.14159..." coming from our shared library!

![Hello Android CMake](/assets/images/HelloAndroidCMake.png)

Here you are!
