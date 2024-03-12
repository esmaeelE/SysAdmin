# Transfer files in server 

## scp — OpenSSH secure file copy

To copy files between servers over ssh protocol we can use `scp`

scp work for files transmission between local and remote servers 

Also a great feature of scp is the ability to transefer files remote to remote

But the middle server must access to both sides.

## rsync, scp replacement

scp depricates, so we must use rsync for this task.
But rsync not support remote to remote transmission.

### How to transfer files between two remote hosts without access from middle server to destination end

Now consider this situation
I want to download some important files from a remote backup server.

Local machine only can access to middle server called **manage_node**
Local machine can initiate ssh session to manage_node and we can not autorize to ssh back to local machine.
So in this circumstance doing scp from **manage_node** between two remote servers.

A simple solution is to use `sshfs` ability.

SSHFS can mount a remote file system localy on current machine.

```
$ sudo apt install sshfs
```

We can mount remote address in **manage_node** and copy mounted files to Local machine.

```
mkdir mount_point
sudo sshfs maria_bk:/var/archive/ mount_point/
```

Now we can download them from Local mahine

```
scp manage_node:~/mount_point/*.tar.gz .
```

---

### rsync 

To using **rsync** both sides must have rsync program.
So run this command to ensure it installed.

```
$ sudo apt install rsync
```

Now we can run rsync instead of scp

```
$ rsync -LvzP manage_node:~/mount_point/lpic*.gz .
```

SpeedUP

https://stackoverflow.com/questions/24058544/speed-up-rsync-with-simultaneous-concurrent-file-transfers/72480364#72480364


Python simple ftp server provides resume download but http server not.

