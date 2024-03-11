# Debian

### /etc/network/interface
```
iface enp0s5  inet static
 address 192.168.2.236
 netmask 255.255.255.0
 gateway 192.168.2.254
 dns-domain sweet.home
 dns-nameservers 192.168.2.254 1.1.1.1 8.8.8.8
```

### Public IP

```
$ curl ifconfig.co/json
```


Set both IPv4 and IPv6 for one Interface

```
auto eth1
iface eth1 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    gateway 192.168.1.1

iface eth1 inet6 static
    address 2001:470:28:5b2::1
    netmask 64
```



```
