# Arch Scripted Installation

This is a minimal Arch installation for my own setup. I wrote this to keep track of the steps I have taken and it is definitely not a replacement for the far more detailed and comprehensive guide on the ArchWiki (which can be found [here](https://wiki.archlinux.org/title/Installation_guide)).

See the alternative manual installation [here](https://github.com/derryleng/arch-manual-install).

## Get the ISO

Get the latest official Arch ISO from
https://archlinux.org/download/.

Don't bother with formatting your USB stick every time and just use [Ventoy](https://www.ventoy.net/en/doc_start.html). 

If you're planning on overwriting any existing drives, back up your data.

Restart your PC and boot with your USB drive for next section.

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

### Update mirrors and package lists

Use reflector to update the fastest mirrors for pacman.

```bash
reflector --country GB --protocol https --latest 10 --sort rate --save /etc/pacman.d/mirrorlist
```

Make sure package lists are up to date.

```bash
pacman -Sy
```

### Run archinstall

Follow instructions.

```bash
archinstall
```

Reboot after this is all finished.

### Connect to internet on new system

Assuming you have successfully booted into new system, start up NetworkManager and connect to the internet.

```bash
sudo systemctl enable NetworkManager.service
sudo systemctl start NetworkManager.service

# Now configure the networking
nmtui
```

### Run LARBS

```bash
curl -s https://github.com/derryleng/arch-scripted-install/blob/main/larbs.sh | sh -s
```
