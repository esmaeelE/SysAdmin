# Unix users

List all users

```
cat /etc/passwd
```

Create user
```
$ sudo adduser alice
```

login
```
$ su -l alice
```

Expire user, one day after epoch time: Jan 1 1970
```
my_user="alice"
sudo usermod -L -e 1 ${my_user}
```
Now User cant loging to system becaused his/her password is expired long time ago.



Remove user
```
sudo deluser alice
```
Not remove user home directory that resides in `/home/alice`
If you want to delete run manually `rm -rf /home/alice` with caution.


lock/unlock password for user
```
passwd -l alice 
passwd -u alice 
passwd --status alice
```

Example
```
$ sudo passwd --status alice 
alice L 2024-03-07 0 99999 7 -1
```

Now unlock alice password
```
$ sudo passwd -u alice
passwd: password changed.
$ sudo passwd --status alice 
alice P 2024-03-07 0 99999 7 -1
```

From now alice can login to system with her password

check with below command
```
su -l alice 
```




