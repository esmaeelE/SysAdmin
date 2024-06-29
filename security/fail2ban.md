# Fail2ban package to protect bruteforce attack

## Debian 12
```
apt install fail2ban
```
Add this config
```
/etc/fail2ban/jail.local
[sshd]
backend=systemd
enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
# initial ban time:
bantime = 1h
# incremental banning:
bantime.increment = true
# default factor (causes increment - 1h -> 1d 2d 4d 8d 16d 32d ...):
bantime.factor = 24
```
Restart
```
systemctl restart fail2ban
```


Source

https://superuser.com/a/1830273/1787481
