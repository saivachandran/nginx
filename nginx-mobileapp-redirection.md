server {
  listen 80;
  server_name chan.sai.in;
  return 301 https://$host$request_uri;
}
 
server {
  listen 443 ssl;
  server_name chan.sai.in;
  set $mobile_rewrite do_not_perform;

  # this regex string is actually much longer to match more mobile devices
  if ($http_user_agent ~* '(iPhone|iPod|iPad|Android|BlackBerry|webOS|Windows Phone)') {
     set $mobile_rewrite perform;
  }
 
  ssl_certificate    /root/ssl/crt.crt;
  ssl_certificate_key  /root/ssl/server.key;

location / {
	if ($mobile_rewrite = perform) {
           return 301 https://hc-staging-app.web.app$request_uri;
       }
#    proxy_set_header        Host $host:$server_port;
#    proxy_set_header        X-Real-IP $remote_addr;
#    proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
#    proxy_set_header        X-Forwarded-Proto $scheme;
    proxy_pass              http://127.0.0.1:4000;
#    proxy_http_version 1.1;
#    proxy_request_buffering off;
#    proxy_buffering off;
    add_header 'X-SSH-Endpoint' 'chan.sai.in:50022' always;
  }
}
