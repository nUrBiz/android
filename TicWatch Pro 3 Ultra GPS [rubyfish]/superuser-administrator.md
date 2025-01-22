dir: C:\Users\nicco\AppData\Local\Android\Sdk\platform-tools

wearOS one: https://wear.onetm.ovh/en/

NH: https://www.kali.org/docs/nethunter/installing-nethunter-on-the-ticwatch-pro-3/#supported-features

NOTES:
rubyfish ticwatch pro 3 ultra gps (days: 2.5 + 2 + 2)
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

////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
crom installing step by step:
 - preparation
 - tools
 + case study (wearOS 3.5)
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
CABLE:
- data cable actung for the direction
- connected, start adb server //**if necessary re-de-attach power usb
- enable adbDebugging from developer options
- adb reboot fastboot
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
UNLOCK BOOTLOADER:
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
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
RECOVERY: (+ causes: wearOS 3.5, in my case downloaded stock fastboot 220703.001, it will restore recovery stock)
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
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
IF GIVE YOU ERROR TRY DOWNGRADE STOCK .img (see platform-tools dir files)(flash-all&images)
CROM
- adb sideload ###.zip / adb push ###.zip (CROM)
- adb sideload ###.zip / adb push ###.zip (addon ultra gps) 
MAGISK:
- adb sideload ###.zip / adb push ###.zip (magisk)
- adb push ###.zip (dm-verity install .zip from recovery)
- system rebooted




********************************************************************************************************************************************************************************3. Finalise Magisk app to finish the rooting process

    Enable ADB again
    Finalise Magisk installation with app install adb install Magisk-v24.3.apk
    Launch Magisk Manager
    You may want to disable auto-update, set grant access in auto response, and disable toast notifications for easier navigation in the future

4. Install NetHunter

    Reboot to recovery
    Select Install -> ADB Sideload
    Flash NetHunter image with adb sideload
    Reboot
    Start NetHunter app & chroot
    Reboot

5. Set NetHunter watch face

    Install Facer onto your phone and watch from Play Store
    Search for NetHunter
    Select & Sync
    Set density so NetHunter app menu buttons will be reachable on OneOS 
    - adb shell wm density 300

Enjoy Kali NetHunter on the TicWatch Pro 3





