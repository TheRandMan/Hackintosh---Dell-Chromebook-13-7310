# Dell Chromebook 13 7310 Hackintosh

This is NOT meant to be a guide or walkthrough but merely a dump of files and notes to get MacOS working on a Dell Chromebook 13. I will try to keep this updated as I update my Chromebook to future MacOS releases


# Requirements
  - Core i3 or Core i5 Processor 
    - Will NOT work with the Celeron model
  - Minimum of a 32GB SSD
    - Minimum 64GB recommended
  - A compatible WiFi card
    - If you're planning on booting an additional OS I recommend a Dell DW1560 - for other compatible cards, do your own research
  - MacOS installer flash drive 
    - There are plenty of guides on how to make this so that won't be covered here
  - USB mouse (the built in touchpad will not work in the installer)

## Notes
  - You will need to generate your own SMBIOS in the attached config.plist - Use the MacBook Air 7,2 profile 
    - Use [Clover Configurator](https://github.com/CloverHackyColor/CloverBootloader/releases) to do this
  - The DSDT is for MrChromebox's firmware version 4.11.2 (other versions may work but YMMV)

## Clover Installation Options
![image](https://github.com/TheRandMan/Dell-Chromebook-13-7310-Hackintosh/raw/master/Clover_Setup.jpg)

## Clover Config
  - [config.plist](https://github.com/TheRandMan/Dell-Chromebook-13-7310-Hackintosh/raw/master/config.plist)
    - You will need to generate your own SMBIOS section - use the Macbook Air 7,2 profile

## Full list of DSDT / SSDT files
- [DSDT.aml](https://github.com/TheRandMan/Dell-Chromebook-13-7310-Hackintosh/raw/master/DSDT.aml)
- SSDT-PLNF.aml
  - https://bitbucket.org/RehabMan/applebacklightfixup/downloads/

## List of Required Kexts
### Installed from Clover Configurator
- AirportBrcmFixup.kext
- SMCLightSensor.kext
- VirtualSMC.kext
- AppleALC.kext
- SMCProcessor.kext
- WhateverGreen.kext
- Lilu.kext
- SMCSuperIO.kext
- SMCBatteryManager.kext
- USBInjectAll.kext

### Installed from elsewhere:
- VoodooI2C.kext
- VoodooI2CSynaptics.kext
  - https://github.com/alexandred/VoodooI2C/releases
- VoodooPS2Controller.kext
  - https://github.com/acidanthera/VoodooPS2/releases
- BrcmBluetoothInjector.kext
- BrcmFirmwareData.kext
- BrcmPatchRAM3.kext
  - https://github.com/acidanthera/BrcmPatchRAM/releases
#
#
# 
#
# What does what?
## Keyboard
- Voodoops2Controller.kext
  - https://github.com/acidanthera/VoodooPS2/releases

## Touchpad
- VoodooI2C.kext
- VoodooI2CSynaptics.kext 
  - https://github.com/alexandred/VoodooI2C/releases
- The required "Windows" edits are applied to the dsdt.aml in this repo

## Sound
- AppleALC.kext
  - https://github.com/acidanthera/applealc/releases
- Audio layout 3

## LCD Backlight Control
- SSDT-PNLF.aml
  - https://bitbucket.org/RehabMan/applebacklightfixup/downloads/

## WiFi
You need swap in a compatible WiFi card - I'll be using a Dell DW1560 so the following kexts are required
- AirportBrcmFixup.kext
- BrcmBluetoothInjector.kext
- BrcmFirmwareData.kext
- BrcmPatchRAM3.kext
  - https://github.com/acidanthera/BrcmPatchRAM/releases
  - https://github.com/acidanthera/AirportBrcmFixup/releases
#
#
#
#
## Credits & Sources (in no particular order and maybe missing some)
- https://github.com/acidanthera/
- https://github.com/alexandred/
- https://github.com/MrChromebox/
- https://github.com/RehabMan
- https://www.insanelymac.com/
- https://reddit.com/r/hackintosh
- https://tonymacx86.com/
- https://www.tonymacx86.com/threads/guide-intel-broadwell-nuc5-using-clover-uefi-nuc5i5mhye-nuc5i3myhe-etc.261712/
