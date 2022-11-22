https://github.com/ricardoandre97/jenkins-resources/tree/master/jenkins
```
version: '3'
services:
  jenkins:
    container_name: jenkins
    image: jenkins/jenkins
    ports:
      - "8080:8080"
    volumes:
      - "/home/ssm-user/jenkins-data/jenkins_home:/var/jenkins_home"
    networks:
      - net
  remote_host:
    image: remote-host
    build:
      context: centos7
    networks:
      - net
  db_host:
    container_name: db
    image: mysql:5.7
    environment:
      - "MYSQL_ROOT_PASSWORD=1234"
    volumes:
      - "/home/ssm-user/jenkins-data/db_data:/var/lib/mysql"
    networks:
      - net
networks:
  net:
```
```
mysql -u root -p  (-h db)

mysql> create database testdb;
mysql> show databases;

ysql> use testdb;
Database changed

mysql> create table info (name varchar(20), lastname varchar(20), age int(20));
Query OK, 0 rows affected (0.01 sec)

mysql> show tables;
+------------------+
| Tables_in_testdb |
+------------------+
| info             |
+------------------+
1 row in set (0.00 sec)


mysql> desc info;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| name     | varchar(20) | YES  |     | NULL    |       |
| lastname | varchar(20) | YES  |     | NULL    |       |
| age      | int(20)     | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+

ysql> insert into info values ('jerry', 'hong', 20);
Query OK, 1 row affected (0.01 sec)

mysql> select * from info;
+-------+----------+------+
| name  | lastname | age  |
+-------+----------+------+
| jerry | hong     |   20 |
+-------+----------+------+
1 row in set (0.00 sec)
```
