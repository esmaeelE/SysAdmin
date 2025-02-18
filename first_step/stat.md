# First steps after connect to Server
## General 
* Find its IP: `hostname -I`
* Check disk storage capacity: `lsblk -f`
* connected user: `w`

## If server become slow

* sar command
```
$ apt install sysstat
```

* **cpu**: `sar 1`
* **network**: `sar -n TCP 1`
* **block device**: `sar -b 1`


* Other commands
```
top, htop, atop
uname -a, -m
uptime, load average 1, 5, and 15 minutes
iotop
GPU: nvtop
s-tui, stress-ng, stress
```

## Network
- iftop
- 

## Sources
* [MortezaBashsiz youtube videos](https://github.com/MortezaBashsiz)
