<p align="center">
  <img src="../img/favicon.ico" alt="UniOS logo" width="200">
</p>

# Installing UniOS
This guide walks you through downloading UniOS, putting it on a USB stick and installing it on your computer. No Linux experience needed, if you can install a game you can install UniOS.

## Before you start
Make sure your computer meets the minimum requirements:

- A 64-bit (x86-64) computer, Apple Silicon Macs and ARM laptops are **not** supported
- At least 2 CPU cores
- At least 4GB of RAM
- At least 25GB of free storage
- A USB stick of 8GB or more (**everything on it will be erased**, unless you use Ventoy, see below)
- An internet connection is recommended during the installation

### **REMEMBER**: Installing an operating system can erase your disk. Back up anything important (documents, photos, university projects) to an external drive or the cloud before you continue.

## 1. Download the ISO
Head to our download server and grab the newest `.iso` file (the name contains the release date, e.g. `UniOS-2026.09.24-x86_64.iso`):

<a href="https://download.unios-project.eu/" target="_blank">download.unios-project.eu</a>

You can also use the download button on our <a href="https://unios-project.eu" target="_blank">webpage</a>. The file is about 4GB, so give it a few minutes. We publish a new ISO every month (see [General Dev Workflow](generalworkflow.md)), but an older ISO is fine too, the system updates itself after the installation.

## 2. Make a bootable USB
Pick **one** of the following tools.

### Ventoy (recommended, Windows & Linux)
<a href="https://www.ventoy.net" target="_blank">Ventoy</a> lets you keep many ISOs on one stick, and you just copy the `.iso` file onto it like any other file.

1. Download Ventoy and run `Ventoy2Disk.exe` (Windows) or `VentoyGUI` (Linux)
2. Select your USB stick and click **Install**. If the stick already has files you want to keep and is formatted as NTFS, use **Option → Non-destructive Install** instead
3. Copy `UniOS-....iso` onto the stick

### Rufus (Windows)
1. Download <a href="https://rufus.ie" target="_blank">Rufus</a> and open it
2. Select your USB stick under **Device** and the UniOS ISO under **Boot selection**
3. Click **Start**, if Rufus asks, choose **Write in DD Image mode**

### balenaEtcher (Windows, macOS & Linux)
1. Download <a href="https://etcher.balena.io" target="_blank">balenaEtcher</a> and open it
2. **Flash from file** → pick the ISO, **Select target** → pick the USB stick, then **Flash!**

### dd (Linux, for the terminal enjoyers)
Find your stick with `lsblk` and double check the name, `dd` will happily overwrite your main disk if you tell it to:
```sh
sudo dd if=UniOS-2026.09.24-x86_64.iso of=/dev/sdX bs=4M status=progress oflag=sync
```

## 3. Boot from the USB
1. Plug in the stick and restart the computer
2. Open the boot menu by pressing the right key as soon as the computer turns on, it is usually one of `F12`, `F11`, `F10`, `F8`, `Esc` or `F2` depending on the manufacturer (Dell/Lenovo: `F12`, HP: `F9` or `Esc`, ASUS: `F8` or `Esc`, Acer: `F12`)
3. Select your USB stick (if you see it twice, prefer the one that says **UEFI**)
4. If you used Ventoy, pick the UniOS ISO from the Ventoy menu and choose **Boot in normal mode**

If the computer refuses to boot the stick or shows a "Secure Boot violation" message, go into the BIOS/UEFI settings (usually `F2` or `Del` at startup) and **disable Secure Boot**, then try again.

## 4. Try it out (Live session)
UniOS will start in a live session straight from the USB, you will be logged in automatically and nothing has been changed on your computer yet. Feel free to look around, check that Wi-Fi, sound and your screen work properly before installing.

## 5. Install UniOS
Start the installer by double clicking **Install UniOS** on the desktop (it may also open by itself when the live session starts). The installer will guide you through the following:

1. **Language**: choose the language of the system
2. **Location**: choose your region and time zone (e.g. `Europe/Athens`)
3. **Keyboard**: choose your keyboard layout, you can test it in the text box
4. **Partitions**: choose where UniOS will be installed
    - **Erase disk**: UniOS takes over the whole disk, the simplest option, **everything on that disk is deleted**
    - **Install alongside**: keeps your current system (e.g. Windows) and lets you choose between them on every boot
    - **Manual partitioning**: for people who know what they are doing
5. **Users**: your name, username, computer name and password. Don't forget your password, you will need it to install apps and updates
6. **Summary**: check everything one last time and click **Install**

The installation takes 10 to 30 minutes depending on your computer. When it finishes, check **Restart now**, click **Done** and **unplug the USB stick** when the screen goes black.

### Dual booting with Windows
If you chose **Install alongside**, do the following in Windows **before** installing:

- Disable **Fast Startup** (Control Panel → Power Options → Choose what the power buttons do)
- If BitLocker is enabled, write down your recovery key or suspend BitLocker, Windows may ask for it after the installation
- Make sure you have enough free space on the disk (at least 25GB) for UniOS

## 6. First boot
After the restart, log in with the user you created. **UniDesk** will greet you and help you set up the system for your university and department. From there on:

- Install the software your courses need with [UniBackpack](unibackpack.md)
- Keep up with the news of your university using [UniNews](uninews.md)
- Keep your system up to date with [unios-update](unios-update.md), it will notify you from the system tray when updates are available

## Want to try it in a virtual machine first?
You can test UniOS without touching your computer using <a href="https://www.virtualbox.org" target="_blank">VirtualBox</a>:

1. Create a new VM, type **Linux**, version **Arch Linux (64-bit)**
2. Give it at least 4GB of RAM, 2 CPUs and a 25GB disk
3. In **Settings → System**, tick **Enable EFI**
4. In **Settings → Storage**, attach the UniOS ISO to the optical drive and start the VM
5. After the installation, remove the ISO from the optical drive before rebooting

## Something went wrong?
Don't panic, come and talk to us! You can find us on Discord, open an issue on <a href="https://github.com/open-source-uom/unios-iso/issues" target="_blank">GitHub</a> or visit us in office B-102 of the University of Macedonia every Sunday. See [General Dev Workflow](generalworkflow.md) for all the ways to reach us.
