---
layout: page
title: Nginx
permalink: /nginx/
---

## Host non-Ghost webpage with Nginx and Ghost

Edit `/etc/nginx/conf.d/default.conf`

```bash

server {
    listen 80;
    server_name karloespiritu.com;
    root /var/www/ghost;

    location / {
        try_files $uri @proxy;
    }

    location @proxy {
        proxy_set_header   X-Real-IP $remote_addr;
        proxy_set_header   Host      $http_host;
        proxy_pass         http://127.0.0.1:2368;
    }

    location /static/ {
            alias /var/www/static/;
    }
}

```