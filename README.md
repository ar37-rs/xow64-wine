![alt_test](components/wine.png)

# Xow64-Wine
Wine-wow64-staging + box64 presetuped for termux-glibc (aarch64)

with minimal dependencies as possible and install only what needed.

### Current state:
Wine 10.2-193-g6e6334d4293 (Staging)

Box64 v0.3.3 1bf4851 (Dev)

# Installation:
[(Using xow64 on proot read the tutorial from here)](https://github.com/ar37-rs/xow64-wine/blob/main/PROOT_MODE.MD)
### Install desktop for native termux
[(Read for more info on how to setup xfce4)](https://github.com/ar37-rs/xfce4-termux)

or

[(using termux-desktop from here)](https://github.com/sabamdarif/termux-desktop/tree/main)

### Make sure if wget is installed
```
pkg install wget openssl
```

### Install xow64
```
cd $HOME && rm -rf ~/xow64 && wget https://github.com/ar37-rs/xow64-wine/raw/refs/heads/main/xow64 && chmod +x ~/xow64
```

### and then
```
~/xow64 install
```

# Usage (inside desktop environment native termux):
Install different version of wine (default is 10.2)

(currently wine 9.18 and 10.2 staging are available) 
```
~/xow64 wine=9.18
```

Switch back to default or specific wine version
```
~/xow64 wine=default
```

Run and check wine version
```
~/xow64 r --version
```

Run winecfg
```
~/xow64 r winecfg
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

Run any specific *.exe
```
~/xow64 r app_name.exe
```
or run any *.exe with any specific path
```
cd ~/'.to/Prog Files/app/path' && ~/xow64 r app_name.exe
```

Launch wine in windows desktop mode, configure desktop size like so

(or any standard windows screen size)
```
~/xow64 desk-size 1024x768
```
and then simply start using
```
~/xow64 s
```

Quit wine or terminate all wine related process
```
~/xow64 q
```

# Wine D3D for OpenGL/ES drivers:
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
~/xow64 vgl-compat=3.3
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

Make sure termux-x11 is using DRI3

if experiencing driver error when using panfrost driver, try disable BOX64_MMAP32

(disabling MMAP32 causes wine to run slightly slower when running 32-bit games/apps)
```
~/xow64 mmap32=false
```

Switch back using default OpenGL driver using any default
preconfigured termux gl drivers including virgl (if any)
```
~/xow64 driver=default
```

Re-enable BOX64_MMAP
```
~/xow64 mmap32=true
```
# Vulkan drivers:
Using vulkan llvmpipe (fo Universal CPUs)
```
~/xow64 vk=lvp
```

Using vulkan turnip driver (for Adreno GPUs)
```
~/xow64 vk=turnip
```

Using vulkan radeonsi driver (for AMD based GPUs such Xclipse)
```
~/xow64 vk=radeon
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

Disable dxvk-proton (vkd3d)
```
~/xow64 vkd3d=false
```

Using dxvk-glasync-proton for more pleasant experience (supported on vulkan the same as dxvk-proton)
```
~/xow64 vkd3d-async=true
```

Disable dxvk-glasync-proton (vkd3d)
```
~/xow64 vkd3d-async=false
```

# Additional usage:
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

Install box64 v0.3.2 (available box64 v0.3.0 to v0.3.3 glibc only)
```
~/xow64 box64=0.3.2
```

Update box64 to newer version (v0.3.3 glibc only)
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

Update angle-android using the newer version (for glibc and android 9+ only)
```
~/xow64 update-angle
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

Remove specific installed version of wine (e.g: 9.18 )
```
~/xow64 wine-remove=9.18
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

* If experiencing any emulation issue, try using different version of box64 and drivers available above accordingly.

* If there's problem when installing xow64, make sure the latest correct termux app version is installed.

  (tested using [termux-app-v0.119.0-beta.1](https://github.com/termux/termux-app/releases))

# Addtional guide:
* Using cnc-ddraw:

    [read more from here](https://github.com/FunkyFr3sh/cnc-ddraw)

# Additional troubleshoot
* Fix virgl-angle vulkan support for some devices

   [such encountered on this issue](https://github.com/ar37-rs/virgl-angle/issues/1)
   ```
   pkg remove *icd-swrast && pkg install vulkan-loader-generic wget openssl && cd && rm -rf ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && wget https://github.com/ar37-rs/virgl-angle/releases/download/latest/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb && dpkg -i ~/mesa-vulkan-icd-wrapper_25.0.0-1_aarch64.deb
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

https://github.com/termux-pacman/glibc-packages

https://github.com/doitsujin/dxvk

https://gitlab.com/Ph42oN/dxvk-gplasync

https://github.com/HansKristian-Work/vkd3d-proton

https://github.com/erfan2255/EnvMapping


