```
$ cat /etc/docker/daemon.json 
{
        "registry-mirrors": ["https://registry.docker.ir"]

}

systemctl daemon-reload
systemctl restart docker
```


