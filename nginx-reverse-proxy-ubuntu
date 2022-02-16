server {
    listen 80;
    listen 443 ssl;
    listen [::]:443 ssl;
    ssl_certificate /etc/nginx/ssl/public.crt;
    ssl_certificate_key  /etc/nginx/ssl/private.key;
    server_name compvisionminio.eastus.cloudapp.azure.com;
    access_log /var/log/nginx/access.log;
    error_log /var/log/nginx/error.log;

location / {
    proxy_pass https://localhost:9001;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_redirect https://compvisionminio.eastus.cloudapp.azure.com  https://compvisionminio.eastus.cloudapp.azure.com;
    }

}
# stpes

unlink /etc/nginx/sites-available/default

cd /etc/nginx/sites-available/

touch sonarqube.conf

vim sonarqube.conf

   server {
    listen 80;
    listen 443 ssl;
    listen [::]:443 ssl;
    ssl_certificate /etc/nginx/ssl/public.crt;
    ssl_certificate_key  /etc/nginx/ssl/private.key;
    server_name sonar.tendercuts.in;
    access_log /var/log/nginx/access.log;
    error_log /var/log/nginx/error.log;

location / {
    proxy_pass https://localhost:9000;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_redirect http://sonar.tendercuts.in  https://sonar.tendercuts.in;
    }
}

save and exit

sudo nginx -t

sudo systemctl restart nginx
