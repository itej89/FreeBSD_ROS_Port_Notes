# Some useful commands for developers

* Get all system #defines
```sh
echo "" | cc -E -dM -xc -
```

* Find connected tty devices
```sh
sysctl -a | grep -i tty
```

* Node based sysctl search 
```
sysctl dev.uslcom
```


* clang address scruitinizer 
```sh
-g -fsanitize=address -fno-omit-frame-pointer
```
 
* Shows all dependacies
```sh
ldd *.so
```

* shows only direct dependancies
```sh
readelf -d *.so
```