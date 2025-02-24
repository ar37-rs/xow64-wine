# Installation:
Dependencies and box64

for debian/ubuntu based distro
```
sudo apt update && sudo apt install wget openssl gnu-which gpg && sudo wget https://ryanfortner.github.io/box86-debs/box86.list -O /etc/apt/sources.list.d/box86.list && sudo wget -qO- https://ryanfortner.github.io/box86-debs/KEY.gpg | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/box86-debs-archive-keyring.gpg && sudo apt update
sudo apt install box64
```

Install xow64
```
cd $HOME && rm -rf ~/xow64 && wget https://github.com/ar37-rs/xow64-wine/raw/refs/heads/main/xow64 && chmod +x ~/xow64
```

Activate proot node
```
~/xow64 proot=true
```

Install xow64 components
```
~/xow64 install
```
# Usage
Basic usage is the same as inside termux glibc

for proot mode run commands inside proot desktop terminal

# Note
* Deactivate proot node
   ```
   ~/xow64 proot=false
   ```
