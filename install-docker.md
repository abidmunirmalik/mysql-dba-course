## INSTALL DOCKER

### OS UPDATE
```sh
sudo yum update
```

### SEARCH FOR DOCKER
```sh
sudo yum search docker
sudo yum info docker
```

### INSTALL DOCKER
```sh
sudo yum install docker -y
```

### ADD CURRENT USER TO DOCKER GROUP
```sh
sudo usermod -a -G docker $USER
```

### VERIFY GROUP MEMBERSHIP
```sh
id 
exit
```

### ENABLE AND START DOCKER
```sh
sudo systemctl enable docker.service
sudo systemctl start docker.service
systemctl status docker.service
```

### LIST DOCKER IMAGES
```sh
docker images
```

### LIST DOCKER CONTAINERS
```sh
docker ps
```

### SEARCH FOR MYSQL
```sh
docker search mysql
```

### PULL MYSQL DOCKER IMAGE
```sh
docker pull mysql
docker images
```

### INSPECT MYSQL DOCKER IMAGE
```sh
docker inspect mysql
```

### RUN MYSQL CONTAINER
```sh
docker run --name mysql-831 -e MYSQL_ROOT_PASSWORD=P@ssw0rd -d mysql:latest
```

### VERIFY IF MYSQL IS RUNNING AS CONTAINER
```sh
docker container ps
pidof mysqld
sudo netstat -ntlp | grep 3306 <-- No, why?
```

### INSPECT MYSQL CONTAINER
```sh
docker container inspect mysql-831
```

### MYSQL CONTAINER LOGS
```sh
docker logs mysql-831
```
