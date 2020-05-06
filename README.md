
#nAOSP 7.1.2 for Asus Nexus 7 2012 - Grouper, Tilapia

near AOSP ROM 7.1.2

## Download Source

```
repo init -u https://github.com/millosr/naosp_manifest -b nAOSP-7.1.2-grouper
mkdir .repo/local_manifests/
ln -s ../manifests/local_manifest.xml .repo/local_manifests/local_manifest.xml
repo sync -j16
```

## Apply patches

Apply all patches from device/asus/grouper/patch

```
cd bionic
patch -p1 < ../device/asus/grouper/patch/bionic.patch
cd ../frameworks/native
patch -p1 < ../../device/asus/grouper/patch/frameworks_native.patch
cd ../../system/netd
patch -p1 < ../../device/asus/grouper/patch/system_netd.patch
cd ../../packages/apps/Jelly
patch -p1 < ../../../device/asus/grouper/patch/packages_apps_Jelly.patch
cd ../../..
```

## Build

```
source build/envsetup.sh

export ROM_BUILD_NUM=xx

lunch
<choose grouper or tilapia>

make otapackage -j4    (-j<number of threads>)
```

