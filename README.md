# phpspace

This project provides a quick setup for running nginx and PHP containers using Docker Compose. It allows users to easily configure and deploy a web server environment for PHP-based applications.

## How to Build 

1. Clone this repository: `git clone https://github.com/4lkaid/phpspace.git`
2. Navigate to the project directory: `cd phpspace`
3. Start the containers: `docker compose up -d`

## Configuration Example

File path: `path/phpspace/html/demo/nginx.conf`

```nginx
server {
  listen       80;
  server_name  demo.test;

  location / {
    root   /usr/share/nginx/html/demo;
    index  index.html index.php;
    try_files $uri $uri/ /index.php?$query_string;
  }

  location ~ \.php$ {
    root           /var/www/html/demo;
    fastcgi_pass   php:9000;
    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    include        fastcgi_params;
  }
}
```