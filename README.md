# Kernel build for redbull
## Version
### Kernel
- [KernelSU: v0.9.5](https://github.com/tiann/KernelSU/releases/tag/v0.9.5)
- [KernelSU-Next: v1.1.1](https://github.com/KernelSU-Next/KernelSU-Next/releases/tag/v1.1.1)
- [SusFS: v1.5.5, branch kernel-4.19](https://gitlab.com/simonpunk/susfs4ksu/-/tree/kernel-4.19)
### Modules
- [ReZysk-v1.0.0-rc.5](https://github.com/PerformanC/ReZygisk/releases/tag/v1.0.0-rc.5)
- [LSPosed v1.11.0](https://github.com/JingMatrix/LSPosed/releases/tag/v1.11.0)
- [PlayIntegrityFix inject-s v4.4](https://github.com/KOWX712/PlayIntegrityFix/releases/tag/v4.4-inject-s)
- [TrickyStore v1.4.1](https://github.com/5ec1cff/TrickyStore/releases/tag/1.4.1)
- [Tricky Addon Module v4.3](https://github.com/KOWX712/Tricky-Addon-Update-Target-List/releases/tag/v4.3)
- [Yurikey Manager v2.52](https://github.com/Yurii0307/yurikey/releases/tag/v2.52)
- *[LimitlessPhotos v1.1.1](https://github.com/daglaroglou/LimitlessPhotos/releases/tag/1.1.1) - Unlimited photos for Google Photos
- *[Simple-Flag-Secure v5](https://github.com/ShivamXD6/Simple-Flag-Secure/releases/tag/v5)

**Modules with * are optional for me, do not need to root bypass.**
### App
- [SPIC: v1.4.0](https://github.com/herzhenr/spic-android/releases/download/v1.4.0)
- [Native Detector: v7.6.1](https://github.com/reveny/Android-Native-Root-Detector/releases/tag/v7.6.1)
- [HMA-OSS: oss-158](https://github.com/frknkrc44/HMA-OSS/releases/tag/oss-158)


## Checked
- Pixel 5 (redfin)
  - [x] android-msm-redbull-4.19-android14 - no susfs - kernelSU
  - [x] android-msm-redbull-4.19-android14 - yes susfs - kernelSU
  - [ ] android-msm-redbull-4.19-android14 - non susfs - kernelSU-Next
  - [x] android-msm-redbull-4.19-android14 - yes susfs - kernelSU-Next
  - [ ] android-msm-redbull-4.19-android14 - non susfs - SukiSU => Not support
  - [ ] android-msm-redbull-4.19-android14 - yes susfs - SukiSU

## How to flash
```bash
fastboot flash boot boot.img
fastboot flash dtbo dtbo.img
fastboot flash vendor_boot vendor_boot.img
```