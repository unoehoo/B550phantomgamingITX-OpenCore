# OpenCore EFI
Version updated on description in release. Tested on Ventura, should work for Monterey too. 5700G iGPU, APU. B550. SMBIOS iMac20,1

# What this is
This is a record for the future me to use as reference. 
This is not a guide, although you may use anything from this repository at your own risk. I have merely gathered data and information from available online sources. All credits to the developers at dortania, chefkissinc, and anyone who contributed selflessly to make this work.

# Guides & notes
- Follow [guide to files](https://chefkissinc.github.io/guide) and [guide to setup](https://dortania.github.io/OpenCore-Install-Guide/).
- PlatformInfo unpopulated.
- Check and update [core count](https://github.com/AMD-OSX/AMD_Vanilla).
- Persist [Bluetooth pairing](https://www.reddit.com/r/hackintosh/comments/p5ost3/macos_monterey_and_windows_bluetooth_pairing/) across MacOS and Windows.

# Build
- ASRock B550 Phantom Gaming ITX/AX v2.30
- R7 5700G
- 2x16g Crucial DDR4-3200 | CP16G4DFRA32A
- 1tb NVMe 2280 Crucial P3 | CT1000P3SSD8
- Intel I225-V Ethernet
- Intel AX200 Wifi + bluetooth on board
- Audio ALC1220
- Cryorig m9 plus
- DarkFlash DLH21 SFF mini-ITX
- DarkFlash C6MS 120 case fans
- Corsair SF600 SFX PSU
- Xiaomi monitor Mi 30 HFCW, 2560x1080 @ 120Hz via DP

# BIOS settings
Necessary
- Boot > CSM > disabled
- Adv > AMD PBS > graphics > changed external default to internal graphics
- Adv > PCI > above 4g decoding > enabled (check Ethernet if it still works fine)
- Adv > PCI > resize BAR support > enabled
- Adv > trusted computing > tpm disable
- Adv > CPU config > AMD fTPM also disabled
- Adv > AMD CBS > NBIO > IOMMU already disabled

Graphics
- Adv > AMD CBS > NBIO common options > GFX config > iGPU config > set to UMA_specified &
- Adv > AMD CBS > NBIO common options > GFX config > iGPU config > UMA frame buffer size (THIS ONE WORKS)

GFX Note:
- Adv > onboard devices config > uma frame buffer > auto (useless, can leave on auto)

Additional
- Adv > onboard > led in s5 > enabled to disabled
- Adv > acpi > deep sleep in s4 & s5 (to disable always on USB power, s5 alone didn't quite seem to work??)

# Setup notes
Extremely smooth setup.
However, this is my first motherboard with LED headers detected on the tool. LED headers **should not** be included in the [USB map](https://github.com/corpnewt/USBMap). Cost me 3 days of troubleshooting. And apparently it was written somewhere, I just didn't come across that note. For that matter..

# USB Map
- One bluetooth internal type 255.
- Front USB A type 3 x 2 and front USB C type 10 without switch (flipping the USB-C shows up as a different port).
- One board USB C with switch type 9.
- Two board USB 3, one of which has an internal split.
