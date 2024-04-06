# Create a user with specific read/write permissions

## sftp

Use `sshd server` which also provides a sftp server(secure ftp) on ssh channel

```
sudo apt list openssh-server
```
By default sshd serve on port 22

## Config new server 

```
/etc/ssh/sshd_config

#Subsystem      sftp    /usr/lib/openssh/sftp-server
Subsystem       sftp    internal-sftp

# Example of overriding settings on a per-user basis
Match group sftp_users
        X11Forwarding no
        AllowTcpForwarding no
        ChrootDirectory /home/user/shared_directory
        PermitTTY no # dont access to this user open ssh session
        ForceCommand internal-sftp
```

Also Match section support User attribute.
We can have multiple users, each one can connect and use specific directory in our ftp server.

Or we can grant specific user to use sftp server
```
Match user ftpuser
        X11Forwarding no
        AllowTcpForwarding no
        ChrootDirectory /home/user/shared_directory
        PermitTTY no # dont access to this user open ssh session
        ForceCommand internal-sftp
```

## Restart openssh to take effect 

```
systemctl restart sshd
```

## User config

```
groupadd sftp_users

adduser uat

usermod -G sftp_users uat
```

# Connect 

* `sftp uat@192.168.1.10`
* filezila GUI application
* gftp GUI application

# Change ownership

```
chown -R uat /data
```

## Its better using facl to grant access to specific user without changing ownership of files

### install package

```
apt install acl
```

## Set permission

```
setfacl -R -m u:uat:rwx mis/
setfacl -R -m u:uat:rwx pics/ 
setfacl -R -m u:uat:rwx data/
```

## Reference

https://askubuntu.com/a/809562/678872

https://aventistech.com/kb/configure-sftp-server-in-debian/


## Hints
In above config under the sshd file if ChrooDirectory is a /root path it must be owned by root from the begining of path.
Unfortunately somebody change it to another user so I have hard time to get it to work.

For example 

```
        ChrootDirectory /root/backend/somedir/
```

