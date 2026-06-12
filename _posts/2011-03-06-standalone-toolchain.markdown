---
title: "Standalone toolchain"
date: 2011-03-06 18:07:46 +0100
tags:
  - android
  - tutorial
---

Since the [revision 5 of the Native Development Kit previously discussed](/2010/12/06/android-native-development-kit/), the NDK can be customized to obtain a standard GCC cross compiler toolchain. This means that you can use it with standard Makefile and make command, or with more sophisticated build tools like automake, CMake or Bakefile. No more Android.mk ant Application.mk proprietary format required ! This is great in many situation where you want to recompile a complex software with big libraries. Lets have a try !

For this experimental article, I'll assume that you already have good knowledge of Android development, SDK, ADB and some good understanding of C/C++ compilation workflow (gcc, make and Makefile).

[NDK Requirements](http://developer.android.com/sdk/ndk/overview.html#reqs) :

- Android SDK (yes, the Java part !) : I'll use API-level 5 (Android 2.0) but the minimum is API-level 3 (Android 1.5): "~/android-sdk-linux_x86/"
- Android NDK r5b (the C/C++ part): "~/android-ndk-r5b/"
- GNU Make 3.81 or later ("make" package under Ubuntu or Debian)
- GNU awk or equivalent (nawk says the documentation, I have mawk)

To make this work under Windows (XP or 7) you'll need Cygwin 1.7 installed, but it's not that simple (the standalone toolchain officially dos not support Cygwin...). For that reason I've decided to work on this entirely under Linux (latest Ubuntu in my case). I you want to try to make it work under Windows, you could exploit useful information from the following blog post [http://www.pocketmagic.net/?p=1462](http://www.pocketmagic.net/?p=1462) and from some other Internet sources.

So let's start by reading the "[/android-ndk-r5b/docs/STANDALONE-TOOLCHAIN.html](https://web.archive.org/web/20120720004459/http://www.srombauts.fr/android-ndk-r5b/docs/STANDALONE-TOOLCHAIN.html)", and proceed directly with the instructions on section 3 "Invoking the compiler (the easy way)". Under a Linux console, type:

```
~/android-ndk-r5b/build/tools/make-standalone-toolchain.sh --platform=android-5 --install-dir=$HOME/android-ndk-r5b/standalone-toolchain-api5
```

Then add this few lines to the end of your .bashrc file and restart a console (or type them directly on the console):

```
PATH=$PATH:$HOME/android-sdk-linux_x86/tools
PATH=$PATH:$HOME/android-sdk-linux_x86/platform-tools
PATH=$PATH:$HOME/android-ndk-r5b/standalone-toolchain-api5/bin/
```

Then, create a standard hello world "hello-ndk.c":

```c
#include <stdio.h>

int main(void)
{
    printf("Hello from NDK\n");
    return 0;
}
```

At this stage, compiling for Android works easily with the following command:

```
arm-linux-androideabi-gcc  hello-ndk.c -o hello-ndk
```

Before testing it, we would like to add a bit of android API in it. You can easily complete it with a minimal Android log (logcat for Eclipse) :

```c
#include <stdio.h>
#include <android/log.h>

#define LOGI(...) ((void)__android_log_print(ANDROID_LOG_INFO, "hello-ndk", __VA_ARGS__))

int main(void)
{
    printf("Hello from NDK\n");
    LOGI("Hello from NDK");
    return 0;
}
```

For this, you need to link explicitly with a the "liblog" library :

- arm-linux-androideabi-gcc  hello-ndk.c -l log -o hello-ndk

Here is a Makefile to handle this with a simple "make" command (or other "make clean" and "make clean all" variants):

```makefile
CC	= arm-linux-androideabi-gcc
CFLAGS	= -Wall -g
LDFLAGS	= -llog
SRC	=hello-ndk.c
OBJ	=$(SRC:.c=.o)
EXE	=hello-ndk

all: $(SRC) $(EXE)

$(EXE): $(OBJ)
	$(CC) -o $@ $^ $(LDFLAGS)

%.o: %.c
	$(CC) -o $@ -c $< $(CFLAGS)

clean:
	rm -f *.o $(EXE)
```

This create the standalone executable **hello-ndk**, so if your device is rooted, you can use adb to copy and execute "hello-ndk" on it, like this:

```shell
% adb shell
$ su
# mkdir /data/tmp
# chmod 777 /data/tmp
# exit
$ exit
% adb push hello-ndk /data/tmp
% adb shell
$ /data/tmp/hello-ndk
```

You should get a "Hello from NDK" on the command line, and the same message on the logcat window of Eclipse (in green, info level).

![Hello NDK Logcat](/assets/images/Hello-NDK-Logcat.png)

For normal users that are not root (no "su" command), there is no way (oops, see edit bellow) of launching directly a native application under Android: you have to package it in a standard Android application .apk and use it from Java code. See [http://gimite.net/en/index.php?Run%20native%20executable%20in%20Android%20App](http://gimite.net/en/index.php?Run%20native%20executable%20in%20Android%20App).

edit: look at the comment from pitypang, the path /data/local/tmp should work for an unrooted phone !

So we need to build instead a shared library, a ".so" file to be loaded by a Java application (through Java Native Interface, JNI). For this, we need to modify the Makefile like this :

```makefile
CC	= arm-linux-androideabi-gcc
CFLAGS	= -Wall -g
LDFLAGS	= -llog -shared
SRC	=hello-ndk.c
OBJ	=$(SRC:.c=.o)
EXE	=libhello-ndk.so
```

With this you will get a **libhello-ndk.so** shared library. This will do nothing interesting by itself; we need to invoke the native function from Java, or to use the NativeActivity.

I will update this post later to make this works.

Edit:  look also at my post on [CMake for Android](/2011/03/15/cmake-for-android/)
Edit 2015: and at my updated [Android NDK r10e and Standalone Toolchain on Ubuntu 14.04](/2015/08/21/android-ndk-r10c-on-ubuntu-14-04/) post.
