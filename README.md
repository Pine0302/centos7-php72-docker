# centos7-php72-docker

docker-compose.yml
```yaml
services:
  test:
    image: liich/centos7-php72-docker:v0.2.5
    volumes:
      - ./nginx/test.conf:/etc/conf.d/default.conf
      - ../test:/srv
```

./nginx/test.conf
```conf
# nginx site config
server {
  root /srv/public;
  
  location ~* \.php$ {
    fastcgi_pass unix:/tmp/php-fpm.sock;
    include       fastcgi_params;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    fastcgi_param SCRIPT_NAME     $fastcgi_script_name;
  }
}
```
