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
```
Restart
```
systemctl restart fail2ban
```


Source

https://superuser.com/a/1830273/1787481
