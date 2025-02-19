# MiTAC_AMD-genoa-coreboot-helper

1. This is source code setup repository for MiTAC S8050 of Genoa/OpenSIL/coreboot.
2. Supported platform:
   - MiTAC_Tyan S8050GM4NE-2T (https://www.mitaccomputing.com/Motherboards_S8050_S8050GM4NE-2T_EN~Spec)
   - Capri2 (https://www.mitaccomputing.com/OCPserver_CP2S11_CP2S11-U_EN~description#ov)
   - MiTAC_Tyan B8261T85E24HR-2T (https://www.mitaccomputing.com/Barebones_TN85B8261_B8261T85E24HR-2T_EN~description) 


## Clone Repositories

1. Execute init.sh to clone source codes and apply patches
2. The repositories and folder structure will be:
  - coreboot (Tag: 24.08)
  - Patches


## Build and Deploy

1. cd coreboot
2. Execute "make crossgcc-x64 -j 4 CPUS=4" to compile related utilities
3. Execute "make defconfig" to configure platform settings
  - For S8050: make defconfig KBUILD_DEFCONFIG=configs/config.mitac_s8050
  - For Capri2: make defconfig KBUILD_DEFCONFIG=configs/config.mitac_capri2.prebuild_kernel
  - For B8261: make defconfig KBUILD_DEFCONFIG=configs/config.mitac_s8261
5. Execute "make" to build coreboot
6. Deploy build/coreboot.rom to 32MB SPI flash of platforms


## Progress

- With these repositories, MiTAC platforms + Genoa can boot to OS(Ubuntu) successfully
- Support USB and NVME devices
- Debug messages are available through BMC SOL


## Existing Known Issues or Limitation
- VGA in OS is not fully functioning
- eSPI configurations in device tree are disabled
