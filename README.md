![alt_test](components/wine.png)

# Xow64-Wine
Wine-wow64-staging + box64 presetuped for termux-glibc (aarch64)

# Current status:
Wine version: 10.2-30-ge1b8e7f6ec7 (staging)

Box64 version: 0.3.3 (dev)

# Installation:
Make sure if wget is installed
```
pkg install wget openssl
```

Install xow64
```
cd $HOME && rm -rf ~/xow64 && wget https://github.com/ar37-rs/xow64-wine/raw/refs/heads/main/xow64 && chmod +x ~/xow64
```

and then
```
~/xow64 install
```
# Usage (on desktop environment such xfce4 native termux-x11):
[(Read for more info to setup xfce4 desktop for native termux-x11)](https://github.com/ar37-rs/xfce4-termux)

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

# OpenGL/ES drivers:
Using newer build of virgl (virpipe) driver

(Universal android 10+ with vulkan 1.1+ GPU supported only)
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

Fix virgl color/visual problems on d3d9+ (Direct X) apps/games
```
~/xow64 vgl-cfg=d3d
```

Reconfigure virgl for OpenGL/ES apps/games
```
~/xow64 vgl-cfg=gl
```

Using panfork/panfrost driver for some specific supported

Mali-G310+ (G610, G710..) series with kernel 5.10+
```
~/xow64 driver=panfrost
```
For panfork driver only make sure termux-x11 is using DRI3 and BOX64_MMAP32 have to be deactivated in order to work

(disabling MMAP32 causes wine to run slower when running 32-bit games/apps)
```
~/xow64 mmap32=false
```
and then install panfrost driver [from here](https://github.com/Saikatsaha1996/mesa-Panfrost-G610/releases/tag/mesa-23.0.0-devel-20240109_armhf_arm64)

Switch back using default OpenGL driver using any default
preconfigured termux gl drivers including virgl (if any)
```
~/xow64 driver=default
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

Install box64 v0.3.2 (available box64 v0.3.0 to v0.3.3)
```
~/xow64 box64=0.3.2
```

Update box64 to newer version (v0.3.3)
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

Update angle-android using the newer version (for android 9+ only)
```
~/xow64 update-angle
```

Update dxvk-proton (vkd3d)
```
~/xow64 update-vkd3d
```

Update patch
```
~/xow64 update-patch
```

Uninstall (remove) xow64-wine
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

* If there's problem when installing xow64, make sure the latest correct termux app version is installed from here:
  https://github.com/termux/termux-app/releases

* tested using termux app v0.119.0-beta.1
  
# Addtional guide:
* Using cnc-ddraw (visit link below)
  
    https://github.com/FunkyFr3sh/cnc-ddraw
  
# Other links for credits (3rd parties):
[InputBridge Wiki](https://search.brave.com/search?q=InputBrige%20exagear%20wiki&source=web)

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


