```shell
cd docker
sudo docker-compose up -d
sudo docker-compose ps
sudo docker-compose logs -f

docker exec -it wordpress bash

docker cp wordpress:/usr/local/etc etc

docker-compose logs service_name
docker-compose exec webserver ls -la /etc/letsencrypt/live
docker-compose up --force-recreate --no-deps certbot
docker-compose stop webserver
curl -sSLo nginx-conf/options-ssl-nginx.conf https://raw.githubusercontent.com/certbot/certbot/master/certbot-nginx/certbot_nginx/_internal/tls_configs/options-ssl-nginx.conf

http://82.157.54.206:8000/
http://82.157.54.206:8000/wp-admin
admin
admin123

http://82.157.54.206:8000/wp-admin/install.php
admin
admin123
admin@test.com

https://hub.docker.com/_/wordpress
6.1.1

https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-docker-compose

https://cn.wordpress.org/
```

```shell
sudo docker container run \
  -d \
  --rm \
  --name wordpressdb \
  --env MYSQL_ROOT_PASSWORD=123456 \
  --env MYSQL_DATABASE=wordpress \
  mysql:5.7

sudo docker container run \
  -d \
  -p 8080:80 \
  --rm \
  --name wordpress \
  --env WORDPRESS_DB_PASSWORD=123456 \
  --link wordpressdb:mysql \
  --volume "$PWD/wordpress":/var/www/html \
  wordpress

docker container ls

docker exec -it wordpress /bin/bash
cd wp-content/
vim wordpress/wp-config.php
// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define( 'DB_NAME', getenv_docker('WORDPRESS_DB_NAME', 'wordpress') );
/** MySQL database username */
define( 'DB_USER', getenv_docker('WORDPRESS_DB_USER', 'root') );
/** MySQL database password */
define( 'DB_PASSWORD', getenv_docker('WORDPRESS_DB_PASSWORD', '123456') );

docker exec -it wordpressdb /bin/bash
mysql -u root -p
show databases;
```

```
docker wordpress
docker-compose wordpress

https://cloud.tencent.com/developer/article/2028050
https://docs.docker.com/compose/wordpress/
```