# ArchTitus Installer Script
[![GitHub Super-Linter](https://github.com/ChrisTitusTech/ArchTitus/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter)

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/de6bd62b-34ea-40e5-b17c-77167fb5cfb8/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220430%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220430T032422Z&X-Amz-Expires=86400&X-Amz-Signature=fa4df257bd431896376094f7e8aca5e2b71879acae745f13bcdd68d7f28c8e07&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" />

This README contains the steps I do to install and configure a fully-functional Arch Linux installation containing a desktop environment, all the support packages (network, bluetooth, audio, printers, etc.), along with all my preferred applications and utilities. The shell scripts in this repo allow the entire process to be automated.)

---
## Create Arch ISO or Use Image

Download ArchISO from <https://archlinux.org/download/> and put on a USB drive with [Etcher](https://www.balena.io/etcher/), [Ventoy](https://www.ventoy.net/en/index.html), or [Rufus](https://rufus.ie/en/)

If you don't want to build using this script I did create an image @ <https://www.christitus.com/arch-titus>

## Boot Arch ISO

From initial Prompt type the following commands:

```
pacman -Sy git
git clone https://github.com/mehultw/ArchTitusV2.git
cd ArchTitus
./archtitus.sh
```

### System Description
This is completely automated arch install. It includes prompts to select your desired desktop environment, window manager, AUR helper, and whether to do a full or minimal install. The KDE desktop environment on arch includes all the packages I use on a daily basis, as well as some customizations. 

Added packages for install using aur and pacman, includes packages specific to Mehul.

## Troubleshooting

__[Arch Linux RickEllis Installation Guide](https://github.com/rickellis/Arch-Linux-Install-Guide)__

__[Arch Linux Wiki Installation Guide](https://wiki.archlinux.org/title/Installation_guide)__

The main script will generate .log files for every script that is run as part of the installation process. These log files contain the terminal output so you can review any warnings or errors that occurred during installation and aid in troubleshooting. 
### No Wifi

You can check if the WiFi is blocked by running `rfkill list`.
If it says **Soft blocked: yes**, then run `rfkill unblock wifi`

After unblocking the WiFi, you can connect to it. Go through these 5 steps:

#1: Run `iwctl`

#2: Run `device list`, and find your device name.

#3: Run `station [device name] scan`

#4: Run `station [device name] get-networks`

#5: Find your network, and run `station [device name] connect [network name]`, enter your password and run `exit`. You can test if you have internet connection by running `ping google.com`, and then Press Ctrl and C to stop the ping test.

## Reporting Issues

An issue is easier to resolve if it contains a few important pieces of information.
1. Chosen configuration from /configs/setup.conf (DONT INCLUDE PASSWORDS)
1. Errors seen in .log files
1. What commit/branch you used
1. Where you were installing (VMWare, Virtualbox, Virt-Manager, Baremetal, etc)
    1. If a VM, what was the configuration used.
## Credits

- Customized script was forked from ArchTitus by ChrisTitusTech: https://github.com/ChrisTitusTech/ArchTitus
- Original packages script was a post install cleanup script called ArchMatic located here: https://github.com/rickellis/ArchMatic
- Thank you to all the folks that helped during the creation from YouTube Chat! Here are all those Livestreams showing the creation: <https://www.youtube.com/watch?v=IkMCtkDIhe8&list=PLc7fktTRMBowNaBTsDHlL6X3P3ViX3tYg>
