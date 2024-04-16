# Run a RDP server on GNU/Linux 

* Install Debian netinstall iso.

* Install required extra packages. update and upgrade

* Install desktop environmet

```
$ sudo apt install tasksel
$ sudo tasksel install xfce-desktop
```

* Install RDP server

```
$ sudo apt install xrdp
$ sudo systemctl status xrdp
$ sudo adduser xrdp ssl-cert  
$ ss -tulpen 
$ hostname -I 
```

* Connect to RDP server with RDP client like Reminna. port 3389


# Run a RDP server on Windows 11


```
################################################
# Window Manage RDP serice commands ############
################################################

# Enable RDP sevice on windows
Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections" -value 0

# Check is enabled?
Get-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -name "fDenyTSConnections"

# Store in variabl, zero means enable
$rdpEnabled = 
  0 -eq (Get-ItemPropertyValue 'HKLM:\SYSTEM\CurrentControlSet\Control\Terminal Server' fDenyTSConnections)

$rdpSessionsPresent = 
  quser.exe | Select-String -Quiet '\brdp-'

# Get RDP port
Get-ItemProperty -Path 'HKLM:\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "PortNumber"


## Change port to solve account lock due to rdp spoofing when expose service to Internet ##

$portvalue = 4493

Set-ItemProperty -Path 'HKLM:\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "PortNumber" -Value $portvalue

New-NetFirewallRule -DisplayName 'RDPPORTLatest-UDP-In' -Profile 'Public' -Direction Inbound -Action Allow -Protocol UDP -LocalPort $portvalue
New-NetFirewallRule -DisplayName 'RDPPORTLatest-TCP-In' -Profile 'Public' -Direction Inbound -Action Allow -Protocol TCP -LocalPort $portvalue

# pause

```
