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
        ForceCommand internal-sftp
```

Also Match section support User attribute.
We can have multiple users, each one can connect and use specific directory in our ftp server.


## Restart server to take effect 

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


