# How [Meshtastic](https://meshtastic.org/) Works

Meshtastic creates a mesh network where devices communicate using `LoRa` (long-range) radio. Connect your phone or computer to a radio via Bluetooth, WiFi, or USB - and communicate with others across vast distances without any internet or cell service.

# Supported Hardware

Before you begin, it's important to determine which kind of hardware you're using. Meshtastic works closely with our Partners and Backers who produce officially supported hardware. These devices are tested, documented, and recommended for the best Meshtastic experience.

There is also a wide range of [community supported hardware](https://meshtastic.org/docs/hardware/devices/community-supported/) available; however, these devices are not officially supported by Meshtastic. Please reach out to the community via [Discord](https://msh.to/discord) for assistance.

Below you'll find examples of supported hardware organized by MCU type. Once you've identified your device, we'll walk you through verifying your data cable, flashing the firmware, and connecting and configuring your device.

## ESP32

The ESP32 chip is equipped with both WiFi and Bluetooth, making it ideal for devices that need web interface access or WiFi-based configuration. ESP32-S3 variants offer improved performance.

### Partner Hardware

![seeed sensecap indicator](https://flasher.meshtastic.org/img/devices/seeed-sensecap-indicator.svg)

#### Seeed Studio

[SenseCAP Indicator](https://meshtastic.org/docs/hardware/devices/seeed-studio/sensecap/indicator/) — 4" touchscreen driven by ESP32-S3 and RP2040 Dual-MCU

![rak_3312](https://flasher.meshtastic.org/img/devices/rak_3312.svg)

#### RAK Wireless

[RAK3312 Core module](https://meshtastic.org/docs/hardware/devices/rak-wireless/wisblock/core-module/?rakcore=RAK3312) — ESP32-S3-based WisBlock modular core

![thinknode_m2](https://flasher.meshtastic.org/img/devices/thinknode_m2.svg)

#### Elecrow

[ThinkNode M2](https://meshtastic.org/docs/hardware/devices/elecrow/thinknode/?thinknode-series=m2) — Portable ESP32-S3 device built for outdoor use

### Backer Hardware

![t deck](https://flasher.meshtastic.org/img/devices/t-deck.svg)

#### LILYGO®

[T-Deck / T-Deck Plus / T-Deck Pro](https://meshtastic.org/docs/hardware/devices/lilygo/tdeck/) — Standalone devices with screen and keyboard

![station g2](https://flasher.meshtastic.org/img/devices/station-g2.svg)

#### B&Q Consulting

[Station G2](https://meshtastic.org/docs/hardware/devices/community-supported/b-and-q-consulting/station-series/) — High power LoRa transceiver for licensed ham operation

![seeed xiao s3](https://flasher.meshtastic.org/img/devices/seeed-xiao-s3.svg)

### Community Supported

[Xiao ESP32-S3 Kit](https://meshtastic.org/docs/hardware/devices/community-supported/seeed-studio/wio-series/wio-sx1262s/?wio-sx1262=esp32-s3) — Compact LoRa dev kit

## nRF52

The nRF52 chip is much more power efficient than the ESP32 chip and easier to update via UF2 bootloader, but is only equipped with Bluetooth (no WiFi). Ideal for battery-powered and solar deployments.

### Partner Hardware

![tracker t1000 e](https://flasher.meshtastic.org/img/devices/tracker-t1000-e.svg)

#### Seeed Studio

[Card Tracker T1000-E](https://meshtastic.org/docs/hardware/devices/seeed-studio/sensecap/card-tracker/) — IP65-rated card-sized tracker with GPS

![rak_wismesh_tag](https://flasher.meshtastic.org/img/devices/rak_wismesh_tag.svg)

#### RAK Wireless

[WisMesh Tag](https://meshtastic.org/docs/hardware/devices/rak-wireless/wismesh/tag/) — Portable location tracker with IP66 rating

![thinknode_m3](https://flasher.meshtastic.org/img/devices/thinknode_m3.svg)

#### Elecrow

[ThinkNode M3](https://meshtastic.org/docs/hardware/devices/elecrow/thinknode/?thinknode-series=m3) — nRF52840 with LR1110 radio and GPS

### Backer Hardware

![t echo](https://flasher.meshtastic.org/img/devices/t-echo.svg)

#### LILYGO®

[T-Echo](https://meshtastic.org/docs/hardware/devices/lilygo/techo/) — All-in-one unit with E-Ink screen, GPS, and battery in injection-molded case

![muzi_r1_neo](https://flasher.meshtastic.org/img/devices/muzi_r1_neo.svg)

#### muzi ᴡᴏʀᴋꜱ

[R1 Neo](https://meshtastic.org/docs/hardware/devices/muziworks/r1-neo/) — Custom-designed nRF52840 device with GPS

## RP2040/RP2350

The RP2040 and RP2350 are dual-core chips developed by Raspberry Pi. Cost-effective options for DIY projects.

### Partner Hardware

#### RAK Wireless

- [RAK11310 Core module](https://meshtastic.org/docs/hardware/devices/rak-wireless/wisblock/core-module/?rakcore=RAK11310) — RP2040-based WisBlock modular core with SX1262

### Community Supported

- Raspberry Pi Pico + Waveshare LoRa Module (Note: **Bluetooth on the Pico W is not yet supported by Meshtastic**)

info

If your device is not listed above, please review our [supported devices](https://meshtastic.org/docs/hardware/devices/) to determine which MCU your device has or contact us in [Discord](https://discord.gg/ktMAKGBnBs) with any questions.

## Verify Data Cable

STOP! Put The Power Cable Down!

Never power on the radio without attaching an antenna as doing so could damage the radio chip!

Prior to connecting your Meshtastic device to the computer, you should perform the following basic checks.

Some cables only provide _charging_, verify that your cable is also capable of _transferring data_ before proceeding. To check if your cable can also transfer data, try connecting it to another device (like a phone) and see if you can copy a file to or from it. If the file transfer works, then your cable is also able to transfer data and you can continue.

## Install Serial Drivers

caution

nRF52/RP2040/RP2350 devices typically do not require serial drivers. They use the UF2 bootloader which makes the devices appear as flash drives. Do _NOT_ download the USB device drivers unless required to install UF2 support.

If you require serial drivers installed on your computer, please choose one of the options below and install it before continuing.

## Flash Firmware

After completing the previous steps, you can now flash the Meshtastic firmware onto your device. To proceed, select the appropriate device type for your device.

## Connect and Configure Device

After flashing the Meshtastic firmware onto your device, you can now move on to initial configuration.