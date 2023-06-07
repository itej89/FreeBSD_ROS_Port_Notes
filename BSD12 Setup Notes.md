# FreeBSD 12.1 : Sytem Setup steps

### Enabling nvidia driver and xorg
```sh
Pkg install nvidia-driver
```

* #### In /etc/rc.conf
  * Kld_list=“linux nvidia nvidia-modeset”
  * dbus_enable=“YES”
  * hald_enable=“YES”

```sh
pkg install Xorg

pkg install nvidia-xconfig

Run nvidia-xconfig

pkg install gdm
```
* In /etc/rc.conf
  * gdm_enable=“YES”



#### FOR XFCE: 
```sh
pkg install xfce
echo ". /usr/local/etc/xdg/xfce4/xinitrc" > ~/.xinitrc
```

#### For Gnome
```sh
pkg install gnome3 gnome-desktop
```
* In /etc/rc.conf
  * gnome_enable=“YES”




####  Make user sudoer
pkg install sudo
visudo
append : <user_name> ALL=(ALL) ALL



#### Create safe alias for rm:
* Download trash-cli from git
* install trash-cli by ruinning
```sh
  python setup.py install in trash-cli directory
```
* touch ~/.bashrc
* add below line to ~/.bashrc 
```sh
  alias rm="trash" 
```

