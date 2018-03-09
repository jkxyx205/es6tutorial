1. 下载`nginx` [http://nginx.org/en/download.html](http://nginx.org/en/download.html)
2. 解压`nginx`
3. 修改配置文件`nginx.conf`

**参考设置**

```conf
#user nobody;
worker_processes 1;

#error_log logs/error.log;
#error_log logs/error.log notice;
#error_log logs/error.log info;

#pid logs/nginx.pid;

events {
worker_connections 1024;
}


http {
include mime.types;
client_max_body_size 200M;
fastcgi_buffers 8 128k;
default_type application/octet-stream;

sendfile on;
#tcp_nopush on;

#keepalive_timeout 0;
keepalive_timeout 65;

#gzip on;
autoindex on;
server {
listen 8000;
server_name devyean.com;
location / {
proxy_pass http://127.0.0.1:8080/;
client_body_buffer_size 50m;
}
}

server {
listen 8000;
#server_name *.devyean.com;
server_name ~^(www\.)?(.+)$;
proxy_set_header Host $host;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header REMOTE-HOST $remote_addr;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
location / {
proxy_pass http://127.0.0.1:8080/portal/;
}
}
server {
listen 3000;
server_name localhost;

#charset koi8-r;

#access_log logs/host.access.log main;

location /tpl-css {
alias /Users/rick/yodean/workspace2/template/dist/tpl-css;
index index.html index.htm;
}

location /static {
alias /Users/rick/yodean/workspace2/portal/sitemgt/src/main/webapp/static;
index index.html index.htm;
}

location / {
root /Users/rick/jkxyx205/tmp;
index index.html index.htm;
}
include servers/*;
}
```

启动`nginx`

```bash
    nginx
```



