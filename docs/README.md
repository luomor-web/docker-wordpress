```shell
cd docker
sudo docker-compose up -d

sudo docker-compose ps

http://82.157.54.206:8000/
http://82.157.54.206:8000/wp-admin
admin
admin123
admin@test.com
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