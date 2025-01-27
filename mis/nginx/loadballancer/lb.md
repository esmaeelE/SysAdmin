# Nginx loadbalancer

**nginx.conf**

```
events {
        worker_connections 1024;
}
http {
        upstream backend {
                # ip_hash;
                # server backend_1:8000;
                # server backend_1:9000;
                # server backend_2:9000 weight=3;
                server 1.0.77.10:9000;
                server 1.0.77.20:9000;
        }
    
        server {
                listen 80;
                location / {
                        proxy_set_header Host $host;
                        proxy_set_header X-Real-IP $remote_addr;
                        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                        # proxy_pass http://backend:8000;
                        proxy_pass http://backend;
                }

        }
}

```

## Dockerize nginx

**docker-compose.yml**

```
version: '3'
services:
  #   backend_1:
  #     image: python-django-app:latest
  #     ports:
  #       - "9000"
  # 
  #   backend_2:
  #     image: python-django-app:latest
  #     ports:
  #       - "9000"
  # 

  nginx:
    image: nginx
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    ports:
      - "8080:80"
```



