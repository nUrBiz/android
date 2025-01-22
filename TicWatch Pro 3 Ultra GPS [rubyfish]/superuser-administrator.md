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






![PXL_20250121_154055926](https://github.com/user-attachments/assets/2aee5818-33f2-4606-9a28-caae75b0f2e1)
![PXL_20250121_154036372](https://github.com/user-attachments/assets/d91be73d-911f-45dd-82e2-7eb182e929b4)
![PXL_20250121_154031358](https://github.com/user-attachments/assets/a5c16caf-9a7b-439f-b62e-cc344e42470c)
![PXL_20250121_153950845](https://github.com/user-attachments/assets/91c6c683-fc2d-4bdb-8a3b-d131cd066ee2)
![PXL_20250121_153939092](https://github.com/user-attachments/assets/9e4ab3fc-2072-447c-bb9b-996b27361020)


https://github.com/user-attachments/assets/d172aa0e-ed68-4f19-9997-0dedeb4bb85f

![PXL_20250115_161412223](https://github.com/user-attachments/assets/55f6bb4d-7241-481c-b948-161848d2c188)
![PXL_20250115_161054261](https://github.com/user-attachments/assets/b92de2b7-f557-4081-8712-0a59411d61ff)
![PXL_20250115_161044194](https://github.com/user-attachments/assets/dd9dbf1b-30cc-4627-b95c-a5486edd7130)
![PXL_20250115_161019334](https://github.com/user-attachments/assets/42e112c6-e2d6-4987-bb66-fea7ea6d65d5)
![PXL_20250115_112554029](https://github.com/user-attachments/assets/be1a98eb-7ea3-4802-9899-51c8ee4e6379)
![PXL_20250115_103915535](https://github.com/user-attachments/assets/4d4bbb0b-ac0f-435d-b0c4-7409ca8add2b)
![PXL_20250115_103633671](https://github.com/user-attachments/assets/45019451-7a33-489a-9b81-25fb2fe11bda)
![PXL_20250115_103614123](https://github.com/user-attachments/assets/8b4baa54-b7f9-4e20-8448-68d991d69554)
