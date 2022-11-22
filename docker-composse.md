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
```
