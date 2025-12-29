# Yocto Bluetooth A2DP on i.MX 8M Plus (LWB5+ USB)

## TL;DR
Built a Yocto (Kirkstone) image for **NXP i.MX 8M Plus EVK** that supports **Wi-Fi + Bluetooth** via **Ezurio LWB5+ USB dongle**, and validated **Bluetooth A2DP audio streaming** (phone → EVK headphone out).

- Yocto layer integration (`meta-summit-radio`)
- Custom image composition (BlueZ + PulseAudio + NetworkManager)
- Kernel config alignment for external USB radio + firmware load behavior
- End-to-end A2DP validation with `bluetoothctl` + PulseAudio/ALSA

➡️ Step-by-step guide: [`docs/step-by-step.md`](docs/step-by-step.md)  
➡️ Original published app note: https://lairdcp.github.io/guides/lwb5plus-tutorials/1.0/A2DP-test-LWB5p-dongle-iMX8M-Plus-EVK.html 

---

## What I Built
An embedded Linux system that can act as a **Bluetooth A2DP sink**, streaming audio from a smartphone to the i.MX 8M Plus EVK through PulseAudio → ALSA → WM8960 codec.

---

## Platform
**Hardware**
- [NXP i.MX 8M Plus EVK](https://www.nxp.com/design/design-center/development-boards-and-designs/8MPLUSLPD4-EVK)
- Ezurio (Laird) [LWB5+ USB Wi-Fi/Bluetooth dongle](https://www.ezurio.com/wireless-modules/wifi-modules-bluetooth/sterling-lwb5-plus-wifi-5-bluetooth-5-module)

**Software**
- Yocto Project (Kirkstone), Linux 5.15
- BlueZ 5, PulseAudio, ALSA
- NetworkManager

---

## Key Engineering Work
- Integrated `meta-summit-radio` into NXP BSP and resolved Yocto provider/dependency configuration.
- Built a custom image including Bluetooth + audio packages needed for A2DP.
- Adjusted kernel configuration to avoid conflicts and ensure stable external dongle operation.
- Verified Wi-Fi connectivity and Bluetooth A2DP streaming end-to-end.

---

## Disclaimer
This repo is a public, re-authored summary based on publicly available documentation and professional experience. No proprietary source code or internal materials are included.
