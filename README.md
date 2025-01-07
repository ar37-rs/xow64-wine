# Xow64-Wine
Wine-10-rc4-wow64-staging + box64 presetuped for termux-glibc (aarch64).
# Installation:
```
cd && pkg install wget 
rm -rf ~/xow64 && wget https://github.com/ar37-rs/xow64-wine/releases/download/latest/xow64 && chmod +x ~/xow64
```
and then
```
~/xow64 install-deps && ~/xow64 update
```
# Usage (on desktop environment such xfce4 native termux-x11):
[(Read for more info to setup xfce4 desktop for native termux-x11)](https://github.com/ar37-rs/xfce4-termux)

Launch winecfg
```
~/xow64 winecfg
```
Launch specific *.exe
```
~/xow64 app_name.exe
```
## Additional usage:
Quit wine or terminate all wine related process.
```
~/xow64 q
```
Using vulkan panfrost driver (only for specific supported Mali-G series with kernel 5.10+)
```
~/xow64 vk-panfrost
```
Using vulkan llvmpipe (Universal CPUs)
```
~/xow64 vk-llvmpipe
```
Switch back using default vulkan driver (If any)
```
~/xow64 vk-default
```
Install box64-0.3.3
```
~/xow64 box64-0.3.3
```
Install box64-0.3.1
```
~/xow64 box64-0.3.1
```
Install box64-0.3.0
```
~/xow64 box64-0.3.0
```
Update wine
```
~/xow64 update-wine
```
Update patch
```
~/xow64 update-patch
```

# Note:
* Using virtual controller, install InputBrige

    [From here](https://github.com/ar37-rs/xow64-wine/releases/download/latest/InputBridge_v0.1.9.9.apk)

    and start command in desktop termux terminal:
    ```
    ~/xow64 s
    ```
    and then `StartInputBridge.cmd` from wine start menu (desktop mode) before launching any game.
* If experiencing any emulation issue, try using different version of box64 above.
* Using virgl for Wine3d (Direct3D) support (Universal supported GPUs)

    [(Read for more info on how to use virgl on termux)](https://github.com/ar37-rs/virgl-angle-termux)
    
# Links for addtional guides and manual setup:
* dxvk:

    https://github.com/doitsujin/dxvk
* wined3d:

    https://fdossena.com/?p=wined3d/index.frag

# Other links for credits (3rd parties):

https://www.winehq.org

https://github.com/termux

https://github.com/termux/termux-x11

https://github.com/termux-pacman/glibc-packages

https://github.com/ptitSeb/box64

https://github.com/airidosas252/Wine-Builds

https://github.com/Kron4ek/Wine-Builds

[InputBridge Wiki](https://search.brave.com/search?q=InputBrige%20exagear%20wiki&source=web)
