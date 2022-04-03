## Task 2. Docker

### Description
Hometask: Написать Dockerfile для backend который располагается в директории /lib_catalog(для сборки контейнера необходимо использовать файл /lib_catalog/requirements.txt), для работы backend необходим postgresql, т.е. необходимо собрать 2 контейнера:

1. backend
2. postgresql

Осуществить сетевые настройки, для работы связки backend и postgresql.


### Create network
```
docker network create --subnet 192.168.100.0/24 --gateway=192.168.100.1 --ip-range 192.168.100.0/24 --label=backend_network backend_network
```

### Run Database
```
docker run -d --name postgres_db --network backend_network --ip 192.168.100.20 -e POSTGRES_USER=django -e POSTGRES_PASSWORD=django -e POSTGRES_NAME=django postgres:13
```

### Building from a Dockerfile and launching
```
git clone https://github.com/nordz0r/docker_homework/
cd docker_homework/lib_catalog
docker build -t docker_task2:v0.1 -t docker_task2:latest  .
docker run -d -p 8000:8000 --name docker_task2 --network backend_network --ip 192.168.100.10 docker_task2:latest
```



### Tested
Tested on Debian 11 WSL2 (Windows 10)
