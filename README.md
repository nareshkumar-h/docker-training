# docker-training




#### Install Docker Compose

```
sudo curl -L https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

#### Task 1: Create a Docker file for Spring Boot

* Dockerfile
```unix
FROM openjdk:17-jdk
VOLUME /tmp
COPY target/*.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```

#### Task 2: Create a Docker Compose file for MySQL

* docker-compose.yml

```
version: "3.8"
services:
  mysql:
   image : mysql:5.7
   restart: unless-stopped
   environment:
     - MYSQL_ROOT_PASSWORD=rev_user
     - MYSQL_DATABASE=training_db
   ports:
     - 3306:3306
   volumes:
     - db:/var/lib/mysql

volumes:
  db:
```
