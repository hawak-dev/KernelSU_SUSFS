<div align="center">

# GKI KernelSU SUSFS
### Automated Build Repository Tailored for ReSukiSU

**Automated GKI Kernel Build | Integrated ReSukiSU + SUSFS**

[![Release](https://img.shields.io/github/v/release/coolzyd9107/GKI_KernelSU_SUSFS?label=Release&style=flat-square&logo=github&logoColor=white&color=2ea44f)](https://github.com/coolzyd9107/GKI_KernelSU_SUSFS/releases)
[![Telegram](https://img.shields.io/static/v1?label=Telegram&message=Channel&color=0088cc)](https://t.me/ReSukiSUKernelBuilds)
[![ReSukiSU](https://img.shields.io/badge/ReSukiSU-Supported-5AA300?style=flat-square)](https://kernelsu.org/)
[![SUSFS](https://img.shields.io/badge/SUSFS-Integrated-E67E22?style=flat-square)](https://gitlab.com/simonpunk/susfs4ksu)

---

</div>

## ⚠️ Repository Guidelines

① This repository is forked from [zzh20188/GKI_KernelSU_SUSFS](https://github.com/zzh20188/GKI_KernelSU_SUSFS/). I have only made some modifications and bug fixes, so users should prioritize forking the original repository.

② This repository only supports building kernels with ReSukiSU. Support for other KernelSU branches has been completely removed. If you need to build kernels with other KernelSU branches, please fork the upstream repository [zzh20188/GKI_KernelSU_SUSFS](https://github.com/zzh20188/GKI_KernelSU_SUSFS/) and build it yourself.

## 💰 Special Thanks

[coolzyd9107](https://github.com/coolzyd9107): The creator and owner of this repository, but he is a big slacker/clumsy guy and doesn't know a lot of things.

[zzh20188](https://github.com/zzh20188): Author of the upstream repository of this project.

[*zhuzhuzihan*](https://github.com/zhuzhuzihan): Assisted with a lot of fixes and modifications, provided servers for our Telegram Bot (since the repository owner is too broke to afford one), and is the lead developer of our Telegram Bot.

[TanakaLun](https://github.com/TanakaLun): Assisted with a lot of fixes and modifications.

[YC-Chanluyancib](https://github.com/luyanci): Assisted with Telegram Bot development, provided suggestions for build workflow fixes and Bot design.

[AlexLiuDev233](https://github.com/AlexLiuDev233): Assisted in fixing issues with the build workflow.

[cctv18](https://github.com/cctv18): Assisted in fixing issues with the build workflow, provided ideas for adding 6.12 kernel build support and resolving some SUSFS-induced issues.

Note: Usernames with an asterisk (*) represent contributors whose GitHub accounts are currently set to private/invisible.

---

## ⚠️ Important Changelog

> **Note:** OnePlus ColorOS 14 & 15 are currently not supported; flashing may require a data wipe to boot successfully.

> **ReSukiSU:** ReSukiSU is updated more frequently than SukiSU. If SukiSU throws errors, try ReSukiSU.
>
> **Default variant has switched to ReSukiSU**

> **Android 16:** Already supported Android 16 - 6.12 kernel versions.
>
> **Since commit #c17aae5 of this repository, we have completely removed kernel build support for KernelSU variants other than ReSukiSU. If for some reason you prefer using managers of other KernelSU variants, do not worry: we have enabled multi-manager support (the KernelSU driver in the kernel remains ReSukiSU, but it supports being managed by managers of most other KernelSU variants, such as KowSU and SukiSU-Ultra managers). This allows you to directly use other variant managers, but please remember to use the ReSukiSU manager when submitting logs for bug reports.**

> **rekernel feature (Beta): already supported rekernel (currently in beta stage)**

---

## 🧪 Droidspaces Container Support (Experimental)

> **Experimental feature:** Successful build or boot is not guaranteed for all GKI versions. Please make sure to back up your Boot image before flashing.
>
> **TIPS:** The workflow uses [official patches](https://github.com/ravindu644/Droidspaces-OSS/tree/main/Documentation/resources/kernel-patches/GKI) from [Droidspaces](https://github.com/ravindu644/Droidspaces-OSS). Feel free to submit an issue if you have better patches. Additionally, since there are three different patches, you may need some trial and error to see which one works for your device; make your choice based on others' experience or your own.

[Droidspaces](https://github.com/ravindu644/Droidspaces-OSS) is a lightweight Linux container tool that runs a full Linux environment (supporting systemd, OpenRC, etc.) on Android, suitable for setting up development environments, running servers, etc.

**Supported versions:** 5.10 / 5.15 / 6.1 / 6.6 / 6.12

**Usage:** When triggering the build manually, select the `Droidspaces Container Support` option:

| Option | Description |
|:---:|:---|
| `off` | Disabled (default) |
| `678` | Use slot 6_7_8 patch (recommended) |
| `123` | Use slot 1_2_3 patch (alternative) |
| `345` | Use slot 3_4_5 patch (alternative) |

> **Tip:** The 6.12 kernel has only one patch; choosing any option other than off is sufficient.

**If the build fails or bootloops after flashing:** Try switching to another slot patch (e.g. 678 -> 123 or 345). Different kernel sublevels may require different patches.

---

## 🧪 Spoofing `/proc/config.gz` (Stock Config)

This is an advanced technique and does not require manual switching in the workflow.  
During the build, it will auto-detect whether `config/stock_defconfig` exists: it applies it if present, and skips if not.

Usage:
1. Ensure your device is running official ROM + official kernel.
2. Obtain `/proc/config.gz` from the device (either on-device or via PC).
3. Extract and rename it to `stock_defconfig`, upload to [`config/`](config/) directory of the repository, and commit (this can be done directly from a phone).

The build process will automatically:
- Copy to kernel source: `$KERNEL_ROOT/common/arch/arm64/configs/stock_defconfig`
- Replace `$(obj)/config_data` rule in `$KERNEL_ROOT/common/kernel/Makefile` from `$(KCONFIG_CONFIG)` to `arch/arm64/configs/stock_defconfig`
- Align the `/proc/config.gz` in the compilation output closer to your official kernel config

---

<div align="center">

**More content is continuously updated...**

⭐ If this project is helpful to you, please give us a Star!

⭐ For new pre-built release notifications and major change announcements, please follow our [Telegram Channel](https://t.me/ReSukiSUKernelBuilds)

</div>
