# SSR Config for Angular and Node on separate server with SSL

- Change the config file content in ``sudo nano /etc/nginx/sites-enabled/website.conf`` to below.

```
server {
    listen       80;
    server_name  website.com;
    rewrite ^ https://www.website.com$request_uri? permanent;
}

server {
    listen 443 ssl http2;

    ssl_certificate /etc/letsencrypt/live/website.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/website.com/privkey.pem;
    ssl_stapling on;

    server_name  website.com;

     location / {
            proxy_set_header   X-Real-IP $remote_addr;
            proxy_set_header   Host      $http_host;
            proxy_pass         http://127.0.0.1:4000;
        }
}
```

- Restart or Reload the nginx Server.
- SSL Certificate can be obtained from LetsEncrypt with the following steps
1. ``sudo add-apt-repository ppa:certbot/certbot``  
2. ``sudo apt install python-certbot-nginx``
3. ``sudo systemctl reload nginx``
4. ``sudo ufw allow 'Nginx Full'``
5. ``sudo certbot --nginx -d website.com -d www.website.com``
6. ``sudo certbot renew --dry-run`` (For Auto Renewal)


- for Detailed info goto [Digital Ocean Docs]

[//]: # 
[Digital Ocean Docs]: <https://www.keycdn.com/support/nginx-virtual-host>
