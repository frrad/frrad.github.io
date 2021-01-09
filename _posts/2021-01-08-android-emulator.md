---
layout: post
title:  "Setting up Android Emulator"
date:   2021-01-08
categories: blog, android
---

Get Android Command Line Tools from [this site](https://developer.android.com/studio).

```
CLT=commandlinetools-linux-6858069_latest.zipw
get https://dl.google.com/android/repository/$CLT && unzip $CLT
```

In order to use these tools you may need to install java with for instance 

```
sudo apt-get install default-jre
```

set up dir

```
export ANDROID_SDK_ROOT=$HOME/sdkroot
mkdir -p $ANDROID_SDK_ROOT/cmdline-tools
mv cmdline-tools tools # rename previously extracted tools
mv tools $ANDROID_SDK_ROOT/cmdline-tools

cd $ANDROID_SDK_ROOT/cmdline-tools/tools/bin
./sdkmanager --install "system-images;android-29;default;x86"

```
