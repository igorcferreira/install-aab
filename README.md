# AAB Installer

This is a set of processes that allows to install an AAB into a device or emulator using adb and bundle-tool. If running on a macOS device with Homebrew, this process will attempt to install bundle-tool if it is not already installed.

## Installation

install-aab is available as a Homebrew Formula. To install it:

```sh
$ brew tap igorcferreira/tap
$ brew install install-aab
```

## Usage

#### Simple usage (debug keystore):

To install an AAB into the connected device, signing the generated APK with the device debug keystore, just run:

```sh
./install-aab --bundle my-app.aab
```

#### Signed APK usage:

If you need to sign the generate APK with a specific keystore, please use the extended configuration:

```sh
./install-aab --bundle ~/Downloads/app-fw-release.aab \
--key ~/.android/debug.keystore \
--key-password android \
--alias androiddebugkey \
--alias-password android
```

### Multiple devices connected:

If you have multiple devices connected to the machine, please specify the device id with the parameter `--device-id`. If the device id is not set, the install will fail.

```sh
./install-aab --bundle my-app.aab --device-id emulator-5554
```

### Full help text

```
Usage:
install-aab -b /path/to/app.aab

Parameters:
    --bundle         -b : Path to the AAB file
    --key            -k : Keystore that will be used to sign the exported APK
    --key-password   -kp: Keystore password
    --alias          -a : Key alias
    --alias-password -ap: Alias password (optional)
    --help           -h : Prints this helper message
    --device-id         : Id of the device where the APK will be installed (optional)

Keystore:
    If all the key configuration is passed, the provided keystore will be used to sign the application. Otherwise, debug keystore is used.
    If no Alias password is provided, the key password is repeated in the alias.
```

## Requirements

- adb
- Java
- bundletool

----

This script is inspired on [JonnyBurger/install-aab](https://github.com/JonnyBurger/install-aab). This version was created to be able to run without NVM/Node in the machine and allow sign the generated APK.