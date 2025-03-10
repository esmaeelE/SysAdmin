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
# For ipv6
$ curl ident.me
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

### ping and ssh

```
ping6  hostIP
ssh -6 user@hostIP
```


### DIG

```
$ dig A google.com AAAA google.com +short 
;; Warning, extra type option
2a00:1450:400e:802::200e
142.250.179.206
```


### IPV6 check after set

#### Run python server 

**server.py**

```
import socket
  
UDP_IP = "::" # = equal to 0.0.0.0 u in IPv4
UDP_PORT = 5005

sock = socket.socket(socket.AF_INET6, # Internet
                                                socket.SOCK_DGRAM) # UDP
sock.bind((UDP_IP, UDP_PORT))
print("start server ... listen on port 5005, ")
while True:
        data, addr = sock.recvfrom(1024) # buffer size is 1024 bytes
        print ("received message:", data)
```

**client.py**

```
import socket

UDP_IP = "2a05:b40:0:559::9"  # Here is server IPv6 address
UDP_PORT = 5005
MESSAGE = b"Hello, World!"

print ("UDP target IP:", UDP_IP)
print ("UDP target port:", UDP_PORT)
print ("message:", MESSAGE)

sock = socket.socket(socket.AF_INET6, # Internet
					socket.SOCK_DGRAM) # UDP
sock.sendto(MESSAGE, (UDP_IP, UDP_PORT))

```

# Ubuntu

Ubuntu use netplan for IP config, and have some issue.
Use `nmtui` instead.

* [Ubuntu netplan](https://ostechnix.com/configure-static-ip-address-ubuntu/)

```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens18:
      dhcp4: no
      addresses:
        - 192.168.1.22/24
        - 192.168.1.23/24
        - 192.168.1.24/24
      routes:
        - to: default
          via: 192.168.1.101
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
```

Ubuntu netplan
```
$ sudo netplan try
$ sudo netplan apply
$ sudo reboot
```

# IP command 

Delete route and new one

```
ip -4 route flush label "enp*"
ip a add 192.168.10.7/24 dev enp4s0
```

```
ip route del default
ip r add 192.168.1.0/24 dev ep4s0
```
