- Install Packages:

 `pacstrap -K /mnt base linux linux-firmware base-devel networkmanager nvidia wget htop vi vim grub git openssh`

- Create fstab:

`genfstab -U /mnt >> /mnt/etc/fstab`

- Chroot 

`arch-chroot /mnt`

- Timezone

`ln -sf /usr/share/zoneinfo/Europe/Belgrade /etc/localtime`

- Edit locale stuff (uncomment GB instead of US to have the 24h time format when using 'date')

`Edit the file /etc/locale.gen and uncomment en_GB.UTF-8 UTF-8`

`locale-gen`

`echo "LANG=en_GB.UTF-8" >> /etc/locale.conf`

- Change the root password

`passwd`

- Install grub

`grub-install --target=i386-pc /dev/sdc`

`grub-mkconfig -o /boot/grub/grub.cfg`

- Enable NetworkManager

`systemctl enable NetworkManager && systemctl start NetworkManager`

- Add my user

`useradd --create-home --groups wheel --shell /bin/bash vlada`

- Sudo config

`visudo` and uncomment the line that says wheel group members can use passwordless sudo

- Kill pc speaker

`rmmod pcskpr` 

`vim /etc/modprobe.d/turn-off-pc-speaker.conf` 

`blacklist pcspkr`

- Grub theme

https://github.com/lfelipe1501/Atomic-GRUB2-Theme

https://github.com/jacksaur/Gorgeous-GRUB

- Bash prompt generator with fancy colors

PS1="\[\e[38;5;243m\]\u\[\e[38;5;245m\]@\[\e[38;5;249m\]\h \[\e[38;5;254m\]\w \[\033[0m\]$ "

https://robotmoon.com/bash-prompt-generator/


- Install X

`sudo pacman -Syu xorg xorg-xinit`


- Install dwm:

```
mkdir ~/bin
cd ~/bin
git clone git://git.suckless.org/dwm
cd dwm
make
make install
```

* Install st

```
sudo pacman -Syu xclip  #Needed for copying to clipboard
cd ~/bin
git clone git://git.suckless.org/st
cd st
make
make install
```

* Install dmenu

```
cd ~/bin
git clone git://git.suckless.org/dmenu
cd dmenu
make
make install
```

* Install scroll

```
cd ~/bin
git clone git://git.suckless.org/scroll
cd scroll
make
make install
```


* Create `~/.xinitrc` and add:

`exec dwm`


* Stop monitor from turning off

```
cat /etc/X11/xorg.conf.d/10-stop-monitor-sleep.conf
Section "Monitor"
    Identifier "LVDS0"
    Option "DPMS" "false"
EndSection

Section "ServerFlags"
    Option "StandbyTime" "0"
    Option "SuspendTime" "0"
    Option "OffTime" "0"
    Option "BlankTime" "0"
EndSection

Section "ServerLayout"
    Identifier "ServerLayout0"
EndSection
```

* Fonts (maybe)

`sudo pacman -Syu noto-fonts`
