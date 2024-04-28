# Use nginx authentication 

## Nginx config

```
server {
    listen 9999 default_server;
    #    listen [::]:80 default_server;# ipv6only=on;
    server_name kibana;
    location / {
        proxy_pass http://127.0.0.1:5601;
        auth_basic "Restricted Content";
        auth_basic_user_file /etc/nginx/.htpasswd;
    }
}
```
Use above config file for kibana backend server

### Explanation
In this example
we have one http server which is listen on **port: 9999**
the server name is: **kibana**
when a request received for address: **/** it redirects to: **http://127.0.0.1:5601**
this is the backend server: **kibana**

But nginx enabled basic authentication (username, passphrase).
So any **unauthorized** access request will be **Restricted**.


We must create username password with ht and place it on
`/etc/nginx/.htpasswd`


```
$ sudo apt install apache2-utils
$ htpasswd -c .htpasswd user
$ sudo mv .htpasswd
```

#### Check connectivity
```
$ curl -u user:pass http://ip:9999
```


