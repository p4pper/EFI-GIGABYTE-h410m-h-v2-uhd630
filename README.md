**Do not endorse distributing and profiting from EFIs**
# EFI-GIGABYTE-H410M-H-V2-uhd630-Sequoia

![Screenshot 2024-12-14 at 4 04 01 PM](https://github.com/user-attachments/assets/97c888af-10ff-4fbc-9b21-d0f2d10e4b8c)

OC Version : 1.0.3 RELEASE
<details>
<summary><strong>Specifications</strong></summary>
</br>
  
| Component           | Specification                                   |
|---------------------|-------------------------------------------------|
| CPU                 | Intel Core i5-10500 @ 3.7 GHz, 12M Cache        |
| RAM                 | 32GB DDR4-2666MHz (XMP)                         |
| SSD                 | HP SSD 512GB SATA                               |
| Sound               | Realtek ALC897 (Layout-id 66)                   |
| Wireless, Bluetooth | Intel Centrino 130-N Singleband (No BT)         |
| Integrated GPU      | Intel UHD Graphics 630 4GB UNIFIED              |

</details>

<details>
<summary><strong>What works and what doesnt</strong></summary>
</br>

| Feature | Status |
| ------------- | ------------- |
| CPU Power Management | ✅ |
| (+HDMI) Sleep/Wake | ✅  |
| Intel HD630 Graphics Acceleration | ✅ |
| Intel Accelerator | ✅ |
| Intel VT-d | ✅  |
| Ethernet | ✅  |
| Audio and HDMI Audio | ✅  |
| iMessage/Facetime and App Store | ✅   |
| Speakers and Headphones | ✅ |
| Wi-Fi/Bluetooth | ✅ |
| Airdrop/Handoff | ❌  |
</details>

**NVRAM Boot arguments**.  
Add ``igfxonln=1`` to fix HDMI Waking from sleep.

**Kexts**   
![image](https://github.com/user-attachments/assets/1493a30c-fd4a-445c-892f-092a5c5a96f9)  

- Map your own ports using UTBMap tool on Windows. Enable Native class in UTBMap settings, and use your SMBios model. 
- Airportltwm is not supported in Sonoma or later. Use ltwm+heliport.

**ACPI**   
![image](https://github.com/user-attachments/assets/b5611e6a-33d4-4c49-a5a6-03d5f2edfcaa). 

- Generate them using SSDTime on Windows
- No patches needed, Ensure you have XHCI-unsupported.kext

**Whatevergreen**  
Use these settings to:
- Fix HDMI Output. 
- Fix Acceleration (ensure DMVT-Pre allocated is  128M at least, and DMVT-IGFX is Max)
- Unified VRAM of 4GiB

| PciRoot(0x0)/Pci(0x2,0x0)             | Value                          |
|---------------------------------------|--------------------------------|
| AAPL, ig-platform-id                  | 00009B3E                  |
| device-id                             | 9B3E0000                  |
| dpcd-max-link-rate                    | 14000000                  |
| enable-dpcd-max-link-rate-fix         | 01000000                  |
| framebuffer-patch-enable              | 01000000                  |
| framebuffer-portcount                 | 04000000                  |
| framebuffer-con1-enable               | 01000000                  |
| framebuffer-con1-alldata              | 010509000004000087010000  |
| framebuffer-con2-enable               | 01000000                  |
| framebuffer-con2-alldata              | 020609000004000087010000  | 
| framebuffer-con3-enable               | 01000000                  |
| framebuffer-con3-alldata              | 03040A000008000087010000  |
| framebuffer-unifiedmem                | FFFFFFFF                  |
| enable-hdmi20                         | 01000000                  |
| enable-Ispcon-support                 | 01000000                  |
| framebuffer-con3-has-Ispcon           | 01000000                  |
| framebuffer-con3-preferred-ls         | 01000000                  |


***Additional Information***   
Enable HashServices in config.plist      
SMBios is iMac21,1

**Updating from Ventura to Sonoma or later?**
Disable SecureBootModel in config.plist by changing it to ``Disabled``   
Clear your NVRAM using ResetNVRAMEntry.efi   
Boot to your macOS and re-run the Sonoma or later installer   
Your mac will restart and boot to the installer, there should be about 2-3 reboots, always boot to the macOS installer until it vanish.   
Enable SecureBootModel after update.

I'll slowly update this guide to include more details, for now, this will help many people.   
If you need any requests or help, please open an issue in this repo.    


