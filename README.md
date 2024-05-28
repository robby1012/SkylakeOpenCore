Skylake i5 6500 OpenCore Config

## **VERY IMPORTANT**, there is no guarantee this Config working on your System

## Computer Hardware

* Asrock H110D4-M2
* Intel i5 6500
* 16GB DDR4 2133 (SK Hynix)
* Graphics Intel HD 530
* Audio Card：Realtek ALC662
* Storage : Sata SSD 512GB
* USB
* Installer : Mac OS Sonoma

# A bit History
It's been a long time since I installed Hackintosh.

Last time I used iAtkos distro on my Asus Laptop to install Snow Leopard.

Just knew OpenCore recently, God, the documentation is really awesome.

Since I'm a programmer so all the setting and coding looks familiar, LOL.
So I decided to give it a try

USB Controller is the most hurdle for installing hackintosh to this system


You **NEED** to mapping your motherboard USB using [USBToolBox](https://github.com/USBToolBox/tool)

Failed to do so will make your usb keyboard or mouse not working. On this config I added USBInjectAll for last resort.

Copy generated UTBMap.kext to EFI\OC\Kexts


SSDT also **very important**, don't use precompiled from internet, every motherboard has different pci layout.


The best thing is to BUILD your own, easiesr way using [SSDTTime](https://github.com/corpnewt/SSDTTime)

copy SSDTTime generated .aml to EFI\OC\ACPI\

if have embeded programming knowledges you can manually add ssdt using iasl.

Minimum SMBIOS to use : iMac18,1 but this config I used iMac19,1 so no need to use -no_compat_check to kernel args
You can generate your own using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)

**Don't Messing NVRAM Setting except boot-args**


You can edit config.plist from OpenShell without booting to windows

but you must test wich partition of your installer

OpenShell will list available partition first time you open it

type this command, example :

`` FS0: ``

`` ls ``

if you not see EFI folder, try another partion, i.e FS1:

if you see EFI folder, type this command:

`` cd EFI\OC\ ``

`` edit config.plist ``

make your necessary edit
Press **Ctrl+S** to save

type command ``reset`` to reboot PC


## Step
## BIOS Configuration
### Disabled
* Serial Port
* Parallel Port
* Secure Boot

### Enabled
* Virtualization VT-D

Copy EFI Folder to EFI partition of Installer
on Windows you can use Aomei Partition Assistant. Assign EFI partition Drive Letter.
Use Explorer++ (run as admin) to navigate (Default Windows Explorer Won't Allow you to access)

Set Motherboard Boot Order to your Instalation Device
