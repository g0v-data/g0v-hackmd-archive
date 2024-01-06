# GCP 基本環境建置

## PHP
```
1. sudo apt update

2. sudo apt upgrade

3. sudo apt install ca-certificates apt-transport-https 

4. wget -q https://packages.sury.org/php/apt.gpg -O- | sudo apt-key add -

5. echo “deb https://packages.sury.org/php/ stretch main” | sudo tee /etc/apt/sources.list.d/php.list

6. sudo apt update

7. sudo apt install php7.2

8. sudo apt install php7.2-fpm php7.2-mysql php-common php7.2-cli php7.2-common php7.2-json php7.2-opcache php7.2-readline php7.2-mbstring php7.2-xml php7.2-gd php7.2-curl

9. sudo systemctl start php7.2-fpm

10. sudo systemctl enable php7.2-fpm
```

## Nginx
```
1. sudo apt install nginx -> If Error -> sudo fuser -k 80/tcp

2. sudo systemctl start nginx

3. nginx 設定檔 ( 註一 ) 寫入 /etc/nginx/sites-enabled/default

```

## NodeJS
```
1. sudo apt update

2. sudo apt install nodejs

3. sudo apt update

4. sudo apt install curl

5. cd ~

6. curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh

7. sudo bash nodesource_setup.sh

8. sudo apt install nodejs

```

## MySQL
```
1. sudo apt install mariadb-server mariadb-client

2. sudo systemctl start mariadb

3. sudo systemctl enable mariadb

4. sudo mysql_secure_installation

5. sudo mysql

6. CREATE DATABASE wp_db;

7. CREATE USER 'reynold'@'localhost' IDENTIFIED BY '55660123';

8. GRANT ALL PRIVILEGES ON *.* TO 'reynold'@'localhost' WITH GRANT OPTION;

10. FLUSH PRIVILEGES;

```

## Git

```
sudo apt install git
```

## Wordpress 

```
1. sudo cd /tmp

2. wget http://wordpress.org/latest.tar.gz

3. sudo tar -xvzf latest.tar.gz -C /var/www/html

4. sudo chown www-data: /var/www/html/wordpress/ -R

```

* Nginx 設定檔

```
server {
listen 80 default_server;
server_name _;
return 301 https://$host$request_uri;
}

server {
	listen 443 ssl http2;
	listen [::]:443 ssl http2;

	#如果是放cf 可以略過
	#ssl_certificate /etc/nginx/ssl/xxx.crt;
	#ssl_certificate_key /etc/nginx/ssl/xxx.key;

	server_name example.com;
	root /var/www/wordpress-test/wordpress-init;
	index index.php index.html index.htm index.nginx-debian.html;

location / {
	try_files $uri $uri/ /index.php$is_args$args;
	#打開cors
	add_header Access-Control-Allow-Origin *;
	add_header Access-Control-Allow-Methods 'GET, POST, OPTIONS';
	add_header Access-Control-Allow-Headers 'DNT,X-Mx-	ReqToken,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization';
	if ($request_method = 'OPTIONS') {
		return 204;
	}
}
location ~ \.php$ {
	include snippets/fastcgi-php.conf;
	fastcgi_pass unix:/run/php/php7.2-fpm.sock;
}
location ~ /\.ht {
deny all;
}
	if (!-e $request_filename) {
		rewrite ^.*$ /index.php last;
	}
}

#NodeJS
server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    
    ssl_certificate /etc/nginx/ssl/linxnote-club.crt;
    ssl_certificate_key /etc/nginx/ssl/linxnote-club.key;

    server_name line-chatbot.linxnote.club;

 location / {
  proxy_pass http://127.0.0.1:8080;
  proxy_http_version 1.1;
  proxy_set_header Host $host;
 }

}

```