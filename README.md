
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
* [Termux](https://github.com/termux/termux-app/releases/download/v0.118.3/termux-app_v0.118.3+github-debug_arm64-v8a.apk) and [Termux-api](https://github.com/termux/termux-api/releases/download/v0.53.0/termux-api-app_v0.53.0+github.debug.apk) 

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


## Installing SideStore
Connect your phone with the iDevice using any cable you got, open termux and run usbmuxd. If it the iDevice shows a popup asking for permission click trust or whatever it says to give it perms. Now it should say something like usbmuxd running. Click Ctrl+c to stop.

Now you can sideload! grab the sidestore ipa by running:
```
wget https://github.com/SideStore/SideStore/releases/download/0.6.2/SideStore.ipa && sideloader install SideStore.ipa -i
```
It will ask you for your Apple ID and password, enter them and the ipa will start installing on your iDevive.

The tool will prompt you for your Apple ID and password to sign the application. Enter your credentials, and SideStore will be installed on your iOS device.

Transfer the pairing file (<UDID>.plist) you generated earlier from your Android device to your iOS device.

Open the SideStore app.

It will ask for a pairing file. Select the .plist file you just transferred.

Sign in with your Apple ID and an App-Specific Password to finalize the setup. You can now use SideStore directly on your device.
## Troubleshooting

* **Connection Issues:** If `usbmuxd` fails or the trust prompt does not appear, your Android device might be restricting low-level USB access. Ensure you are running Termux with appropriate permissions or root access if necessary.
* **Host Mode Failure:** Try flipping the ends of the Type-C cable or use a USB-A OTG adapter on the Android side to force the host connection.
* **Apple ID Errors:** If the sideloading tool rejects your Apple ID, generate an App-Specific Password from the Apple ID website and use that instead of your main password.

## Credits & License

This project utilizes sideloading scripts from AmarKherala/termux-sideload. Licensed under the MIT License.

```

```
