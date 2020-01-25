Docker Mysql Demo
=================

启动：

```
docker-compose up -d
```

关闭：

```
docker-compose down
```

mysql server 默认情况不允许从远程连接，但是由于我们在`docker-compose.yml`里指定了参数`MYSQL_ROOT_HOST=%`，
它将会由docker启动时相应的脚本执行一些额外的操作，允许远程访问。

```
brew install mysql
mysql -uroot -P 23306 -h localhost -p
```

（注意`-h`指定目标)

初始化数据可以放在`docker-entrypoint-initdb.d`中，它们会在启动后执行。

```
mysql -uroot -P 23306 -h localhost -p
$ use mydb;
$ show tables;
$ select * from books;
```

详情请一定参看：

- https://github.com/mysql/mysql-docker/blob/mysql-server/5.6/docker-entrypoint.sh
