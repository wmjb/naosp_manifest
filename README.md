
#nAOSP 7.0 for Asus Nexus 7 2012 - Grouper, Tilapia

near AOSP ROM 7.0

##Build

```
repo init -u https://github.com/millosr/naosp_manifest -b nAOSP-7.0-grouper
mkdir .repo/local_manifests/
ln -s ../manifests/local_manifest.xml .repo/local_manifests/local_manifest.xml
repo sync

source build/envsetup.sh

export ROM_BUILD_NUM=xx

lunch
<choose grouper or tilapia>

make otapackage -j4    (-j<number of threads>)
```

##Jack Xmx issue

```
out/host/linux-x86/bin/jack-admin stop-server
export JACK_SERVER_VM_ARGUMENTS="-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4096m"
out/host/linux-x86/bin/jack-admin start-server

make otapackage
```
