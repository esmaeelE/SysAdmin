# Simple http website with nginx webserver

```
$ sudo apt install nginx
```

# Copy config file
mywebsite

```
server {
    listen 80;
    server_name mywebsite.com www.mywebsite.com;

    root /var/www/mywebsite;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

```
sudo cp mywebsite /etc/nginx/sites-available/
```

---

# Check config is OK
```
sudo nginx -t
```

# Enable wesite
```
sudo ln -s /etc/nginx/sites-available/mywebsite /etc/nginx/sites-enabled/
```

# Unlink default website
```
sudo unlink /etc/nginx/sites-enabled/default
```

# Reload nginx service 
```
sudo systemctl reload nginx
```


# check website is UP?
```
ss -tulpen
curl http://localhost:80
```




# Nginx


## nginx file server

```
cat /etc/nginx/nginx.conf 
user www-data;
worker_processes auto;
pid /run/nginx.pid;
error_log /var/log/nginx/error.log;
include /etc/nginx/modules-enabled/*.conf;

events {
	worker_connections 768;
	# multi_accept on;
}

http {
	server {
	  listen *:9999;
	  server_name 127.0.0.1;
	
	  root /var/db/backup_dir;
	  autoindex on;
	}
}
```
Reload setting

```
sudo nginx -T
sudo systemctl restart nginx.service
```

Now file server will server on **IP:9999**


