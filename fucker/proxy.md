# Set proxy

As fucking docker company restricted IRAN we must use proxy to access their images.

    $ cat /etc/systemd/system/docker.service.d/https-proxy.conf
    [Service]
    Environment="HTTP_PROXY=http://192.168.5.35:8119"
    Environment="HTTPS_PROXY=http://192.168.5.35:8119"
    Environment="NO_PROXY=localhost,127.0.0.1,docker-registry.example.com,.corp"
    

    $ sudo systemctl daemon-reload
    $ sudo systemctl restart docker

