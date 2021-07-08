docker run -d --name mycontainer -p 80:80 myimage
# DOCKER QUICKSTART

CLI QUICK COMMANDS



``` bash

## IMAGES

docker images   # get list fo docker images

docker pull <image>    # get docker image from dockerhub


docker build [OPTIONS] PATH | URL | -
docker build -t myimage/latest .    # build an image tagged myimage/latest from current dir 
docker build -f dockerfile .        # specifies docerk file
docker rmi <image>              # delete an image:  -f flag is to force it 

docker system prune             # remove all containers, images, networks that are "dangling"



## CONTAINERS
docker ps       # get list of docker containers: -a flag is to list all??
docker run <image-name>     # run docker images and create a container from image

docker run -d --name mycontainer -p 80:80 myimage



docker run -it myimage:latest /bin/bash     
# run myimage in i(nteractive) t(erminal) connected mode
# start /bin/bash on running the container
# can use -d flag to start d(etached) - run container in background and exit when container close
# --name flag names the container

docker run -p 8080:80 myimage/latest 
# map port 8080 of host device to port 80 of container


docker run --it -p 8080:80 --name=webserver1 -v /mnt/data nvingx:latest 
# mount data inside a conatiner



docker stop <container-id>  # stops container 



docker inspect container-id # gives details about container can: | grep ip to call ip info






```

pull image (build and image) -> docker run (Creates a container) 


####### *********************************** ############
### Docker Exec 
https://docs.docker.com/engine/reference/commandline/exec/
```
# Run a command in a running container
docker exec -it <container_id> <command>
docker exec -it <container_id> redis-cli      # run redis-cli in containeri
docker exec -it <container_id> sh
```
#### [Docker Exec Options](https://docs.docker.com/engine/reference/commandline/exec/#options)

| Name, shorthand        | Default | Description                                                                                       |
| ---------------------- | ------- | ------------------------------------------------------------------------------------------------- |
| `--detach` , `-d`      |         | Detached mode: run command in the background                                                      |
| `--detach-keys`        |         | Override the key sequence for detaching a container                                               |
| `--env` , `-e`         |         | [API 1.25+](https://docs.docker.com/engine/api/v1.25/)<br>Set environment variables               |
| `--env-file`           |         | [API 1.25+](https://docs.docker.com/engine/api/v1.25/)<br>Read in a file of environment variables |
| `--interactive` , `-i` |         | Keep STDIN open even if not attached                                                              |
| `--privileged`         |         | Give extended privileges to the command                                                           |
| `--tty` , `-t`         |         | Allocate a pseudo-TTY                                                                             |
| `--user` , `-u`        |         | Username or UID (format: <name\|uid>[:<group\|gid>])                                              |
| `--workdir` , `-w`     |         | [API 1.35+](https://docs.docker.com/engine/api/v1.35/)<br>Working directory inside the container  |














####### *********************************** ############

docker attach
docker create & docker start ( for containers) > combined in docker run

docker stop vs docker kill   //docker stop tells it to start cleaning up and shutdown

idocker logs



### DOCKER ATTACH
When containers are run with the interactive option, you can connect to the container and enter commands as if you are on the terminal:
``` shell
$ docker run -itd --name busybox busybox
dcaecf3335f9142e8c70a2ae05a386395b49d610be345b3a12d2961fccab1478

$ docker attach busybox
/ # echo hello world
hello world
```
Lastly, while connected to a container with the tty option (-t), you can type Control-P Control-Q to detach from that container and leave it running in the background.

### MOUNT BASE DIR IN CONTAINER
```
docker run -it  -v  /etc:/etc1 8251da35e7a7 /bin/bash
# /etc is dir from host machine /etc1 is target inside container
```

### LAUNCH A CONTAINER WITH A VOLUME
``` shell
[root@localhost ~]# docker run -it -v  /data  --name=vol3   8251da35e7a7 /bin/bash
root@d87bf9607836:/# cd /data/
root@d87bf9607836:/data# touch abc{1..10}
root@d87bf9607836:/data# ls
```


docker logs

