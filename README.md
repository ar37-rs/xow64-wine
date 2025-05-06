# XoW64-Wine
Wine-WoW64 + Box64 presetuped for termux glibc/proot (aarch64)

<img align="center" src="components/wine.png">

with minimal dependencies as possible and install only what needed.

# Latest state
## Wine
Version: 10.7

## Box64
Version: 0.3.5

# Installation:
[(Using xow64 on proot read the tutorial from here)](https://github.com/ar37-rs/xow64-wine/blob/main/PROOT_MODE.MD)

[(Using xow64 on native/bionic read more from here)](https://github.com/ar37-rs/xaw64-wine)
### Install desktop for native termux
[(Read for more info on how to setup xfce4)](https://github.com/ar37-rs/xfce4-termux)

or

[(using termux-desktop from here)](https://github.com/sabamdarif/termux-desktop/tree/main)

### Make sure if wget is installed
```
pkg install wget
```

### Install xow64 (Bash script only)
```
cd $HOME && rm -rf ~/xow64 && wget https://github.com/ar37-rs/xow64-wine/raw/refs/heads/main/xow64 && chmod +x ~/xow64
```

### and then
```
~/xow64 install
```

# Usage (inside desktop environment native termux):
Switch to different version of wine

Other available versions:
```
9.18-staging
10.7-stable
```

e.g: Wine 9.18 staging (if experiencing crash gecko iexplore or website based apps, recommended using this version)
```
~/xow64 wine=9.18-staging
```

Switch back to default version (10.7-staging)
```
~/xow64 wine=default
```

Run wine config
```
~/xow64 r winecfg
```

Run registry editor (regedit)
```
~/xow64 r regedit
```

Run any specific *.exe
```
~/xow64 r app_name.exe
```
or run any *.exe with any specific path
```
cd ~/'.to/Prog Files/app/path' && ~/xow64 r app_name.exe
```

Launch GPU Caps (test OpenGL and Vulkan)
```
~/xow64 gpucaps
```

Launch TestD3D (D3D9)
```
~/xow64 testd3d
```

Launch CubeMap (test EnvMapping D3D9)
```
~/xow64 cubemap
```

Launch SphereMap (test EnvMapping D3D9)
```
~/xow64 spheremap
```

Launch wine in windows desktop mode, configure desktop size like so

(or any standard windows screen size)
```
~/xow64 desk-size=1024x768
```
and then simply start using
```
~/xow64 s
```

Quit wine or terminate all wine related process
```
~/xow64 q
```

# OpenGL/ES drivers:
Using newer build of virgl (virpipe) driver

(Universal android 9+ with vulkan 1.1+ GPU supported only)

[(Read more for virgl-angle additional usage from here)](https://github.com/ar37-rs/virgl-angle)
```
~/xow64 driver=virpipe
```

Using virpipe angle driver
```
~/xow64 vgl-use=angle
```

Using virpipe native android driver (less stable might using older version of virgl)
```
~/xow64 vgl-use=android
```

Using virgl 4.3COMPAT profile (default is OpenGL 4.1COMPAT)

support OpenGL 2.1, 3.2, 3.3, 4.1 and 4.3 with COMPAT
```
~/xow64 vgl-compat=4.3
```

Switch back virgl to default COMPAT profile.
```
~/xow64 vgl-compat=4.1
```

Fix virgl color/visual problems on d3d9+ (Direct X) apps/games
```
~/xow64 vgl-cfg=d3d
```

Reconfigure virgl for OpenGL/ES apps/games
```
~/xow64 vgl-cfg=gl
```

Using panfork/panfrost driver for some specific supported

Mali-G310+ (G610, G710..) series
```
~/xow64 driver=panfrost
```
install panfrost driver for glibc [from here](https://github.com/Saikatsaha1996/mesa-Panfrost-G610/releases/tag/mesa-23.0.0-devel-20240109_armhf_arm64) (not required for proot mode)

make sure termux-x11 is using DRI3 and if experiencing driver error when using panfrost driver

try disable ```BOX64_MMAP32``` environment (if not error, just skip)

disabling ```MMAP32``` causes wine to run slightly slower (when running 32-bit games/apps)
```
~/xow64 env-add BOX64_MMAP32=0
```

Check the environment variable
```
~/xow64 env-info
```

Re-enable BOX64_MMAP
```
~/xow64 env-remove BOX64_MMAP32=0
```

Switch back using default OpenGL driver using any default
preconfigured termux gl drivers including virgl (if any)
```
~/xow64 driver=default
```

# Direct 3D support for OpenGL drivers:
Using WineD3D version 3.21
```
~/xow64 wined3d=3.21
```
and then (for wined3d 3.21 only: changing ```deviceId``` back to default is required if previously changed to something else)
```
~xow64 device=default
```

Using WineD3D version 4.21
```
~/xow64 wined3d=4.21
```

Using WineD3D version 9.2 (fix graphical glitches for some devices on wine 10.x and highly recommended for virgl stability and performance)
```
~/xow64 wined3d=9.2
```

Switch back using default builtin WineD3D version
```
~/xow64 wined3d=default
```

# Vulkan drivers:
Using vulkan llvmpipe, extremely slow for testing only (Universal CPUs)
```
~/xow64 vk=lvp
```

Using vulkan turnip driver (for Adreno GPUs)
```
~/xow64 vk=turnip
```

Switch back using default vulkan driver (if any)
```
~/xow64 vk=default
```

# Direct 3D support for vulkan drivers:
Using dxvk-proton (supported on vulkan llvmpipe and any supported GPU driver)  
```
~/xow64 vkd3d=true
```

Using dxvk-glasync-proton for more pleasant experience (supported on vulkan the same as dxvk-proton)
```
~/xow64 vkd3d-async=true
```

Using dxvk-v1-proton (support for some legacy devices with vulkan 1.1)
```
~/xow64 vkd3d-v1=true
```

Disable dxvk-proton, dxvk-glasync and dxvk-v1-proton
```
~/xow64 vkd3d=false
```

If experiencing error on some specific vulkan drivers use the older supported version [from here](https://github.com/doitsujin/dxvk) or use modified dxvk version [from here](https://github.com/pythonlover02/DXVK-Sarek)

# Additional usage:
Adding any custom environment variable (e.g: disabling ```MMAP32```)
```
~/xow64 env-add BOX64_MMAP32=0
```

Check list of the added custom environment variables
```
~/xow64 env-info
```

Remove the added custom environemnt variable
```
~/xow64 env-remove BOX64_MMAP32=0
```

Reset custom environment variables to default
```
~/xow64 env-default
```

Using custom graphic card deviceId and vendorId, some games require the ```deviceId``` to be available on the system

use custom GPU code name (GeForce GTX 950M)
```
~/xow64 device=gtx950m
```
or (GeForce GTX 980)
```
~/xow64 device=gtx980
```
or (UHD Graphics 630)
```
~/xow64 device=uhd630
```
Swich back to default ```deviceId```
```
~/xow64 device=default
```

Enable winedlloverride for cnc-ddraw
```
~/xow64 cnc-ddraw=true
```

Disable winedlloverride for cnc-ddraw
```
~/xow64 cnc-ddraw=false
```

Disable wine debugger (for stability)
```
~/xow64 debug=false
```

Re-enable wine debugger
```
~/xow64 debug=true
```

Using custom ```WINEPREFIX``` to the new specific path (default is ```.xow64_wine```)

(after changing ```WINEPREFIX``` make sure to reconfigure most of things such update-patch, renabling vkd3d and .etc if previously being enabled)

e.g: change to ```.wine``` 
```
~/xow64 WINEPREFIX=.wine
```

Install box64 v0.3.3 (available box64 v0.3.0 to v0.3.5 glibc only)
```
~/xow64 box64=0.3.3
```

Update box64 to newer version (v0.3.5 glibc only)
```
~/xow64 update-box64
```

Update wine
```
~/xow64 update-wine
```

Update graphics drivers
```
~/xow64 update-drivers
```

Update angle-android (android 9+ only)
```
~/xow64 update-angle
```

Update virglrenderer (android 10+ only)
```
~/xow64 update-virgl
```

Update dxvk-proton (vkd3d)
```
~/xow64 update-vkd3d
```

Update dxvk-proton async (vkd3d)

```
~/xow64 update-vkd3d-async
```

Update patch
```
~/xow64 update-patch
```

Remove specific installed version of wine (e.g: 10.4-staging)
```
~/xow64 wine-remove=10.4-staging
```

Remove specific installed version of box64 (e.g: 0.3.2)
```
~/xow64 box64-remove=0.3.2
```

Uninstall (remove) xow64-wine completely
```
~/xow64 remove-all
```

# Note:
* Using virtual controller, install InputBrige

    [From here](https://github.com/ar37-rs/xow64-wine/releases/download/latest/InputBridge_v0.1.9.9.apk)

    and start command in desktop termux terminal
    ```
    ~/xow64 s
    ```
    and then `StartIB.cmd` from wine start menu (desktop mode) before launching any game, then open InputBridge app on android device and then start configuring control buttons as need.

* If experiencing any emulation issue for specific app/game
  
    try using different version of box64, wine, configuration (especially box64 environment variables) and drivers available above accordingly.

* If there's problem when installing xow64, make sure the latest correct termux app version is installed.

  (tested using [termux-app-v0.119.0-beta.1](https://github.com/termux/termux-app/releases))

# Addtional guide:
* Using cnc-ddraw:

    [read more from here](https://github.com/FunkyFr3sh/cnc-ddraw)

# Additional troubleshoot:
* Fix virgl-angle vulkan support for some devices

   [such encountered on this issue](https://github.com/ar37-rs/virgl-angle/issues/1)
   ```
   pkg remove *icd-swrast && pkg install vulkan-loader-generic wget && cd && rm -rf ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && wget https://github.com/ar37-rs/virgl-angle/releases/download/latest/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && dpkg -i ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb
   ```
   
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
  [read more for more info from here](https://ivonblog.com/en-us/posts/fix-termux-signal9-error/) or [here](https://github.com/termux/termux-app/issues/2366)

# Other links for credits (3rd parties):
[InputBridge Wiki](https://search.brave.com/search?q=InputBrige%20exagear%20wiki&source=web)

[XinputBridge Wiki](https://github.com/Ilan12346-maya/XinputBridge)

https://www.mesa3d.org

https://github.com/termux

https://github.com/termux/termux-x11
 
https://github.com/ptitSeb/box64

https://github.com/wine-staging/wine-staging

https://github.com/airidosas252/Wine-Builds

https://github.com/brunodev85/winlator

https://github.com/termux-pacman/glibc-packages

https://github.com/doitsujin/dxvk

https://gitlab.com/Ph42oN/dxvk-gplasync

https://github.com/HansKristian-Work/vkd3d-proton

https://github.com/erfan2255/EnvMapping


