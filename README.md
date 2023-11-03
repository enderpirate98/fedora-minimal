(Insert Image of final installed system here)

# Sections
- 0 Introduction
- 1 prerequisites
- 2 Installation
- 3 Installing Kde Plasma and Flatpak
- 4 Codecs and Drivers
- 5 Additional Software

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
- The Fedora Everything ISO which you can download [here]([https://pages.github.com/](https://alt.fedoraproject.org/)https://alt.fedoraproject.org/)
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

Login to your computer and type the command ``ip a`` and you will note that there are 2 lines that start with ```inet``` please remember the 2nd one, on a different computer type the command: ``ssh yourusernamehere@your.ip.address`` and login to your user

The hardest part is over and now copy and paste the following commands, first one installing the base KDE Plasma packages as well as hardware support packages for your system:

```
sudo dnf install fgjerijgei sorry I need to go and continue this later
```
