# dotfiles

Config files for
* window-manager: dwm (sometimes bspwm)
* compositor: picom (forked compton)
* status-bar: none/yabar
* windows switcher: rofi/dmenu
* terminal: terminator/cool-retro-term
* music: pulseaudio (and `pacmd` for runtime configuration of pulseaudio)
* shell: fish(framework: oh my fish)
* web-browser: chromium/vivaldi (plugins: 
                                 adblock plus, 
                                 vimium, 
                                 https everywhere)
* text-editor: vim
* file-manager: ranger
* image-viewer: nomacs/ sxiv
* virtualization: (virtualbox, 
                   vagrant, 
                   minikube, 
                   docker, 
                   docker-compose, 
                   docker-machine, 
                   kubectl, 
                   kubectx, 
                   kubens, 
                   kubeadm, 
                   helm3, (plugins: secrets))
* infra-as-code: terraform
* screenshots: shutter
* movies: vlc
* photos: sxiv
* music: x



Usefull commands idk how much will put here, whatever comes to mind:


pulseaudio [-k|--start]


pacmd [list-sinks|set-default-sink] -> set speakers/headset as sound output


bluetoothctl (devices|list|scan-on|scan-off|trust|pair|connect|disconnect] 


arandr/xrandr -> setup monitors


xset r rate 300 50 -> key refresh/speed


neofetch/uname -a -> system info


figlet Colgateplax -> cool tool to write stuff in terminal


### First time setup Git on new system

```
git config --global user.email ""
git config --global user.email ""
git config credential.helper store -> then git push and enter creds
```

### Add new user

```
useradd -m -G users <user>
usermod -aG wheel <user>
```

### Change shell on the system, 3 ways

```
vim /etc/passwd (change shell at the end of the line)
chsh --shell (whereis <shell>) <user>
usermod --shell (whereis <shell>) <user>
```

### Connect to wifi and enable on the start

```
wifi-menu
nmtui
pacman -Sy networkmanager
systemctl enable NetworkManager
systemctl start NetworkManager
```


### Interesting packages
---

```
community/tlp 1.3.1-2
    Linux Advanced Power Management
Packages (3) hdparm-9.58-3  usbutils-012-2  tlp-1.3.1-2
```

---

```
/bluez 5.54-2 [installed]
    Daemons for the bluetooth protocol stack
```

---

```
extra/bluez-hid2hci 5.54-2
    Put HID proxying bluetooth HCI's into HCI mode
Packages (1) bluez-hid2hci-5.54-2
```

---

```
extra/bluez-utils 5.54-2
    Development and debugging utilities for the bluetooth protocol stack
Packages (1) bluez-utils-5.54-2
```

---

```
ty/sxiv 26-1
    Simple X Image Viewer
Packages (1) sxiv-26-1
```

---

```
community/blueman 2.1.3-1
    GTK+ Bluetooth Manager
Packages (1) blueman-2.1.3-1
```

---
