### Update 08/15/2020
- Switch back to VoodooI2CSynaptics.kext
  - No more VoodooRMI.kext


### Update 08/09/2020
- Confirmed working on MacOS 11.0 Big Sur Public Beta
- Config updated
  - No longer maintaining multiple configs
- VoodooPS2Controller.kext updated
  - Most top row keys are now mapped through the kext
  - Keyboard backlight now controlled with left ctrl + alt + "comma" and "period" keys
  - Karabiner no longer required!
- Some clean up/restructuring of readme.md

### 08/05/2020
- Switched away from using a modified DSDT for keyboard backlight control
  - Now using SSDT-KBBL.aml

### 08/04/2020
- Updated config.plist for OpenCore 0.6.0
- Switched to VoodooRMI.kext for trackpad kext
  - No longer using the modified VoodooI2CSynaptics.kext

### 07/29/2020
- Confirmed working on MacOS 10.15.6
  - Updated through System Preferences - no changes necessary

### 07/04/2020
- Fixed poor headphone audio
  - Changed boot-args entry from **alcid=3** to **alcid=15**


### 07/02/2020
- Fixed the weird click/highlight stick after sleep
  - New modified VoodooI2CSynaptics.kext included in VoodooI2C-CB13.zip
- Fixed lid wake
  - Added **darkwake=1** to boot-args
