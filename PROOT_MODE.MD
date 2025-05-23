# Installation:

### Install dependencies (for virgl/virpipe driver):

#### (Run inside termux terminal)
```
pkg install wget which virglrenderer-android virglrenderer angle-android
```
[or here for latest virgl-angle setup](https://github.com/ar37-rs/virgl-angle)

### Install desktop for proot termux
[Read for more info on how to setup termux-desktops with ubuntu-proot](https://github.com/LinuxDroidMaster/Termux-Desktops/blob/main/Documentation/proot/ubuntu_proot.md)

#### (Run inside proot desktop terminal)

for debian/ubuntu based distro
```
sudo apt install box64 wget tar gnu-which
```
or install devel version
```
sudo apt update && sudo apt install wget tar gnu-which gpg && sudo wget https://ryanfortner.github.io/box86-debs/box86.list -O /etc/apt/sources.list.d/box86.list && sudo wget -qO- https://ryanfortner.github.io/box86-debs/KEY.gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/box86-debs-archive-keyring.gpg && sudo apt update
sudo apt install box64
```

for arch/manjaro based distro
```
sudo pacman -S box64 wget tar which
```
or install devel version
```
sudo pacman -S wget tar which && cd $HOME && sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
yay -S box64-git
```

for RHEL/fedora based distro
```
sudo dnf install wget tar which
sudo dnf install box64 box64-data
```

### Install xow64 (Run inside proot desktop terminal)
```
cd $HOME && rm -rf ~/xow64 && wget https://github.com/ar37-rs/xow64-wine/raw/refs/heads/main/proot_mode/xow64 && chmod +x ~/xow64
```

### Activate proot mode
```
~/xow64 proot=true
```

### Install xow64 components
```
~/xow64 install
```
# Usage:
Basic usage is the same as inside desktop environment native termux.

[for more info read the usage from here](https://github.com/ar37-rs/xow64-wine)

# Note:
* Deactivate proot mode
   ```
   ~/xow64 proot=false
   ```
* Fix virgl-angle vulkan support for some devices

   [such encountered on this issue](https://github.com/ar37-rs/virgl-angle/issues/1)

   run command inside termux terminal
   ```
   pkg remove *icd-swrast && pkg install vulkan-loader-generic wget && cd && rm -rf ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && wget https://github.com/ar37-rs/virgl-angle/releases/download/latest/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && dpkg -i ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb
   ```
* If there's problem when installing, make sure the latest correct termux app version is installed from here:
   https://github.com/termux/termux-app/releases

* Tested using termux app v0.119.0-beta.1

* Fix for some android 12+ devices with [Process completed (signal 9) - ...] issue using adb:
   ```
   adb shell "settings put global settings_enable_monitor_phantom_procs false"
   ```
   and set max_phantom_processes as well
   ```
   adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
   adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"
   ```
   and then restart/reboot device.

   [Read more from here](https://ivonblog.com/en-us/posts/fix-termux-signal9-error/) or [here](https://github.com/termux/termux-app/issues/2366)

* Uninstall box64-git on arch linux based distro
   ```
   yay -Rns box64-git
   ```
