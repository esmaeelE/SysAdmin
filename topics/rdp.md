# Run a RDP server on GNU/Linux 

* Install Debian netinstall iso.

* Install required extra packages. update and upgrade

* Install desktop environmet

```
$ sudo apt install tasksel
$ sudo tasksel install xfce-desktop
```

* Install RDP server

```
$ sudo systemctl status xrdp
$ sudo apt install xrdp
$ sudo systemctl status xrdp
$ sudo adduser xrdp ssl-cert  
$ ss -tulpen 
$ hostname -I 
```

* Connect to RDP server with RDP client like Reminna.
