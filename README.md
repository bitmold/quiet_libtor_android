These instructions are for building `libtor.so` for Android with an arm64-v8a chipset on a Debian based system.

First install the prerequisite packages:

```bash
sudo apt install autotools-dev
sudo apt install automake
sudo apt install autogen autoconf libtool gettext-base autopoint
sudo apt install git make g++ pkg-config openjdk-17-jdk openjdk-17-jre
```

Then obtain the Android SDK and NDK. The Android SDK is installed by default with Android Studio, and the NDK 25.2.9519654 can be downloaded from within Android Studio's SDK manager.

Then set these environment variables for the SDK and NDK:

```bash
export ANDROID_HOME=~/Android/Sdk
export ANDROID_NDK_HOME=~/Android/Sdk/ndk/25.2.9519653
```

Be sure that you have all of the git submodules up-to-date:
```bash
./tor-droid-make.sh fetch -c
```

To build, run:
```bash
./tor-droid-make.sh build 
```

This will produce `external/lib/arm64-v8a/libtor.so` which can be placed in `quiet/packages/mobile/android/app/src/main/jniLibs/arm64-v8a` to be bundled into the Quiet APK.
