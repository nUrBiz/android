# STEP BY STEP GUIDE TO GAIN ROOT(SU) PERMISSIONS [rubyfish]
NOTE: from abstracts steps, guidelines can be emulated for other android devices.
 Personally it took me total 1w, i'll comment below what i've been encountered, wait for the unexpected. (EE:🤫).
 Be carefull, this procedure's gonna invalidate any material & non material warranty.
 
ETA:
 
- hardware components (it depends on personal skills)
- abstract (1h from first wipe to magisk superuser confirm)
 
PREP:
 
 - hardware: USB data cable
 - tools: android sdk platform-tool (adb, fastboot, RSA key finger-print dir: $user/.android/adbkey && $user/.android/adbkey.pub)
 - data resources: GOTO @end of this file
 - unexpected
*********************************************************************************************************************************************************
*********************************************************************************************************************************************************
********************************************************************************************************************************************************* 
A) CABLE:
 
- data cable actung for the direction of v++ & v--
- enable adb debugging from watch developer options
- when connected, start adb server on host (if necessary re-de-attach power usb if not detected)
```
adb start-server
```
- on watch allow always for the MAC address of the host for future handshake (compare for thriftiness the RSA finger-print)
- reboot on bootloader
```
adb reboot fastboot
```
 
*********************************************************************************************************************************************************
 
B) UNLOCK BOOTLOADER:
 
bootloader menu GUI:
.1 start (make default boot)
.2 restart bootloader (restart bootloader)
.3 recovery mode (at the moment the factory recovery mode)
.4 power off
.5 boot to ffbm (Factory Fastboot Bootloader Mode/Forced Fallback Boot Mode/Factory Boot Mode)*
.6 enter ship mode
 
exec the following:
- on host:
```
fastboot oem unlock
```
- after unlocking OEM, continue wiping data on watch to factory default OR skip ROM installation GOTO E).
- need to re init and to re-enable adb debug GOTO A.
 
*********************************************************************************************************************************************************
 
C) INSTALL RECOVERY: (utility ROM necessary to proceed, some function ex: file explorer, adb connection, .zip installer, partition mounter, etc.)
(NOTE: if unexpected encountered GOTO: C.1 and WearOS by One exclusively compiled ROM<->DEVICE)
 
- reach bootloader holding phisical buttons: Power + Multi-function, than release the power after vibrate
  OR
- reach bootloader from OS initialized
```
adb reboot bootloader
```
 
- secure to handshake host-device than flash recovery from bootloader/fastboot:
```
fastboot flash recovery recovery.img
```
- flash vbmeta: (to make persistent recovery and next mod, necessary to continue)
```
fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img
```
- reboot in recovery:
```
fastboot reboot recovery
```
- if succeed GOTO D).
 
C.1 
 UNEXPECTED: Wear OS 3.5 [last OTA update]
 CAUSED: bootloader bootloop
 FIX: needed to downgrade firmware flashing all .img.
 
-you need to downgrade Wear OS 3.5 (at the moment of this article is the last OTA update) installing fastboot OR recovery stock firmware.
 DIFFERENCE:
 recovery stock: can be restored from custom recovery
 fastboot stock: can be restored from fastboot/bootloader
 
here A direct resource:
 https://wear.onetm.ovh/en/OneOSWear/downloads/rubyfish/
 
NOTE: the developer team have made on the fastboot stock zip file the .bat and .sh precompiled scripts otherwise you can run the follow for each .img file:
```
fastboot flash ####.img
```
 
*********************************************************************************************************************************************************
 
D) INSTALL ROM/CROM & other AddOn: (AddOn ex.: Gapps[google apk & service])
 there are two methods to flash .zip:
  
D.1 directly from host by sideloading:
- from recovery select install-sideloadADB:
```
 adb sideload ####.zip
```

OR

D.2 locally on device trough recovery, push the desired file to device trough:
```
adb push ###.zip
```
- than on recovery select install from zip
 
- reboot after install:
```
adb reboot
```
(NOTE: it's not necessary to wipe cache and Dalvik for every flash but it's a good practice)

NOW YOU HAVE A FRESH ROM INSTALLED, YOU CAN CONTINUE TO GAIN SPECIAL PERMISSION.
 
*********************************************************************************************************************************************************
 
E) MAGISK(SU)
NOTE: next is one of the various method to gain SU, it's differ for devices.

- we need first to access the boot.img of the installed ROM, usually it's inside the ROM .zip file, otherwise with a different direction of evolution we can extract it directly from the device trough the next:
```
adb shell
```
```
dd if=/dev/block/bootdevice/by-name/boot of=/sdcard/boot.img
```
it will extract it to dir /sdcard/

- install magisk apk trough adb:
```
adb install magisk.apk
```

- from magisk APP move forward patching the boot.img extracted, locate the patched boot and move it to the host.
- reboot to fastboot
- flash the patched .img trough:
```
fastboot flash boot magisk_patched_[random_strings].img
```
-than reboot

*********************************************************************************************************************************************************

F) FINALLY YOU'VE GAINED ROOT(SU) to your android device, enjoy 🥳.

*********************************************************************************************************************************************************
*********************************************************************************************************************************************************
*********************************************************************************************************************************************************
*********************************************************************************************************************************************************
*********************************************************************************************************************************************************
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




 LINKS / RESOURCE:
List of Wear OS devices: https://en.wikipedia.org/wiki/List_of_Wear_OS_devices
XDA WearOS: https://xdaforums.com/c/wear-os-development-and-hacking.2983/
Magisk: https://github.com/topjohnwu/Magisk
WearOS one: https://wear.onetm.ovh/en/
Net Hunter: https://www.kali.org/docs/nethunter/installing-nethunter-on-the-ticwatch-pro-3/#supported-features

 CREDITS:
this guide is made thanks to the following:
 https://xdaforums.com/t/rom-official-kali-nethunter-for-the-ticwatch-pro-3-wearos.4456797/page-8
from post Mar 9, 2024, to post Apr 24, 2024.
Monk987 (New member, bug reporter), feivel5 (Member), yesimxev (Senior Member, resourcer), steso90 (Senior Member, first bug resolver)

 DEVICE SPEC:
 - Model TicWatch Pro 3 Ultra GPS
 - Dimensions (mm) 47 x 48 x 12.3
 - Weight 41g
 - Color Shadow Black
 - Watch case Stainless steel and high-strength nylon with fiberglass
 - Screen Corning Gorilla Anti-fingerprint Cover Glass
 - Watch strap Fluoro Rubber (interchangeable), 22mm
 - Operating System Wear OS by Google
 - Chipset Qualcomm® Snapdragon Wear™ 4100 Platform and Mobvoi dual processor system
 - Memory RAM: 1GB / ROM: 8GB
 - Display 1.4“ 454*454 326ppi Full Color Always On Display AMOLED + FSTN
 - Connectivity Bluetooth 5.0, Wi-Fi:802.11b/g/n
 - GNSS GPS+Beidou+Glonass+Galileo+QZSS
 - NFC Payments Google Pay
 - Speaker Yes
 - Mic Yes
 - Vibrator Yes
 - PPG Yes
 - Barometer Yes
 - Sensors Accelerometer, Gyro Sensor, HD PPG Heart Rate Sensor, SpO2 Sensor, Low Latency Off-Body Sensor, Barometer
 - Battery capacity 577mAh
 - Durability IP68, Pool Swim/MIL-STD-810G
   
