# Sudo user

## In Debian based system add current user to sudo group

```
$ sudo usermod -aG sudo ${USER}
```

## In RHEL based system add current user to wheel group

```
$ sudo usermod -aG wheel ${USER}
```
