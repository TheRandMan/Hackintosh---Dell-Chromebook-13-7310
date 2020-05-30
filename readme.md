# Dell Chromebook 13 7310 Hackintosh
### Now using OpenCore! 

This is NOT meant to be a guide or walkthrough but merely a dump of files and notes to get MacOS working on a Dell Chromebook 13. I will try to keep this updated as I update my Chromebook to future MacOS releases.

Confirmed working on MacOS 10.15.5
#
### Basic steps:
 - Install MrChromebox custom [UEFI firmware](https://mrchromebox.tech/#fwscript)
 - Create MacOS installer flashdrive with OpenCore bootloader
 - Download SSDTs, kexts, and config.plist from this repo
 - Generate SMBIOS and add it to the config.plist
 - Place the SSDTs, kexts, and config.plist in appropriate locations in your EFI partition
 - Install MacOS
 - Install OpenCore to internal SSD
 - Disable force click in trackpad settings
 - Install [Karabiner](https://karabiner-elements.pqrs.org) to map top row keyboard shortcuts
 - Disable hibernate with "sudo pmset -a hibernatemode 0"
 - Install LogoutHook.command according to directions in Utilities folder of the OpenCore download

If you want a full guide, use this: https://dortania.github.io/vanilla-laptop-guide/
All of the SSDTs and the config file were created through this guide.


# Requirements
  - Core i3 or Core i5 Processor 
    - Will NOT work with the Celeron model
  - Minimum of a 32GB SSD
    - Minimum 64GB recommended
  - A compatible WiFi card
    - The Dell DW1560 works in MacOS, Windows & Ubuntu
  - MacOS installer flash drive 
    - There are plenty of guides on how to make this so that won't be covered here

## Notes
  - This is all made for [OpenCore](https://github.com/acidanthera/OpenCorePkg/releases) 0.5.8
    - Clover is no longer used here but old Clover data can be found in the Clover branch.
  - You will need to generate your own SMBIOS for the attached config.plist - Use the MacBook Air 7,2 profile 
    - Use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to do this
  - The SSDTs are made from version 4.11.2 MrChromebox's firmware (other versions may work but YMMV)

## What's Working: 
  - Just about everything!
  
## What's Not Working:
  - Touchscreen - unlikely to be fixed
  - Keyboard backlight control - also turns off after closing the lid
  - Occasional trackpad click stick after waking from sleep
    - Possibly fixed with latest custom [VoodooI2C.kext](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/raw/master/VoodooI2C-CB13.zip)

## To Do:  
  - Keyboard backlight control   

## OpenCore Config
  - [config.plist](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/raw/master/config.plist)
    - You will need to generate your own SMBIOS section with GenSMBIOS - use a Macbook Air 7,2 profile.

## Full list of DSDT / SSDT files
Placed in EFI/EFI/OC/ACPI
- [SSDT-EC.aml](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/raw/master/SSDT-EC.aml)
  - Exposes the embedded controller to MacOS
- [SSDT-PLNF.aml](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/raw/OpenCore/SSDT-PNLF.aml)
  - Enables LCD backlight control
- [SSDT-PLUG](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/blob/master/SSDT-PLUG.aml?raw=true)
  - Enables proper CPU power management
- [SSDT-USB.aml](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/raw/OpenCore/SSDT-USB.aml)
  - Properly maps USB ports, Micro SD card reader, webcam, and bluetooth
- [SSDT-SBUS-MCHC.aml](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/raw/OpenCore/SSDT-SBUS-MCHC.aml)
- [SSDT-HPET.aml](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/raw/OpenCore/SSDT-HPET.aml)

  
## List of Required Kexts
Placed in EFI/EFI/OC/Kexts
- [AppleALC.kext](https://github.com/acidanthera/applealc/releases)
- [Lilu.kext](https://github.com/acidanthera/lilu/releases)
- [WhateverGreen.kext](https://github.com/acidanthera/whatevergreen/releases)
- [VirtualSMC.kext](https://github.com/acidanthera/virtualsmc/releases)
  - SMCBatteryManager.kext
  - SMCProcessor.kext
  - SMCSuperIO.kext
- [VoodooI2C.kext](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/raw/master/VoodooI2C-CB13.zip) 
  - VoodooI2CSynaptics.kext
  - This is a modified VoodooI2C.kext for appropriate Trackpad sensitivity
- [VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2/releases)
- [CPUFriend.kext](https://github.com/acidanthera/CPUFriend/releases)
- [CPUFriendDataProvider.kext](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/raw/master/CPUFriendDataProvider.kext.zip)

## Kexts for Dell DW1560 wifi
Placed in EFI/EFI/OC/Kexts 
 - [AirportBrcmFixup.kext](https://github.com/acidanthera/airportbrcmfixup/releases)
 - [BrcmPatchRAM3.kext](https://github.com/acidanthera/BrcmPatchRAM/releases)  
  - BrcmBluetoothInjector.kext
  - BrcmFirmwareData.kext
 

### Post-Install
- Setup LogoutHook.command following the directions found in the Utilities folder of the OpenCore download
- Disable force click in trackpad settings
- Install [Karabiner](https://karabiner-elements.pqrs.org) to map top row keyboard shortcuts
- Disable hibernate with "sudo pmset -a hibernatemode 0"

#
#
# 
#
# What does what?
### Keyboard
- Voodoops2Controller.kext
  - https://github.com/acidanthera/VoodooPS2/releases
- Top row keyboard shortcuts with Karabiner-Elements
  - https://karabiner-elements.pqrs.org

### Trackpad
- [VoodooI2C.kext](https://github.com/TheRandMan/Hackintosh---Dell-Chromebook-13-7310/raw/master/VoodooI2C-CB13.zip)
  - VoodooI2CSynaptics.kext (Included with the above download)
  - This is a custom version, modified for appropriate trackpad sensitivity

### Sound
- AppleALC.kext
  - https://github.com/acidanthera/applealc/releases
- Audio layout 3 (already in config.plist)

### LCD Backlight Control
- SSDT-PNLF.aml
  - https://bitbucket.org/RehabMan/applebacklightfixup/downloads/

### WiFi
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
- https://www.tonymacx86.com/
- https://reddit.com/r/hackintosh
- https://github.com/corpnewt/CPUFriendFriend
- https://github.com/TheRandMan/VoodooI2C
- https://dortania.github.io/vanilla-laptop-guide/
