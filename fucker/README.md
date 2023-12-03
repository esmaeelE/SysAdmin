If you are lived in restricted locations like IRAN, docker not work and may generate related message.

Here is the message

> Since Docker is a US company, we must comply with US export control regulations. In an effort to comply with these, we now block all IP addresses that are located in Cuba, Iran, North Korea, Republic of Crimea, Sudan, and Syria. If you are not in one of these cities, countries, or regions and are blocked, please reach out to https://support.docker.com\n\n\n". See 'docker run --help
    
As fucking docker company restricted IRAN we have two options.

## Use Mirror registry

Using mirror instead of default docker registry 

    $ cat /etc/docker/daemon.json 
    {
            "registry-mirrors": ["https://registry.docker.ir"]
    }
    
    systemctl daemon-reload
    systemctl restart docker
        
If its not work use proxy for docker 

## Set proxy


    $ cat /etc/systemd/system/docker.service.d/https-proxy.conf
    [Service]
    Environment="HTTP_PROXY=http://192.168.5.35:8119"
    Environment="HTTPS_PROXY=http://192.168.5.35:8119"
    Environment="NO_PROXY=localhost,127.0.0.1,docker-registry.example.com,.corp"
    

    $ sudo systemctl daemon-reload
    $ sudo systemctl restart docker



