# SSH


## Force ask password instead of using public key authentication

```
ssh -o PubkeyAuthentication=no -o PreferredAuthentications=password
```

Use public/private key pairs instead of plaintext password

Create new keypair in a machine
```
ssh-keygen
```
Generate these two files `id_ed25519.pub, id_ed25519` inside `.ssh/` directory.

From now we can copy our public key to destination server and use these type of authentication instead of username and password.
The destination server match our public key with private and give access.


### Use in Github
copy `id_ed25519.pub` and place to github ssh-keys section.
then run `ssh -T git@github.com` to confirm access.


# Fail2ban
Prevent brute force ssh password logins.

## debian 12
```
$ sudo apt install fail2ban
$ sudo systemctl restart fail2ban.server
```
 
 
 /etc/fail2ban/jail.local
```
[sshd]
backend=systemd
enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
```


