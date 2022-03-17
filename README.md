# AAB Installer

This is a set of processes that allows to install an AAB into a device or emulator using adb and bundle-tool. If running on a macOS device with Homebrew, this process will attempt to install bundle-tool if it is not already installed.

## Usage

#### Simple usage (debug keystore):

```sh
./install-aab --bundle my-app.aab
```

#### Signed APK usage:

```sh
./install-aab --bundle ~/Downloads/app-fw-release.aab \
--key ~/.android/debug.keystore \
--key-password android \
--alias androiddebugkey \
--alias-password android
```

## Requirements

#### Non-recoverable

- adb

#### Recoverable (if Homebrew is installed)

- Java
- bundletool

----

This script is inspired on [JonnyBurger/install-aab](https://github.com/JonnyBurger/install-aab). This version was created to be able to run without NVM/Node in the machine and allow sign the generated APK.