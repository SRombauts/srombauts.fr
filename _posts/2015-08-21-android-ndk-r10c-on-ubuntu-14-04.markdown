---
title: "Android NDK r10e and Standalone Toolchain on Ubuntu 14.04"
tags:
  - android
date: 2015-08-21 15:45:18 +0200
---

This is an update on my [previous post about Android NDK Standalone Toolchain on Ubuntu](http://www.srombauts.fr/2011/03/06/standalone-toolchain/), so have a look to it for better understanding.

We will see basic setup of the SDK & NDK. We will generate a standalone toolchain, for use with Android 4.1 Jelly Bean (target 90% of active devices). I then uses CMake to generate Makefiles. I am doing all this on the latest Ubuntu LTS (14.04).

![Ubuntu Logo](/assets/images/ubuntu-logo.png)

**Ubuntu 14.04 desktop 64-bit**:
[Ubuntu download page](http://www.ubuntu.com/download/desktop)
After standard installation, we need Java for the Android SDK, and a C/C++ development environment.

```
sudo apt-get install openjdk-7-jre ant
sudo apt-get install build-essential cmake
```

**Android SDK (the Java part, to bundle C++ in an APK, see [Native Activity](http://www.srombauts.fr/2011/03/01/android-2-3-nativeactivity/))**:
[Android SDK (r24.3.4) download page](http://developer.android.com/sdk/index.html)
SDK Tools Only, Linux
32 & 64-bit **android-sdk_r24.3.4-linux.tgz**
Uncompress under ~/android-sdk-linux/
Execute:

```
~/android-sdk-linux/tools/android
```

Add all packages from Android 4.1 – API Level16 (See [Adding SDK Packages](http://developer.android.com/sdk/installing/adding-packages.html))

**Android NDK (the C/C++ part)** ([Have a look at my standalone toolchain post](http://www.srombauts.fr/2011/03/06/standalone-toolchain/)):
[Android NDK guide](https://developer.android.com/ndk/guides/index.html) and [API reference](https://developer.android.com/ndk/reference/index.html)
[Android NDK download page](https://developer.android.com/ndk/downloads/index.html)
Platform Linux 64-bit (x86) **android-ndk-r10e-linux-x86_64.bin**

```
chmod u+x android-ndk-r10e-linux-x86_64.bin
```

Execute into your $HOME to uncompress the NDK under ~/android-ndk-r10e/

Extract a standalone toolchain for API level 16 (with default GCC 4.8):

```
~/android-ndk-r10e/build/tools/make-standalone-toolchain.sh --arch)arm --platform=android-16 --install-dir=$HOME/android-standalone-toolchain-api16
```

Or package it with the following command:

```
~/android-ndk-r10e/build/tools/make-standalone-toolchain.sh --platform=android-16
```

Add SDK & Standalone toolchain to your PATH, with your ~/.bashrc file:

```
$ echo 'PATH=$PATH:$HOME/android-sdk-linux/tools' >> ~/.bashrc
$ echo 'PATH=$PATH:$HOME/android-sdk-linux/platform-tools' >> ~/.bashrc
$ echo 'PATH=$PATH:$HOME/android-standalone-toolchain-api16/bin' >> ~/.bashrc
```

$ echo 'export ANDROID_STANDALONE_TOOLCHAIN=$HOME/android-standalone-toolchain-api16' >> ~/.bashrc

**Android CMake** (Have a look at my previous post on [CMake for Android](http://www.srombauts.fr/2011/03/15/cmake-for-android/)):
Download the [android-cmake now maintained on Github](https://github.com/taka-no-me/android-cmake)

Note: This is a work in progress, as I will need to refresh all my knowledge to switch to Android Studio in the following months.
