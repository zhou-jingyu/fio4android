fio - How to build fio with libaio enabled for Android
======================================================


Download Code and Build
-----------------------

You can download a prebuild for IA64 platform from here: 


Download Code and Build
-----------------------

Under AOSP source tree, run below command to download code and build:
::

    cd <PATH_TO_AOSP>/external
    git clone https://github.com/zhou-jingyu/fio4android.git --branch enable_libaio
    git clone https://github.com/zhou-jingyu/libaio.git
    cd <PATH_TO_AOSP>
    source build/envsetup.sh
    lunch <YOUR_TARGET>
    mmm external/libaio
    mmm external/fio4android

The build output to be used:
::

    out/target/product/<your target>/system/bin/fio
    out/target/product/<your target>/system/lib64/libaio.so


Install to target
-----------------
Establish adb connection with your target and run below commands:
::

    adb root
    adb remount
    adb push out/target/product/<your target>/system/bin/fio /system/bin/fio
    adb push out/target/product/<your target>/system/lib64/libaio.so /system/lib64/libaio.so

