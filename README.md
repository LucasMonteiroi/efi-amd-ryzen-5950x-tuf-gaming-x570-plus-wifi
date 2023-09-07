# EFI AMD Ryzen 9 5950X + x570 TUF Gaming Plus

Note|Description
:----|:----
Initial macOS Support|macOS 10.13, High Sierra.

- Opencore version: 0.9.4
- Release date: 07/08/2023
- Included **additional** kexts (for ethernet, audio, etc);
- Included the **necessary** ACPI patches (.aml);

<br>

# Basic Steps

1. Generate and complete your SMBIOS infos - **ALWAYS**;
2. Adjust your BIOS;
3. Install macOS and enjoy :)

<br>

# Features
- [x] Very light, very clean, basic files for your Hackintosh.
- [x] Made with latest OpenCore versions.
- [x] Two editions - *Release* and *Debug* Edition.
- [x] Updated montly with refresh versions of Opencore.

<br>

# Kexts

### Required

Kext|Description
:----|:----
[AMDRyzenCPUPowerManagement.kext](https://github.com/trulyspinach/SMCAMDProcessor/releases)|For [AMD Power Gadget](https://github.com/trulyspinach/SMCAMDProcessor).
[SMCAMDProcessor.kext](https://github.com/trulyspinach/SMCAMDProcessor/releases)|For [AMD Power Gadget](https://github.com/trulyspinach/SMCAMDProcessor).
[AppleMCEReporterDisabler.kext](https://github.com/acidanthera/bugtracker/files/3703498/AppleMCEReporterDisabler.kext.zip)|Useful starting with Catalina to disable the AppleMCEReporter kext which will cause kernel panics on AMD CPUs and dual-socket systems.
[Lilu.kext](https://github.com/acidanthera/Lilu/releases)|Patch many processes, required for AppleALC, WhateverGreen, VirtualSMC and many other kexts.
[VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC/releases)|Emulates the SMC chip found on real macs, without this macOS will not boot.<br>Alternative is FakeSMC which can have better or worse support, most commonly used on legacy hardware.
[WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)|Used for graphics patching, DRM fixes, board ID checks, framebuffer fixes, etc; all GPUs benefit from this kext.

### Ethernet
Kext|Description
:----|:----
[RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X/releases)|For Realtek's Gigabit Ethernet.<br>Sometimes the latest version of the kext might not work properly with your Ethernet. If you see this issue, try older versions.

### WiFi and Bluetooth
Kext|Description
:----|:----
[AirportItlwm](https://github.com/OpenIntelWireless/itlwm/releases)|Adds support for a large variety of Intel wireless cards and works natively in recovery thanks to IO80211Family integration.
[IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases)|Adds Bluetooth support to macOS when paired with an Intel wireless card.
[IntelBTPatcher](https://openintelwireless.github.io/IntelBluetoothFirmware/FAQ.html#intelbtpatcher)|Workaround for a bug in bluetoothd by initializing the bluetooth module properly before attempting a LE Scan 

### Audio

Kext|Description
:----|:----
[AppleALC.kext](https://github.com/acidanthera/AppleALC/releases)|Used for AppleHDA patching, allowing support for the majority of on-board sound controllers.<br>AMD 15h/16h may have issues with this and Ryzen/Threadripper systems rarely have mic support.

### Others
Kext|Description
:----|:----
[NVMeFix](https://github.com/acidanthera/NVMeFix/releases)|Used for fixing power management and initialization on non-Apple NVMe.
[RestrictEvents](https://github.com/acidanthera/RestrictEvents/releases)|Better experience with unsupported processors like AMD, Disable MacPro7,1 memory warnings and provide upgrade to macOS Monterey via Software Updates when available.
[FeatureUnlock](https://github.com/acidanthera/FeatureUnlock)|Add Sidecar support to unsupported models
[CryptexFixup](https://github.com/acidanthera/CryptexFixup)|Various patches to install Rosetta Cryptex
[BlueToolFixup](https://github.com/acidanthera/BrcmPatchRAM)|Required for macOS 12 or newer, as in macOS 12 Apple has changed parts of the Bluetooth stack from kernel-space to user-space as detailed in [here](https://github.com/acidanthera/bugtracker/issues/1669) and [here](https://github.com/acidanthera/BrcmPatchRAM/pull/12). Requires Lilu 1.5.4+. Do not use it with BrcmBluetoothInjector for macOS 12 or newer.
[USBMap](https://github.com/corpnewt/USBMap)| USBMap Utility (All ports are mapped)

<br>

# Important changes on **config.plist**
Update **config.plist** in PlatformInfo > Generic with YOUR informations.
<br>
1. MLB (Board Serial)
<br>
1. ROM (Mac Address)
<br>
1. SystemSerialNumber (Serial)
<br>
1. SystemUUID (SmUUID)*

Please use [*genSMBIOS*](https://github.com/corpnewt/GenSMBIOS/archive/refs/heads/master.zip) for generate values for above itens.
<br>
Please use [*ProperTree*](https://github.com/corpnewt/ProperTree/archive/refs/heads/master.zip) for configure/edit your config.plist.

<br>

# BIOS Settings

### Disable
- Fast Boot
- Secure Boot
- Serial/COM Port
- Parallel Port
- Compatibility Support Module (CSM)(Must be off, GPU errors like `gIO` are common when this option in enabled)

<br>

# References
https://dortania.github.io/OpenCore-Install-Guide/AMD/zen.html
<br>
https://github.com/luchina-gabriel/BASE-EFI-AMD-RYZEN-THREADRIPPER
<br>

## Discord - Universo Hackintosh
- [Access Discord](https://discord.universohackintosh.com.br)