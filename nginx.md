1. 下载`nginx` [http://nginx.org/en/download.html](http://nginx.org/en/download.html)
2. 解压`nginx`
3. 修改配置文件`nginx.conf`

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

#log_format main '$remote_addr - $remote_user [$time_local] "$request" '
# '$status $body_bytes_sent "$http_referer" '
# '"$http_user_agent" "$http_x_forwarded_for"';

#access_log logs/access.log main;

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
#error_page 404 /404.html;

# redirect server error pages to the static page /50x.html
#
error_page 500 502 503 504 /50x.html;
location = /50x.html {
root html;
}

# proxy the PHP scripts to Apache listening on 127.0.0.1:80
#
#location ~ \.php$ {
# proxy_pass http://127.0.0.1;
#}

# pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
#
#location ~ \.php$ {
# root html;
# fastcgi_pass 127.0.0.1:9000;
# fastcgi_index index.php;
# fastcgi_param SCRIPT_FILENAME /scripts$fastcgi_script_name;
# include fastcgi_params;
#}

# deny access to .htaccess files, if Apache's document root
# concurs with nginx's one
#
#location ~ /\.ht {
# deny all;
#}
}


# another virtual host using mix of IP-, name-, and port-based configuration
#
#server {
# listen 8000;
# listen somename:8080;
# server_name somename alias another.alias;

# location / {
# root html;
# index index.html index.htm;
# }
#}


# HTTPS server
#
#server {
# listen 443 ssl;
# server_name localhost;

# ssl_certificate cert.pem;
# ssl_certificate_key cert.key;

# ssl_session_cache shared:SSL:1m;
# ssl_session_timeout 5m;

# ssl_ciphers HIGH:!aNULL:!MD5;
# ssl_prefer_server_ciphers on;

# location / {
# root html;
# index index.html index.htm;
# }
#}
include servers/*;
}
```



