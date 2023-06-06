# Arch Scripted Installation

This guide uses the archinstall script and Luke's Auto Rice Boostrapping Script (LARBS).

> See my alternative manual installation [here](https://github.com/derryleng/arch-manual-install).

## Table of Contents

- [Get the ISO](#get-the-iso)
- [Install Arch](#install-arch)
- [Connect to the internet (Wi-Fi)](#connect-to-the-internet-wi-fi)
- [Run archinstall](#run-archinstall)
- [Connect to internet on new system](#connect-to-internet-on-new-system)
- [Run LARBS](#run-larbs)

## Get the ISO

1. Download latest [official Arch ISO](https://archlinux.org/download/).
2. Use [Ventoy](https://www.ventoy.net/en/doc_start.html).
3. Boot with your Ventoy USB device.

## Install Arch

### Connect to the internet (Wi-Fi)

```bash
iwctl
```

Then in the iwctl prompt:

```bash
station wlan0 scan
station wlan0 get-networks
station wlan0 connect ...YOUR_SSID...
```

### Run archinstall

Assuming the script is not broken, just run:

```bash
archinstall
```

Set these:

- Keyboard layout: uk
- Mirror region: United Kingdom
- Locale language: en_GB.UTF-8
- Locale encoding: UTF-8
- Set drive and disk layout
- No disk encryption
- Bootloader: (any)
- Swap: False
- Hostname: your_host_name
- Root password: (set a password for root)
- User account: (don't create any other accounts for now - LARBs will prompt you)
- Profile: xorg + graphics driver
- Audio: pipewire
- Kernels: linux
- Network configuration: Use NetworkManager
- Timezone: Europe/London
- Automatic time sync (NTP): True

Reboot after this is all finished.

### Connect to internet on new system

Login with root, start NetworkManager and connect to the internet.

```bash
sudo systemctl enable NetworkManager.service
sudo systemctl start NetworkManager.service

# Now configure the networking
nmtui
```

### Run LARBS

```bash
curl -LO https://raw.githubusercontent.com/derryleng/arch-scripted-install/main/larbs.sh
sh larbs.sh
```
