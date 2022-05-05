# docker-training

#### Step 1: In




#### Install Docker Compose

```
sudo curl -L https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```
* Set Permissions
```
sudo chmod +x /usr/local/bin/docker-compose
```
* Check Version
```

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

#### Task 2.1:  Go to mysql running container
* Check the mysql db

```
docker ps -a
```

```
docker exec -it 398 /bin/bash
```
* Note: **ContainerId**: 398

#### Task 2.2: Connect mysql
```
mysql -u root -p
```
Note: Password: rev_user

