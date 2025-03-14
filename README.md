# Dell-Inspiron-14-5490-OpenCore

![image](https://user-images.githubusercontent.com/79068208/156099352-be17a6a1-64d3-428c-a4fd-ca65de19719e.png)


An updated fork of the original EFI folder.

Update: i'll be maintaining this per request of the owner, so you should head here for updated versions.

My specs:  
Intel Core i5-10210U @ 1.60 GHz.   
20GB DDR4-2667 SODIMM RAM (4GB soldered, 16GB additional).  
Patriot P300 NVMe (512GB)
Intel UHD Graphics 620 (0x9b41) (spoofed to 0x3e9b).  
NVIDIA GeForce MX 230 (Disabled via `-wegnoegpu`).  
Fenvi BCM94360NG Wireless card (802.11ac).  
Realtek USB Camera.  
Shenzhen Goodix Fingerprint.  

What works:  
Audio Out  
Power Management  
Camera  
Built-in Speakers  
Battery Percentage Monitor  
HDMI & HDMI audio  
Trackpad gestures  
Backlight keys  
All USB Ports  
WiFi, Airdrop, Airplay and Bluetooth  

Fixed:  
Sidecar (USB Map Issue)  
Headphone jack audio (Set `alcid=16` or `10000000` in `DeviceProperties`)  
Patriot SSD (Remove `NVMeFix.kext`)  
> NOTE: Changing the `alcid` causes instability with main speakers.  

Untested:  
Displayport via USB-C (disabled in config.plist)  
Security lock  

Partially working:  
Fingerprint sensor (not working in macOS, use VMware Fusion with USB passthrough on Windows)

Not working:  
Microphone (Intel SST)  
Headphone jack input (Realtek issue)  
Disable NVIDIA GPU with SSDT (Freezes 10 seconds after login)  
Trackpad with SSDT-GPI0 (Trackpad OS Checking) SSDT-XOSI works fine though.  
Windows Dual-boot (SSDT-XOSI conflict)

Notes:  
The serial number in `Platforminfo > Generic` is blanked out. You can generate a serial with [GenSMBIOS.](https://github.com/corpnewt/GenSMBIOS)  
USB Map Kext is removed because some variants of this laptop have different USB configurations.  
My BIOS revision is 1.17, so please update to the latest Dell BIOS before proceeding.  
My CFG Lock is disabled using [Dortania's method](https://dortania.github.io/OpenCore-Post-Install/misc/msr-lock.html) so if your CFG Lock is still enabled, enable `AppleXcpmCfgLock` in `Kernel > Quirks`. (ControlMSRE2 reports CFG lock enabled, idk why).  
