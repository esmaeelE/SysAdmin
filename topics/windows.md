# Windows as shitware OS

When we need windows os use this method

* Install windows 11 lite (Windows 11 Enterprise LTSC)
* Disable intenet
* Remote blot/sharewares
* Disable update and definder

* create news user and enable rdp for only that user
[prevent other users to remote login](https://superuser.com/a/1018827/1787481)

* enable internet
* Install [ssh server](https://github.com/esmaeelE/SysAdmin/blob/main/topics/ssh.md#windows)
* run ansible to destination
* install desired application
* other configs

# Time

As Microshaft windows allways make troubles to users and especially system administrators.
We must implement a way to force windows time stop and don't sync with any ntp servers.

command prompt

```tzutil /s "UTC"```

Show

```time /t```

Set

```time 10:20```

Also turn off any online and automatic method and time shifting set it to UTC


# Configs
## Programs

- firefox
- mobaexterm
- notepad++

## Install wsl, make development environment

* Install windows 11 lite
* microsoft store get latest version of ubuntu 24.04 LTS, vscode
* set user, password
* install Mobaexterm
* vscode, Mobaexter connect to wsl
* create ssh keypair, copy to remote hosts
* 

