# system time

```
date
timedatectl
tzdata
cat /etc/timezone
zdump
zdump -v Asia/Tehran
```
linux maintain time in tzdata package. update it.
```
$ sudo apt install tzdata
```
or manual install https://packages.ubuntu.com/jammy/tzdata
```
$ sudo apt install ./tzdata.deb
```

windows mange timezones with windows update patches. [bad](https://serverfault.com/a/1100527/1023046)

