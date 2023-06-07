# Enabling devices and permissions in FreeBSD

#### Enabling FTDI device:
* add below line to /boot/loader.conf
```sh
uftdi_load="YES"
```

#### enabling /dev/input/js0 linux standard device:

* add below line to /boot/loader.conf
```sh
cuse_load="YES"
```
* add below line to /etc/rc.conf
```sh
webcamd_enable="YES"
```
* check for JoyStick packages:
```sh
pkg install sdl2
pkg install libevdev
pkg install evdev-proto //for Ros joy node compilation
```
* add user to "webcamd" group


#### Create a new group for devices 
* Create group 'wavdev'
```sh
pw groupadd wavdev
```

* Add devfs rules in /etc/devfs.rules --> create if not present

```
[wavdevrules=10]
add path 'usb/*' mode 0660 group wavdev 
add path 'ugen*' mode 0660 group wavdev 
add path 'ttyu*' mode 0660 group wavdev 
```

* Enable rules in /etc/rc.conf as below
```sh
devfs_system_ruleset="wavdevrules"
```

#### Groups Handinlg:
* Add user to group wavdev
```sh
pw group mod wavdev -m tej 
```

```sh
* Important:**********************************
:for tty access add user to "dialer" group
pw group mod dialer -m $USER 
*******************************************/
```

* delete user from group wavdev
```sh
pw group mod wavdev -d tej 
```

* list available groups in FreeBSD
```sh
awk -F":" '{print $1}' /etc/passwd
awk -F":" '{print $1}' /etc/group
```

* check user groups
```sh
id userID
```