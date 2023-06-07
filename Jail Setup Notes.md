# Command history to setup Jails in FreeBSD

```sh
export DESTDIR=/usr/jails/rosreq
```

```sh
export DESTRELEASE=12.0-RELEASE

export DESTARCH=`uname -m`

export SOURCEURL=http://ftp.freebsd.org/pub/FreeBSD/releases/$DESTARCH/$DESTRELEASE/

for set in base ports; do fetch $SOURCEURL/$set.txz ; done
```

```sh
tar -xf base.txz -C $DESTDIR

touch jail.conf

vi jail.conf
   
	  rosreq {
	    host.hostname = roswav;           # Hostname
	    ip4.addr = 192.168.1.135;         # IP address of the jail
	    allow.raw_sockets=1;
	    path ="/usr/jails/rosreq";  
	    mount.devfs;                      # Path to the jail
	    exec.start = "/bin/sh /etc/rc";            # Start command
	    exec.stop = "/bin/sh /etc/rc.shutdown";    # Stop command
	}
```

* copy /etc/resolv.conf to /usr/jails/rosreq/etc

```sh		
service jail onestart rosreq

service jail onestop rosreq
```

* Jail management
```sh
jls

jexec JAIL_ID /bin/tcsh
```

* To remove jail directory run inside the directory: 
```sh
	chflags -R noschg *
```
	   
