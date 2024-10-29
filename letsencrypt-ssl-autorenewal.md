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


server {
    server_name snbx-g45prod.vmaker.com;

    location / {
        auth_basic "Restricted Access";
        auth_basic_user_file /etc/nginx/.htpasswd;
        proxy_pass http://localhost:5556;
    }

    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/snbx-g45prod.vmaker.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/snbx-g45prod.vmaker.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
}

server {
    if ($host = snbx-g45prod.vmaker.com) {
        return 301 https://$host$request_uri;
    } # managed by Certbot

    server_name snbx-g45prod.vmaker.com;
    listen 80;
    return 404; # managed by Certbot
}





sudo apt update
sudo apt install certbot python3-certbot-nginx -y

Test Manual Renewal



Set Up a Cron Job for Auto-Renewal
sudo crontab -e
0 0,12 * * * /usr/bin/certbot renew --quiet --nginx


sudo certbot certonly --nginx -d web.goodtogostore.com


Verify Renewal and Reloading

sudo certbot renew --quiet --nginx


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


sudo certbot --nginx -d goodtogostore.com 


```
sudo certbot certificates
Saving debug log to /var/log/letsencrypt/letsencrypt.log

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Found the following certs:
  Certificate Name: goodtogostore.com
    Serial Number: 4a55048b8b5f40fef32ce5fff8459351a30
    Key Type: ECDSA
    Domains: goodtogostore.com
    Expiry Date: 2025-01-27 14:34:06+00:00 (VALID: 89 days)
    Certificate Path: /etc/letsencrypt/live/goodtogostore.com/fullchain.pem
    Private Key Path: /etc/letsencrypt/live/goodtogostore.com/privkey.pem
  Certificate Name: web.goodtogostore.com
    Serial Number: 3a6b68a72ddcee5b2420b6040b8cb648827
    Key Type: ECDSA
    Domains: goodtogostore.com web.goodtogostore.com
    Expiry Date: 2025-01-27 14:28:22+00:00 (VALID: 89 days)
    Certificate Path: /etc/letsencrypt/live/web.goodtogostore.com/fullchain.pem
    Private Key Path: /etc/letsencrypt/live/web.goodtogostore.com/privkey.pem
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

```
sudo certbot renew --dry-run
Saving debug log to /var/log/letsencrypt/letsencrypt.log

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Processing /etc/letsencrypt/renewal/goodtogostore.com.conf
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Account registered.
Simulating renewal of an existing certificate for goodtogostore.com

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Processing /etc/letsencrypt/renewal/web.goodtogostore.com.conf
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Simulating renewal of an existing certificate for goodtogostore.com and web.goodtogostore.com

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Congratulations, all simulated renewals succeeded: 
  /etc/letsencrypt/live/goodtogostore.com/fullchain.pem (success)
  /etc/letsencrypt/live/web.goodtogostore.com/fullchain.pem (success)
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```
