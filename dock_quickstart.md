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

docker exec 
docker attach



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

