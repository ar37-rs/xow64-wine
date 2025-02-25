# Installation:

# Run inside termux terminal
Install dependencies (for virgl/virpipe driver):
```
pkg install wget openssl which virglrenderer-android virglrenderer angle-android
```
[or here for latest virgl-angle setup](https://github.com/ar37-rs/virgl-angle-termux)

# Install desktop for proot termux
[Read for more info on how to setup termux-desktops with ubuntu-proot](https://github.com/LinuxDroidMaster/Termux-Desktops/blob/main/Documentation/proot/ubuntu_proot.md)

# Run inside proot desktop terminal
Install dependencies and box64

for debian/ubuntu based distro
```
sudo apt update && sudo apt install wget tar openssl gnu-which gpg && sudo wget https://ryanfortner.github.io/box86-debs/box86.list -O /etc/apt/sources.list.d/box86.list && sudo wget -qO- https://ryanfortner.github.io/box86-debs/KEY.gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/box86-debs-archive-keyring.gpg && sudo apt update
sudo apt install box64
```

Install xow64 (the same as for termux glibc)
```
cd $HOME && rm -rf ~/xow64 && wget https://github.com/ar37-rs/xow64-wine/raw/refs/heads/main/xow64 && chmod +x ~/xow64
```

Activate proot mode
```
~/xow64 proot=true
```

Install xow64 components
```
~/xow64 install
```
# Usage:
Basic usage is the same as inside desktop environment native termux.

[for more info read the usage from here](https://github.com/ar37-rs/xow64-wine/blob/main/README.md)

# Note:
* Deactivate proot mode
   ```
   ~/xow64 proot=false
   ```
* Fix virgl-angle vulkan support for some devices

   [such encountered on this issue](https://github.com/ar37-rs/virgl-angle-termux/issues/1)

   run command inside termux terminal
   ```
   pkg remove *icd-swrast && pkg install vulkan-loader-generic wget openssl && cd && rm -rf ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && wget https://github.com/ar37-rs/virgl-angle-termux/releases/download/latest/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && dpkg -i ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb
   ```
* If there's problem when installing, make sure the latest correct termux app version is installed from here:
   https://github.com/termux/termux-app/releases

* Tested using termux app v0.119.0-beta.1

* Fix for android 12+ devices with [Process completed (signal 9) - press Enter] issue (using adb):

   For Android 12L & Android 13+
   ```
   adb shell "settings put global settings_enable_monitor_phantom_procs false"
   ```

   For Android 12
   ```
   adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent; /system/bin/device_config put activity_manager max_phantom_processes 2147483647"
   ```

   and then restart/reboot device.

   [Read more from here](https://ivonblog.com/en-us/posts/fix-termux-signal9-error/) or [here](https://github.com/termux/termux-app/issues/2366)
