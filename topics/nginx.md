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


