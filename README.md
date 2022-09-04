# DOCKER-PROJECT

# Mysql

```
docker run \
--detach \
--name=[container_name]\
--env="MYSQL_ROOT_PASSWORD=[my_password]" \
--publish 6603:3306 \
--volume=/root/docker/[container_name]/conf.d:/etc/mysql/conf.d \
mysql:tag
```

**--publish**: Publish a container's port(s) to the host \
-docker mysql port: 3306 \
-public host port: 6603

**--volume**: Bind mount a volume
Here i bind directory contain my.cnf file

**mysql:tag**: name of image and image's tag

Exmaple:

```
docker run \
--detach \
--name=mysql-container\
--env="MYSQL_ROOT_PASSWORD=P@ssword789" \
--publish 6603:3306 \
--volume=/root/docker/mysql/conf.d:/etc/mysql/conf.d \
mysql:8.0.23
```

Connect with mysql client

```
mysql -u root -h 127.0.0.1 -P 3306 -pP@ssword789
```