```
sudo apt update
sudo apt install certbot python3-certbot-nginx -y
```
```
Test Manual Renewal

sudo certbot renew --dry-run
```


Set Up a Cron Job for Auto-Renewal
```
sudo crontab -e

0 0,12 * * * /usr/bin/certbot renew --quiet --nginx
```


```
sudo certbot certonly --nginx -d web.goodtogostore.com
```


Verify Renewal and Reloading
```
sudo certbot renew --quiet --nginx
```

```
server {
    server_name web.domain.com;

    location / {
        auth_basic "Restricted Access";
        auth_basic_user_file /etc/nginx/.htpasswd;
        proxy_pass http://localhost:4000;
    }

    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/web.domain.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/web.domain.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
}

server {
    if ($host = web.domain.com) {
        return 301 https://$host$request_uri;
    } # managed by Certbot

    server_name web.domain.com;
    listen 80;
    return 404; # managed by Certbot
}
```
