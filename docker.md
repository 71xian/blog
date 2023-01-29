## docker 笔记

查看docker信息: docker info

宿主机传文件到容器

> docker cp {host_path}/{host_file} {container_name}:{container_path}

容器传文件到宿主机

> docker cp {container_name}:{container_path}/{container_file} {host_path}/{host_file}

查看镜像
> docker images

删除镜像
> docker rmi {image_name}:{tag}

删除容器
> docker rm {container_name}

停止容器
> docker stop {container_name}

显示容器
> docker container ls -a

查看容器日志
> docker logs {container_name}

进入容器
> docker exec -it {container_name} /bin/bash

## docker-compose

nacos 需要数据库url需要删除&connectTimeout=1000&socketTimeout=3000&useSSL=false 

```yaml
version: '3'
services:
  nacos:
    image: nacos/nacos-server
    container_name: standalone-nacos
    environment:
      - MODE=standalone
    volumes:
      - ./logs:/home/nacos/logs
      - ./application.properties:/home/nacos/conf/application.properties
    ports:
      - "8848:8848"
      - "9848:9848"
      - "9555:9555"
    networks:
      - localhost
    restart: always
    
networks:
  localhost:
    external:
      name: web
```

## 网络

birdge: 为每一个容器分配，设置ip,并将容器连接到一个docker0虚拟网桥，默认模式

host: 不会生成虚拟网卡，使用宿主机的ip和端口

none: 容器有自己的network namespace，但并没有对其进行任何网络设置

container: 和一个容器共享ip，端口

查看网络:

docker network ls

创建网络 

docker network create {network_name} -d {network_mode}

查看该网络下有什么容器:

docker inspect {network_name}

容器之间的通信可以直接使用服务名

推荐阅读：

[docker从入门到实践](https://github.com/yeasy/docker_practice)

[nacos-docker](https://github.com/nacos-group/nacos-docker)
