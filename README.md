(Insert Image of final installed system here)

# Sections
- 0 Introduction
- 1 prerequisites
- 2 Installation
- 3 Installing Kde Plasma and Flatpak
- 4 Additional Software
## Section 0: Introduction

This is a guide on how to install and configure a debloated Fedora system that will hopefully be good for beginners and experts alike, we will be covering how to install the base system as well as configuring the installed system to get you what you need for your Linux system.

Why is this guide a thing? Doesn't a normal install work?

In the past I used Arch based distros and I liked how minimal the base system was and when I wanted something a little more stable and user Friendly Fedora was of interest. You could just install Fedora workstation as it is and move on with your life but I feel that 1800 or so packages on a vanilla fresh install is a little bit too much.

## Section 1: Prerequisites

You will need the following to install the new system:
- An Existing X86 computer with all data backed up
- An Internet Connection
- A 2nd Computer to ssh into the Fedora one
- A 4GB Flashdrive
- The Fedora Everything ISO which you can download [here](https://alt.fedoraproject.org/)
## Section 2: Installation

To get started you will need [Balena Etcher](https://etcher.balena.io/) to flash the iso file to your (empty) flash drive

Reboot your device and when the manufacturer's logo comes up mash the boot menu key (Example for Dell is F12) and select the flash drive to boot from (if you have a Nvidia Graphics card in your device you will have to boot into the main bios menu and disable secureboot because the drivers needed can't be loaded unless you do shenanigans to get it working)

Set your language and then go into ``Installation Destination`` and double click the disk you want to install Fedora to and click ``Done`` (WARNING: Make sure all important data is backed up before installation)

It is recommended to leave the root user disabled for security reasons but if you need it you can enable it

After setting your username an password, check to see if the timezone information is correct and don't forget to change the 24 hour clock to am/pm to get what you're used to (if you can't change the time format try clciking the ``Use Network Time`` toggle and switch it, don't forget to switch the toggle back)

As for software selection go with the ``Minimal Install`` option and if you need wifi then somewhere in the list to the right there should be a ``NetworkManager`` option that will make connecting to wifi possible

After that in the main menu click ``Begin Installation`` and wait for your (Very little packages!) Fedora system install

## Section 3 Installing KDE Plasma and Flatpak

You may be wondering why there is no GUI, don't worry it will be a few easy steps to install KDE plasma.

To make this simple we will be using an application called ``ssh`` to remote in from another computer so that we can just copy and paste the commands

Login to your computer and type the command ``ip a`` and you will note that there are 2 lines that start with ```inet``` please remember the 2nd one, on a different computer type the command: ``ssh yourusernamehere@192.168.1.something`` and login to your user

The hardest part is over and now copy and paste the following commands, first one installing the base KDE Plasma packages as well as hardware support packages for your system:

```
sudo dnf install NetworkManager-config-connectivity-fedora bluedevil breeze-gtk breeze-icon-theme cagibi colord-kde dolphin glibc-all-langpacks gnome-keyring-pam kde-gtk-config kde-style-breeze kdegraphics-thumbnailers kdeplasma-addons kdialog kdnssd kf5-akonadi-server kf5-akonadi-server-mysql kf5-baloo-file kf5-kipi-plugins khotkeys kmenuedit konsole5 kscreen kscreenlocker ksysguard kwalletmanager5 kwebkitpart kwin pam-kwallet phonon-qt5-backend-gstreamer pinentry-qt plasma-breeze plasma-desktop plasma-desktop-doc plasma-drkonqi plasma-nm plasma-pa plasma-user-manager plasma-workspace plasma-workspace-geolocation polkit-kde qt5-qtbase-gui qt5-qtdeclarative sddm sddm-breeze sddm-kcm sni-qt xorg-x11-drv-libinput @"Hardware Support" @base-x @"Common NetworkManager Submodules"
```

Next we must enable the display manager if we want the login screen to work
```
sudo systemctl enable sddm && sudo systemctl set-default graphical.target
```
Congrats! All the base system packages are now installed to make your system functional!

Just reboot your system with ``sudo reboot``

## Section 4: Additional Software

Your system is now up and running with the beautiful Kde Plasma but you will still need some additional packages to enable proper video playback
```
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install gstreamer1-plugins-{bad-\*,good-\*,base} gstreamer1-plugin-openh264 gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel
```

If your system is like mine and has a Nvidia GPU in it you will need the official drivers for the best performance in your gaming (If your graphics card is not supported by the latest drivers please refer to the guide [here](https://phoenixnap.com/kb/fedora-nvidia-drivers))
```
sudo dnf install akmod-nvidia
```
For the rest of the packages in the system we will be using Flatpak (unless otherwise needed) because it is a universal package manager which means that we can get access to the smae applications no matter what Linux distro we are using and it is also generally more stable and secure than the native package manager thanks to sandboxing

We will also install the Kde Discover app store to make package management a bit more user friendly since it is a gui frontend
```
sudo dnf install flatpak discover && flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
After a reboot you should be good to use Discover to install Flatpak packages onto your system

Web Browser options: ``Chrome``, ``Firefox``, ``Brave``, ``Chromium``, ``Ungoogled-Chromium``, ``Librewolf``, ``Waterfox`` and ``Opera`` are all installable from Flatpak as well as ``Thorium`` and ``Vivaldi`` avalible from their respective web sites

Alturnatives to MS Office: ``OnlyOffice Desktop Editors``, ``Libreoffice`` and ``WPS Office`` from Flatpak as well as ``OpenOffice`` from their website

Media Players: ``VLC``&``mpv`` from Flatpak as well as ``Dragon`` as a native system package

Firmware Updater: ``Gnome Firmware`` from Flatpak

More to come
