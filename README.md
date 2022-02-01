TWRP device tree for Lenovo Z5 Pro GT

The Lenovo Z5 Pro GT (codenamed _"heart"_) is a high-end smartphone from Lenovo.
Lenovo Z5 Pro GT was announced in December 2018 and released in January 2019.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
SoC     | Qualcomm SM8150 Snapdragon 855
CPU     | Octa-core (1x2.84 GHz Kryo 485 Gold & 3x2.42 GHz Kryo 485 Gold & 4x1.78 GHz Kryo 485 Silver)
GPU     | Adreno 640
Memory  | 6GB / 8GB / 12GB RAM (LPDDR4X)
Shipped Android Version | 9.0 with ZUI 10
Storage | 128/256/512 GB UFS2.1
Battery | Non-removable Li-Po 3350 mAh
Display | 1080 x 2340 pixels, 19.5:9 ratio, 162.31 mm (6.39 in), Super AMOLED, HDR10 (~403 ppi density)
Height | 155.1 mm (6.11 in)
Width | 73 mm (2.87 in)
Diameter | 9.3 mm (0.37 in) 
Weight | 210 g (7.41 oz)
Build | Glass front, glass back, aluminum frame
SIM | Hybrid Dual SIM (Nano-SIM, dual stand-by, dual Volte)
Rear Camera 1 (Sony IMX576) | 24.8MP, f/1.8, 1/2.8 sensor size, PDAF, 0.9µm pixel native / 1.8µm pixels in 6.2MP pixel binning, dual-LED (dual tone) flash
Rear Camera 2 (Sony IMX519) | 16MP, f/1.8, 1/2.8 sensor size, 1.22 µm pixel size, PDAF, dual-LED (dual tone) flash
Front Camera 1 (Samsung S5K3P9SX) | 16MP, f/2.2, 1/3.1 sensor size, 1.0µm pixel size
Front Camera 2 (Omnivision S5KGD1) | 8MP, f/2.2, infrared camera

## Device picture

![Lenovo Z5 Pro GT](https://i.imgur.com/gtyGruZ.jpg)

## Features

Works:

- ADB
- Decryption of /data
- Screen brightness settings
- Correct screenshot color
- MTP
- Flashing (opengapps, roms, images and so on)
- Backup/Restore (Needs more testing)
- USB OTG
- Vibration support

## Compile

First checkout minimal twrp with omnirom tree:

```
mkdir -p ~/android/twrp-11
cd ~/android/twrp-11
repo init -u git@github.com:minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-11
repo sync
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/lenovo/heart" name="TeamWin/android_device_lenovo_heart" remote="github" revision="android-11" />
```

You need also of this commit in /build:

```
https://gerrit.omnirom.org/#/c/android_build/+/36483/
```


Finally execute these:

```
. build/envsetup.sh
export ALLOW_MISSING_DEPENDENCIES=true
export LC_ALL=C
lunch twrp_heart-eng
make recoveryimage
```

To test it:

```
fastboot boot out/target/product/heart/recovery.img
```

## Other Sources

Kernel source: https://github.com/lenovo-sm8150/android_kernel_lenovo_sm8150/tree/twrp-11

## Thanks

Thanks to @Lucchetto for the kernel
