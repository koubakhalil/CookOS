# CookOS

CookOS is a bootable **live Linux system** for UEFI PCs, built from Ubuntu 24.04 packages. It runs from a USB stick (nothing is installed to your disk) and gives you a ready-to-use desktop with working Ethernet.

## What's in 1.0

- Xfce desktop with a dark theme, automatically logged in as `live` (no password, `sudo` works without one)
- Linux kernel 7.0 (Ubuntu HWE) with drivers for common Intel, Realtek, Broadcom and USB Ethernet adapters, plus firmware for Wi-Fi and graphics
- NetworkManager: Ethernet connects automatically over DHCP; Wi-Fi and Bluetooth are managed from the tray icons when your hardware has them
- PipeWire audio, Epiphany web browser, file manager, terminal, text editor, screenshot tool and GParted
- UEFI boot with Ubuntu's signed shim, GRUB and kernel, so it can boot with Secure Boot on
- Live session only: changes are lost when you shut down, and there is no installer yet

## Download

Get `cookos-1.0-amd64.iso` (about 1.3 GB) and its `.sha256` file from the [latest release](https://github.com/koubakhalil/CookOS/releases/latest).

## Put it on a USB stick

Writing the ISO **erases the USB stick** (4 GB or larger).

1. **Rufus (Windows):** select the ISO and, when asked, choose **DD Image mode**. Or use **balenaEtcher** (Windows, macOS, Linux).
2. Restart the PC and open its boot menu (usually F12, F10, F9, Esc or F2, depending on the brand). Pick the USB stick's **UEFI** entry.
3. Choose **CookOS (live session)**. If the screen stays black, restart and choose the **safe graphics** entry.

## Verify the download

SHA-256 of `cookos-1.0-amd64.iso`:

```
97a3874b1e43cb3aa6cdc80bf3141be59983aed555481537f0dd2be89a9080b6
```

- Windows: `certutil -hashfile cookos-1.0-amd64.iso SHA256`
- Linux: `sha256sum cookos-1.0-amd64.iso`
- macOS: `shasum -a 256 cookos-1.0-amd64.iso`

## Tested on

Booted in QEMU virtual machines with UEFI firmware, with Secure Boot on and off: it reaches the desktop, and Ethernet gets an address over DHCP with working DNS. **Not yet tested on physical hardware.**

## Sources and licences

CookOS is built from Ubuntu 24.04 ("noble") packages, which carry their own licences. The full package list is in `cookos-1.0-amd64.manifest.txt`, and the source packages are available from `archive.ubuntu.com/ubuntu`. CookOS is not an official Ubuntu release and is not affiliated with or endorsed by Canonical.
