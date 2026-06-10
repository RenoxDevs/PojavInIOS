
# PojavLauncher & Amethyst Sideloading iOS With Termux: 

This repository provides an automated environment and guide to sideload iOS applications (specifically PojavLauncher and Amethyst Launcher) directly from an Android device to an iOS device using Termux and an OTG cable. It combines standard pairing protocols with the sideloading scripts.

## Features

* Automated installation of required dependencies
* Step-by-step iOS device pairing instructions via `libimobiledevice`
* Direct IPA sideloading from Android to iOS
* Setup mechanism for Minecraft Java Edition launchers on iOS

## Requirements

* An iOS device (iPhone/iPad)
* An Android device with OTG support
* A USB-C to Lightning or USB-C to USB-C cable
* Termux and Termux:API installed from F-Droid

## Environment Setup

First, grant Termux storage permissions and install the necessary base packages.

```bash
termux-setup-storage
pkg update && pkg upgrade -y
pkg install wget git tsu -y

```

Download and execute the sideload setup script to install all required packages.

```bash
wget [https://github.com/AmarKherala/termux-sideload/releases/download/script/setup.sh](https://github.com/AmarKherala/termux-sideload/releases/download/script/setup.sh)
chmod +x setup.sh
./setup.sh

```

## Connecting and Pairing

Connect your Android device to your iOS device using the cable. Ensure the Android device is acting as the USB Host (File Transfer / MTP mode).

Start the USB multiplexer daemon.

```bash
usbmuxd

```

Initiate the pairing sequence.

```bash
idevicepair pair

```

A "Trust This Computer" prompt will appear on your iOS device. Accept it and enter your device passcode. Run the pairing command one more time to finalize the process.

```bash
idevicepair pair

```

## Sideloading Launchers

Once the devices are successfully paired, you can download and sideload your desired IPA files.

For Amethyst Launcher:

```bash
wget [AMETHYST_IPA_DOWNLOAD_LINK] -O Amethyst.ipa
sideloader install Amethyst.ipa -i

```

For PojavLauncher:

```bash
wget [POJAVLAUNCHER_IPA_DOWNLOAD_LINK] -O PojavLauncher.ipa
sideloader install PojavLauncher.ipa -i

```

The tool will prompt you for your Apple ID and password to sign the IPA file. Enter your credentials, and the application will be installed on your iOS device.

## Troubleshooting

* **Connection Issues:** If `usbmuxd` fails or the trust prompt does not appear, your Android device might be restricting low-level USB access. Ensure you are running Termux with appropriate permissions or root access if necessary.
* **Host Mode Failure:** Try flipping the ends of the Type-C cable or use a USB-A OTG adapter on the Android side to force the host connection.
* **Apple ID Errors:** If the sideloading tool rejects your Apple ID, generate an App-Specific Password from the Apple ID website and use that instead of your main password.

## Credits & License

This project utilizes sideloading scripts from AmarKherala/termux-sideload. Licensed under the MIT License.

```

```
