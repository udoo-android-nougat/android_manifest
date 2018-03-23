#### __Download source:__

```
$ mkdir mydroid
$ cd mydroid
$ repo init -u https://github.com/udoo-android-nougat/android_manifest.git -b android-7.1
$ repo sync --no-tags --no-clone-bundle
```

#### __Set up ccache:__

```
$ export USE_CCACHE=1
$ export CCACHE_DIR=/path/to/ccache_cache/.ccache
$ prebuilts/misc/linux-x86/ccache/ccache -M 50G
```

#### __Select your target device:__

```
$ source build/envsetup.sh
$ lunch
```

#### __Compile Android image:__

```
$ make -jxx
```
+ Replace *xx* with number of cores of your CPU.

#### __Write Android image to MicroSD:__

1. Copy *device/udoo/common/tools/write_sdcard_ext4.sh* to out/target/product/udoo_*xxx*
   + Replace *xxx* with the name of target device.
2. Write the MicroSD with:
   ```
   $ sudo ./write_sdcard_ext4.sh -f soc_name /dev/sdX
   ```
   + Replace *soc_name* with *imx6q* for UDOO Dual/Quad or *imx6sx* for UDOO Neo
   + Replace *dev/sdX* with the correct device letter.
