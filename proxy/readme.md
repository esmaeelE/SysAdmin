# Proxy

Proxy meaning

Usage

## simple implementation

Suppose a situation we have a service on server which is works on localhost(127.0.0.1) on port: 8000

To expose it and be accessible from outside we must use a proxy.
This proxy will listen on port 8080 on all interfaces and redirects all traffic to 127.0.0.1:8000

### simpleproxy

Debian have a good package can be userd here.
    
    sudo apt install simpleproxy
    sudo simpleproxy -L 0.0.0.0:8080 -R 127.0.0.1:8000

### Nginx

This work can be done with nginx reverse proxy


```/etc/nginx/conf.d/local_proxy.conf```

    server {
        listen 80;
        server_name webfig.ir;
    
        location / {
            proxy_pass http://127.0.0.1:8080/;
        }
    }    

    # check nginx config
    sudo nginx -t
    # restart nginx service to take effect changes
    systemctl restart nginx    