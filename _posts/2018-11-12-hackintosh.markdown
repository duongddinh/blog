---
layout: post
title: Hackintosh
date: 2018-11-12 15:47:15 +0300
description: Hackintosh guide. # Add post description (optional)
img: # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Mac, OS, Apple, MacOS, Hackintosh]
---

# Hackintosh guide

## What is hackintosh?

if you are here, i assume that you already know what that is

**TL;DR**: installl Macos in non-apple device(s)

> Hackintosh is not hard as it seems as long as you do it carefully

-----------------------

## Disclaimer:

1. Hackintosh is **illegal**
    - Under UELA, you only license the software
    - Read more [here](https://images.apple.com/legal/sla/docs/macosx107.pdf)
2. I _Do not_ encourage anybody to hackintosh his/her device(s)
3. This is what works for me; it does not neccessary mean it works for everyone (i use a laptop, not desktop)
4. There may be more bugs for you; these are bugs that presented to me
5. Do this with your own risk

----------------

## Requirements:

- **hardware:**

1. A computer
2. A Mac (the real mac [it is not recommended to use VM]) - Do not ask, "can we do this on windows," Of course, NO!
3. USB drive (>=8GB)
4. SSD (recommended)
5. RAM >= 4GB

- **software, files:** 

1. Clover configurator or mounting software ( download clover [here](https://www.tonymacx86.com/resources/clover-configurator.335/) ), clover bootloader (download [here](https://sourceforge.net/projects/cloverefiboot/))
2. 64 bit

--------------------

## Procedure:

### [+] Setup USB

Plug your USB in your Mac. After that, open disk utility (type in "disk utility" in search or launch pad -> click on it)

format the USB - make sure you back up your USB.

format:

 + name: **_[whatever you want]_**
 
 + format: **_Mac OS Extended (Journaled)_**
 
 + scheme: **_GUID Partition Map_**

Make sure that your Mac is on the version that you want to hackintosh

Download that version in the Appstore, make sure that it is in /Applications/

open terminal, type in

```

$sudo /Applications/Install\ macOS\ [version].app/Contents/Resources/createinstallmedia --nointeraction --volume /Volumes/[USB's name]/

```
 
 type in the password, wait for it; after it is done, open clover configurator, click on "mount EFI" in the left
 bar -> your USB name -> click on mount
 
 After that, there are two methods:
 
[-] **Method 1: _using pre-configurated EFI file_**
 
 + Advantage: you don't have to do much
 
 + Disadvantage: old version of clover, may not compatible with your device, still have to change something later on
 
 download [this](https://bitbucket.org/bobdinh139/hackintosh/downloads/) and copy it to your EFI file
 (Do note that this is for laptop, and if you have desktop, you have to change something - mentioned below)


[-] **Method 2: _you do it yourself_**

+ Advantage: get newer version of clover, compatible with your device

+ Disavantage: you have to do everything

open clover bootloader

just do what the program say, but if you get to the installation part, choose "customize" and choose your USB

_What you need in the customize:_

1. UEFI booting only
2. Drivers64UEFI
    - AppleImageCodec-64.UEFI
    - AppleKeyAggregator-64.UEFI
    - AppleUITheme-64.UEFI
    - DataHubDxe-64.UEFI
    - FirmwareVolume-64.UEFI
    - FSInject-64.UEFI
    - SMCHelper-64.UEFI
    - VboxHfs-64.UEFI
    - apfs
    - OsxAptioFix2Drv-64
    - PartitionDxe-64

Then click "install", type in your password and wait

### [+] Changes to the config.plist

Go to your EFI folder -> goto Clover -> config.plist -> open with Clover configurator

> If you cannot see your USB's EFI; goto Clover -> mount EFI -> mount your USB

#### Clover

**Boot**

In the "Boot" section, make sure the argument is:

```
shikigva=1 dart=0 -disablegfxfirmware -lilubetaall -igfxbeta

```

if you want to see the output instead of boring Apple logo, do this: 

```
shikigva=1 dart=0 -disablegfxfirmware -lilubetaall -igfxbeta -v

```

**Graphics**

In the "Graphics" option, find ig-platform-id and choose the HEX that fits your device (You can change this later)

If you don't do this or you do this incorrectly, MacOs will not load (But you can still change it in the boot loader)

If you don't really care for now or you just want safety first, do 
```

0x12345678

```
(Yes, you can always change it later)

**SMBIOS**

After that, click on "SMBIOS" in your left hand bar -> Click on the arrow below the clover's conputer's screen;
then, choose the version that fits your computer or close-to your computer.

Remember: if you use a desktop then choose iMac, laptop then choose Macbook Pro or Macbook Air or what ever kind of Macbook that fits you 
If your you has a laptop and you choose iMac, you will see some unwanted changes

### Kext

Go to Clover -> kext -> other

This is the list of Kext(s) file that you will need (You may need more later on):

+ [FakeSMC](https://bitbucket.org/RehabMan/os-x-fakesmc-kozlek/downloads/)
+ [VoodooPS2Controller](https://bitbucket.org/RehabMan/os-x-voodoo-ps2-controller/downloads/) - for desktop - fix not working mouse + keyboard 
+ [ACPI](https://bitbucket.org/RehabMan/os-x-acpi-battery-driver/downloads/) - for desktop - enable battery indicator
+ [USBInjectAll](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/)
+ [GenericUSBXHCI.kext](https://bitbucket.org/RehabMan/os-x-generic-usb3/downloads/)
+ [FakePCIID](https://bitbucket.org/RehabMan/os-x-fake-pci-id/downloads/)
+ [Lilu](https://github.com/acidanthera/Lilu/releases)
+ [IntelGraphicsFixup](https://github.com/lvs1974/IntelGraphicsFixup/releases)
+ [Realtek](https://bitbucket.org/RehabMan/os-x-realtek-network/downloads/)

> Now, eject your USB and plug it on the computer that you want to hackintosh on

-----------------------

## Hackintosh your non-Apple

### BIOS Settings:

Turn of your computer (not your mac), to go to BIOS (there are many ways you can do this [F2, Del,...], so you can look up your device on google) 

Also try to set your USB as a primary boot disk 

**recommended settings**

You may not have all of theses, especially if you are using a laptop, change what you can

 + Virtualization: _Enabled_
 + VT-d : Disabled
 + XHCI Hand-Off: _Enabled_
 + Legacy USB Support: _Auto/Enabled_
 + IO SerialPort: _Disabled_
 + Network Stack: _Disabled_
 + XMP Profile:  _Auto / Profile 1/Enabled_
 + UEFI Booting: _Priority_
 + Secure Boot: _Disabled_
 + Fast Boot: _Disabled_
 + OS Type: _Other OS_
 + Wake on LAN: _Disabled_

Dedicated Graphics, Integrated graphics card

 + Integrated Graphics: _Enabled_
 + Graphics: _PEG/PCIe Slot 1_
 + Initial Display Output: _PCIe 1 Slot_
 + DVMT Pre-Allocated: _128M or higher_

Dedicated graphics card

 + Integrated Graphics: _Disabled_
 + Graphics: _PEG/PCIe Slot 1_
 + Initial Display Output: _PCIe 1 Slot_

Intel iGPU

 + Integrated Graphics: _Enabled_
 + Graphics: _IGD/Integrated/iGPU/CPU Graphics_
 + DVMT Pre-Allocated: _128M or higher_

### Actually doing it:

Turn off your device - the one you want to hackintosh, make sure it is backed up

Go to temporary boot option (try F12, F11, F8) and choose your USB.

Select the "Boot Install" option and wait for it to install

After that, you will see several volumes, click on what Clover highlights

After it is done, choose boot from [your volume's name]

first, open disk ultility, not installing MacOS

Choose your disk -> click format 

it should look like this:

 + name: **_[whatever you want]_**
 
 + format: **_Mac OS Extended (Journaled)_**
 
 + scheme: **_GUID Partition Map_**
 
and wait ...

After it is done, click close ("x" button on left hand conner)

and go to install MacOS

I think from here on, you know what to do, but make sure you read all of this

### Boot up by not using USB:

Wait, you are not done yet. If you unplug your USB, the device will not boot up. What should you do

The solution is very simple

Go to your hackintoshed computer, open "clover configurator" or mounting software

Click on mount - both your hackintosh disk (The disk that you installed yout MacOS) and your USB

Copy all the file on the EFI folder in your USB

Paste it to the EFI folder on your hackintosh disk

> DONE!

-----------------------

## Fix bug(s)

I would recommend not to erase the USB because if you were to change something and
the clover does not boot up, you can use your USB to boot up your device.

Do note that after hackintosh, you will have bug(s) to fix; you can search for the kext
and use kext installer to fix some of the bugs. You can also look up/ask on google, reddit,
tonymac. If you want detailed write-up for patches, you can go to tonymac; some patches that I mentioned
here are just to solve somewhat of a problem.

you may need to change your resolution if you don't want lag or bad graphics
you can choose and select which fits yours, reboot your hackintosh; if you hackintosh does not boot up, don't panic,
turn of your computer and go to setting in clover bootloader, find _Graphic injector_ and go to _ig-platform-id_, 
change the hex; if it still not boot up, use default one - **0x12345678** and try again.

**Screen brightness**

[AppleBacklightFixup](https://bitbucket.org/RehabMan/applebacklightfixup/downloads/)

Put it to /L/E (Library/Extensions)

check kernel cache 

```
sudo kextcache -i /

```

then boot

**Battery percentage**

[OSXACPIBatteryDriver](https://bitbucket.org/RehabMan/os-x-acpi-battery-driver/downloads/)

install using kext installer

reboot

**Screen flickering, glitching in non-appstore software**
 
 Open clover -> Kernel and Kext patches -> KextToPatch 
 
 click on "+" button and add these two:

```
Name: com.apple.driver.AppleIntelFramebufferAzul
Find: 0600260a 01030303 00000002 00003001 00006000
Replace: 0600260a 01030202 00000002 00003001 00009000
Comment: 0x0a260006 9MB cursor bytes (vbo), 2 ports only (RehabMan)

Name: com.apple.driver.AppleIntelFramebufferAzul
Find: 01050900 00040000 87000000 02040900 00040000 87000000
Replace: 02040900 00080000 87000000 FF000000 01000000 40000000
Comment: 0x0a260006 disable 0204 port, change 0105 DP port to 0204 HDMI (RehabMan)

```

**Patch DSDT/SSDTs**

Use [MaciASL](https://bitbucket.org/RehabMan/os-x-maciasl-patchmatic/downloads/)
and [iasl](https://bitbucket.org/RehabMan/acpica/downloads/)

This [Tutorial](https://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/) here 

**AppleHDA and voodooHDA**

Some people prefer AppleHDA to voodooHDA, they argues that AppleHDA has better sound quality, but AppleHDA 
requires more work so I use VoodooHDA atm (I am lazy). I may try AppleHDA and give you an update.

### Unsupported device(s)

intel wifi is NOT supported, in the writing of this, unless there is/are someone/people writting it. 
As a result, bluetooth will not work either

so if you have intel wireless, expect your computer to not connect to wifi or bluetooth via intel card;

you have to buy or use external device to connect to wifi or bluetooth

TP-Link TL-WN725N works for me - 10.14 mojave - (about $10)

> there maybe more

------------------------

## Updating Clover bootloader

It may cause you hackintosh to not boot up, black screen 
so be careful while doing that

Goto clover configurator -> update -> check for update -> update

------------------------

## Additional files:

You may need kext installer, such as kext wizard, to install kext if you are not in boot  

-------------------------

## Keyboard

Alt: Command key

Windows: Option key (-\_)

Ctrl: Control key (^)

**Remap**

Setting -> keyboard -> Application -> add 

> example:

Copy, paste (Ctrl+C, Ctrl+V)

Menu tile: Copy

Keyboard shortcut: Ctrl C

> Brightness then you can patch DSDT

> Remember, drag and drop is not VoodooPS2 problem, it can be enabled in setting -> accessibility -> mouse and touch pad-> trackpad option -> enable draging

---------------------------

## Credits:

> tonymacx86.com

> hackintosher.com

> Rehabman

> TechHowdy