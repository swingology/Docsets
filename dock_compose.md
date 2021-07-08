# DOCKER COMPOSE GUIDE
docker: @compose: 


## Quickstart
```
docker compppose up     # starts starts and runs entire app
docker compose down     # stops entire app




```



## Example of docker compose
``` bash
version: "3.9"  # optional since v1.27.0
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/code
      - logvolume01:/var/log
    links:
      - redis
  redis:
    image: redis
volumes:
  logvolume01: {}

```


## SUMMARY
BAREBONES
```
version: "3.7"
services:
    # container's configuration
        - pull an image
        - build an image
volumes:
    # shared dir in host
        - 
networks:
    
```
### Services

```
services:
  network-example-service:
    image: karthequian/helloworld:latest
    ports:
      - "80:80"
    ...
  my-custom-app:
    image: myapp:latest
    ports:
      - "8080:3000"
    ...
  my-custom-app-replica:
    image: myapp:latest
    ports:
      - "8081:3000"
    ...

```


### Volumes
```
services:
  volumes-example-service:
    image: alpine:latest
    volumes: 
      - my-named-global-volume:/my-volumes/named-global-volume
      - /tmp:/my-volumes/host-volume
      - /home:/my-volumes/readonly-host-volume:ro
    ...
  another-volumes-example-service:
    image: alpine:latest
    volumes:
      - my-named-global-volume:/another-path/the-same-named-global-volume
    ...
volumes:
  my-named-global-volume: 
```

### Declaring Depnedencies
```
services:
  kafka:
    image: wurstmeister/kafka:2.11-0.11.0.3
    depends_on:
      - zookeeper
    ...
  zookeeper:
    image: wurstmeister/zookeeper
    ...
```

### Managing Env Variables
Working with environment variables is easy in Compose. We can define static environment variables, and also define dynamic variables with the ${} notation:

```
services:
  database: 
    image: "postgres:${POSTGRES_VERSION}"
    environment:
      DB: mydb
      USER: "${USER}"
```


ENVIROMENT FILES .env file in same dir
```
POSTGRES_VERSION=alpine
USER=foo

# Can use oneliner in the shell
POSTGRES_VERSION=alpine USER=foo docker-compose up

```


### Scaling and Replicas
```
services:
  worker:
    image: dockersamples/examplevotingapp_worker
    networks:
      - frontend
      - backend
    deploy:
      mode: replicated
      replicas: 6
      resources:
        limits:
          cpus: '0.50'
          memory: 50M
        reservations:
          cpus: '0.25'
          memory: 20M

```






### USING LOCAL IMAGES IN DOCKER COMPOSE
#### USE .env file

```
version: '3'
services:
  chat-server:
    image: chat-server:staging
    ports:
      - "8110:8110"
  web-server:
    image: web-server:staging
    ports:
      - "80:80"
      - "443:443"
      - "8009:8009"
      - "8443:8443"
```

```
.env file
DOCKER_HOST=tcp://***.***.**.**:2376
DOCKER_TLS_VERIFY=true 
DOCKER_CERT_PATH=/Users/Victor/Documents/Development/projects/.../target/docker
```



#*****************************************************************#
#### Structure and addressing method
#### **WORKING** **TESTED:**
```
# Structure
.
├── docker-compose.yml
└── Dockerfile

# Dockerfile
FROM alpine
CMD ["echo", "i am groot"]

# Build and Tag Image
docker build -t groot .
docker tag groot:latest groot:staging

# Docker-Compose
version: '3.1'
services:
  groot:
    image: groot:staging
   
# Start docker compose
$ docker-compose upCreating groot_groot ... 
Creating groot_groot_1 ... done
Attaching to groot_groot_1
groot_1  | i am groot
groot_groot_1 exited with code 0

```







## Links

[Docker Compose General Guide](https://www.baeldung.com/ops/docker-compose)

[Docker Compose Reference Page](https://docs.docker.com/compose/)
[Docker Compose EXCE Reference](https://docs.docker.com/compose/reference/exec/)
[Docker Compose - compose file Referene](https://docs.docker.com/compose/compose-file/)

[Docker Compose CLI Reference](https://docs.docker.com/compose/cli-/)

