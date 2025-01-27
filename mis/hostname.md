# change machine hostname

## Return machine hostname

```
hosname
echo $HOSTNAME
```

## Change hostname to FTP
```
hostnamectl set-hostname FTP
```
Now `hostnmae` show FTP

## Change hostes file 

Add new record for new hostname

```
$ cat /etc/hosts
127.0.0.1    FTP
```


Machine IP addresses except **lo**

```
hostname -I
```
