# Docker notes

- `docker --help` or `man docker` -> offline docker manuals on local machine
- `docker pull docker-image-name` -> download docker image from docker hub
- `docker run docker-image-nme` -> check for image on local machine to run a container if not pull from docker hub
- `docker ps` -> list running docker containers
- `docker ps -a` -> list all docker container including running and stopped
- `docker images` -> list all docker images on local machine
- `docker rm docker-container-name` or `docker rm docker-container-id` to remove docker container from local machine
- `docker rmi docker-image-name` to remove docker image from local machine
- `docker exec -it docker-container-name /bin/bash` -> access docker container shell

## Docker volume

**Docker volume is useful for sharing date between physical machine and running docker container to which volume is configured**
*Volumes are created on /var/lib/docker/volumes/volume_name/_data*

- `docker volume --help` -> offline help about docker volumes
- `docker volume inspect my_volume` -> inspect docker volume location
- `docker volume ls` -> list existing docker volumes
- `docker volume create volume-name` -> create volume
- `docker run -v volume-name:/data docker-image-name` -> using volume in a container
- `docker run -v /data docker-image-name` -> using anonymous volume in a container
- `docker run -v /host/path:/container/path docker-image-name` -> For bind mounts, the location on the host is explicitly specified when creating the mount
- `docker volume prune` -> clean up unused volumes

## Docker network

- `docker network create docker-network-name` -> create docker network
- `docker network rm docker-network-name` -> remove docker network
- `docker network ls` -> list docker networks
- `docker network connect docker-network-name docker-container-name` -> add container to certain network
- `docker network disconnect docker-network-name docker-container-name` -> remove container from certain network
- `docker network purne` -> clean up unused network
- `docker run --network myNet01 nginx --volume /path/to/host:/path/to/container -d -p 80:80 nginx` -> run docker container using custom network, adding volume, in detached mode, expose port 80 to host