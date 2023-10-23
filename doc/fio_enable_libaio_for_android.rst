fio - How to build fio with libaio enabled for Android
======================================================


Download prebuilt binary
------------------------

You can download prebuilt binary for IA64 platform from: https://github.com/zhou-jingyu/fio4android/releases/download/enable_libaio_for_android/release.zip


Build from source code
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

The build output files to be used:
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


Verify libaio works on the target
---------------------------------
Establish adb connection with your target and run below commands under adb shell, and ``libaio`` should be listed in the ``Available IO engines``
::

    fio --enghelp
