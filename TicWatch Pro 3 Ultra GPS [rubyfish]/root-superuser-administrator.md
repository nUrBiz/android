# STEP BY STEP GUIDE TO GAIN ROOT(SU) PERMISSIONS [rubyfish]
note: from abstracts steps, guidelines can be emulate for other android devices.
Personally it took me total 1w, i'll comment below what i've been encountered, wait for the unexpected.(EE:🤫).
Be carefull, this procedure's gonna invalidate any material & non material warranty.

ETA:
- hardware components (it depends on personal skills)
- abstract (1h from first wipe to magisk superuser confirm)

PREP:
 - hardware: USB data cable
 - tools: android sdk platform-tool
 - unexpected
*********************************************************************************************************************************************************
*********************************************************************************************************************************************************
 
A) CABLE:
- data cable actung for the direction
- connected, start adb server //**if necessary re-de-attach power usb
- enable adbDebugging from developer options
- adb reboot fastboot
  
*********************************************************************************************************************************************************
 
B) UNLOCK BOOTLOADER:
bootloader menu:

.1 start (make default boot)
.2 restart bootloader (restart bootloader)
.3 recovery mode (at the moment the factory recovery mode)
.4 power off
.5 boot to ffbm (Factory Fastboot Bootloader Mode/Forced Fallback Boot Mode/Factory Boot Mode)*
.6 enter ship mode

- fastboot oem unlock
- after unlocking OEM, default wipe data
- need to reconnect to re-enable adb debug (with the current ROM)
 
*********************************************************************************************************************************************************
 
C) RECOVERY: (+ causes: wearOS 3.5, in my case downloaded stock fastboot 220703.001, it will restore recovery stock)
- adb reboot bootloader

.1 - if you encounter bootloader bootloop, you need to downgrade wearOS 3.5 (at the moment of this article 16.01.2025) installing fastboot stock
here A file resource: 

https://wear.onetm.ovh/en/OneOSWear/downloads/rubyfish/
NOTE: the team developer for the resource have made on the zip files the .bat and .sh precompiled automation

.2 instead you can run the follow for each .img file:
- fastboot flash ###.img

this guide is made thanks to the following resource/case studies:
https://xdaforums.com/t/rom-official-kali-nethunter-for-the-ticwatch-pro-3-wearos.4456797/page-8
from post Mar 9, 2024, to post Apr 24, 2024.
Monk987 (New member, bug reporter), feivel5 (Member), yesimxev (Senior Member, resourcer), steso90 (Senior Member, first bug resolver)

- fastboot flash recovery recovery.img (oneOS recovery)
- fastboot reboot recovery
- fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img
 
*********************************************************************************************************************************************************
 
D) ROM/CROM 
IF GIVE YOU ERROR TRY DOWNGRADE STOCK .img (see platform-tools dir files)(flash-all&images)
CROM
- adb sideload ###.zip / adb push ###.zip (CROM)
- adb sideload ###.zip / adb push ###.zip (addon ultra gps) 
MAGISK:
- adb sideload ###.zip / adb push ###.zip (magisk)
- adb push ###.zip (dm-verity install .zip from recovery)
- system rebooted
 
*********************************************************************************************************************************************************
 
E) MAGISK(SU)






![twp3 (13)](https://github.com/user-attachments/assets/eb3cfe49-d437-4fad-a746-4d93ddc98046)
![twp3 (12)](https://github.com/user-attachments/assets/fd07ab7e-0c88-4ed0-a32e-16fcbc934d40)
![twp3 (11)](https://github.com/user-attachments/assets/426125a6-f95d-4561-bbcf-d4871793aaaf)
![twp3 (10)](https://github.com/user-attachments/assets/0cc1b56d-c263-4a8f-97ff-3bb712c35c76)
![twp3 (9)](https://github.com/user-attachments/assets/444bf04d-d83d-4dab-a6ea-0dd3fb10cc5e)
![twp3 (8)](https://github.com/user-attachments/assets/0cba5f32-b22e-435f-bf32-fcbbd5a8724b)
![twp3 (7)](https://github.com/user-attachments/assets/4d7af7c4-0108-402f-a136-740f3da73d5e)
![twp3 (6)](https://github.com/user-attachments/assets/50ad2891-3019-4f29-868f-2c0a174bee2f)
![twp3 (5)](https://github.com/user-attachments/assets/a24ed931-d525-4783-abc2-eee1304fdf6f)
![twp3 (4)](https://github.com/user-attachments/assets/03a955b7-4362-4f69-ab71-73bed7791d7e)
![twp3 (3)](https://github.com/user-attachments/assets/9bc05ae5-76a9-4414-a85b-b6c740f240e4)
![twp3 (2)](https://github.com/user-attachments/assets/37bd1d54-f4e3-41f4-96fb-b6351d505862)


https://github.com/user-attachments/assets/63e82190-e9f9-4cc1-bbc7-8e75ae1798fb

![twp3 (1)](https://github.com/user-attachments/assets/dadbfacd-c3f9-4775-8a32-82fdfece5aa7)




links/resource:
XDA WearOS: https://xdaforums.com/c/wear-os-development-and-hacking.2983/
WearOS one: https://wear.onetm.ovh/en/
Net Hunter: https://www.kali.org/docs/nethunter/installing-nethunter-on-the-ticwatch-pro-3/#supported-features

NOTES:
(days: 2.5 + 2 + 2)
+14012025 (start)
+16012025 (wearOS bug fix)
+18012025.1559-21012025.03.20(bootloop, stock fastboot)
+21012025.0758(flash rom fastboot stock as needed for bricked bootloop than restored factory from recovery stock)

+0800 flashed recovery
+0802 vbmeta

+1212 wiped all for a clean install

+1217 sideload crom pushed (2023)
+1219 addon (oem)
**wiped cache and dalvik every sideload

+ reboot
+ init (24 colored round to complete!!)

+ re-enable adb debug
+ adb install magisk.apk    NOT .zip because no ramdisk
+ 1554 from selecting file img magisk app select boot.img pushed from crom.zip
+ 1554 patch boot.img
+ pull patched .img from sdcard/Download/magisk_patched_[random_strings].img to pc
+ fastboot flash boot magisk_patched_[random_strings].img
+ disable dm verity (tryed without with success for me)
+ reboot
+ ok rooted 1608

