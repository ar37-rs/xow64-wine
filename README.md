# Xow64-Wine
wine-10-wow64-staging + box64 presetuped for termux-glibc (aarch64).
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
Start wine on desktop terminal (desktop mode)
```
~/xow64 s
```
Launch winecfg
```
~/xow64 winecfg
```
Launch specific *.exe
```
~/xow64 app_name.exe
```
## Additional usage:
Quite wine or terminate all wine related process.
```
~/xow64 q
```
Updating box64
```
~/xow64 update-box64
```
Updating wine
```
~/xow64 update-wine
```
Updating patch
```
~/xow64 update-patch
```
Install InputBrige for virtual controller:

[From here](https://github.com/ar37-rs/xow64-wine/releases/download/latest/InputBridge_v0.1.9.9.apk)
# Credits and 3rd parties:

https://www.winehq.org

https://github.com/termux

https://github.com/termux-pacman/glibc-packages

https://github.com/ptitSeb/box64

https://github.com/airidosas252/Wine-Builds

https://github.com/Kron4ek/Wine-Builds

[InputBridge Wiki](https://search.brave.com/search?q=InputBrige%20exagear%20wiki&source=web)
