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
$ sudo systemctl restart fail2ban
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


## Windows


Run powershell in administrator mode

```
Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
# Install the OpenSSH Client
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0

# Install the OpenSSH Server
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0

# Start the sshd service
Start-Service sshd

# OPTIONAL but recommended:
Set-Service -Name sshd -StartupType 'Automatic'

# Confirm the Firewall rule is configured. It should be created automatically by setup. Run the following to verify
if (!(Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue | Select-Object Name, Enabled)) {
    Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, creating it..."
    New-NetFirewallRule -Name 'OpenSSH-Server-In-TCP' -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
} else {
    Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' has been created and exists."
}
```
[windows openssh server](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=powershell)
