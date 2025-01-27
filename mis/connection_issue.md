# When we cant connect to remote server

## ssh not works

* list open port
```
ss -tulpen
```
* ssh service
```
systemctl status ssh
```

* check firewall
```
ufw status
```

* check raw ports
```
nc -l 9999
nc -nvz 1.2.3.4 9999
python -m http.server
```
