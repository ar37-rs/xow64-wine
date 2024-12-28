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
# Usage (on desktop environment such xfce4,lxqt native termux-x11):
Start wine on desktop terminal (desktop mode)
```
~/xow64 s
```
Launch specific *.exe
```
~/xow64 your_app_name.exe
```
Quite wine or terminate all wine related process.
```
~/xow64 q
```

# Credits and 3rd parties:

https://www.winehq.org

https://github.com/termux

https://github.com/termux-pacman/glibc-packages

https://github.com/ptitSeb/box64

https://github.com/airidosas252/Wine-Builds

https://github.com/Kron4ek/Wine-Builds
