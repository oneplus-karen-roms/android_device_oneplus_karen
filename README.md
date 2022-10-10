Device tree for the OnePlus Nord 2T 5G (karen)
=================================================

| Basic                   | Spec Sheet                                                                                                                     |
| -----------------------:|:------------------------------------------------------------------------------------------------------------------------------ |
| Codename                | `karen`                                                                                                                        |
| Device name             | `OP557AL1` (OnePlus Nord 2T 5G)                                                                                                |
| Model names             | `CPH2399` "EU" global model<br/>`CPH2401` India model                                                                          |
| CPU                     | Octa-core                                                                                                                      |
| Chipset                 | MediaTek MT6893 Dimensity 1300 5G (6 nm) (MT6893Z_Z/CZA)                                                                       |
| GPU                     | Mali-G77 MC9                                                                                                                   |
| Memory                  | 8/12 GB RAM                                                                                                                    |
| Shipped Android Version | Android 12.1 (OxygenOS 12.1)                                                                                                   |
| Storage                 | 128/256 GB                                                                                                                     |
| Battery                 | Li-Po 4500 mAh, non-removable                                                                                                  |
| Display                 | AMOLED, 90Hz, HDR10+ 1080 x 2400 pixels, 20:9 ratio (~409 ppi density)                                                         |
| Camera (Back)(Main)     | 50 MP, f/1.8, 24mm (wide), 1/1.56", 1.0µm, PDAF, OIS<br/>8 MP, f/2.2, 120˚ (ultrawide)<br/>2 MP, f/2.2, (monochrome)           |
| Camera (Front)          | 32 MP, f/2.4, (wide), 1/2.8", 0.8µm                                                                                            |

![image](https://fdn2.gsmarena.com/vv/pics/oneplus/oneplus-nord-2t-5g-1.jpg)

## Building

First init LineageOS.

```
repo init -u https://github.com/LineageOS/android.git -b lineage-19.1
```

Add the file `.repo/local_manifests/local_manifest.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <!-- Device Tree -->
  <project path="device/oneplus/karen" name="oneplus-karen-roms/android_device_oneplus_karen.git" remote="github" revision="lineage-19.1" />

  <!-- Kernel -->
  <project path="kernel/oneplus/karen" name="oneplus-karen-roms/android_kernel_oneplus_mt6893.git" remote="github" revision="patched-12.1-karen" />

  <!-- Vendor modules -->
  <project path="kernel/oneplus" name="oneplus-karen-roms/android_vendor_mediatek_kernel_modules_mt6893.git" remote="github" revision="patched-12.1-karen" />
</manifest>
```

And then... <sub>see you 160GiB later!</sub>
```
repo sync -j5 --current-branch --no-clone-bundle --no-tags
```

Welcome back. Still OK? Good, now you can build.
```
source build/envsetup.sh; breakfast karen
croot && brunch karen
```
