# DOCKER GUIDE
@docker: @dockerfiles: @dockercompose:

______
## DockerFiles

### Example - Python Alpine DockerFile
Create following dockerfile in a dir that will house the project APP dir
``` shell
FROM python:3.9.5-alpine

WORKDIR /app
COPY requirements.txt /
RUN pip install -r /requirements.txt    # isntall flask and gunicorn

COPY . /app

```




### Example - Datascience example dockerfile
``` shell

FROM python:3.6-alpine
RUN apk --no-cache add --virtual build-dependencies \
                build-base \
                python3-dev \
        && pip3 install \
                jupyter \
                pandas
WORKDIR /notebooks

```

### CMDS
| FROM | using a dockerhub image | 
||
| RUN | run a command during build process - usually install
| RUN apk add --update redis | 
| |
| CMD | command on starting container from image | 
| CMD ["redis-server"] |  


### Multi Stage Builds
Take advantage of multi-stage builds to create a temp image used for building an artifact that will be copied over to the production image. The temp build image is discarded along with the original files, folders, and dependencies associated with the image.

This produces a lean, production-ready image.

One use case is to use a non-Alpine base to install dependencies that require compilation. The wheel files can then be copied over to the final image.


### Web Dev Example Mutli-Stage dockerfile
``` shell
FROM python:3.6 as base
COPY requirements.txt /
RUN pip wheel --no-cache-dir --no-deps --wheel-dir /wheels -r requirements.txt

FROM python:3.6-alpine
COPY --from=base /wheels /wheels
COPY --from=base requirements.txt .
RUN pip install --no-cache /wheels/* # flask, gunicorn, pycrypto
WORKDIR /app
COPY . /app

```


### Data Science Multi-Stage dockerfile
``` shell
FROM python:3.6 as base
RUN pip wheel --no-cache-dir --no-deps --wheel-dir /wheels jupyter pandas

FROM python:3.6-sliim
COPY --from=base /wheels /wheels
RUN pip install --no-cache /wheels/*
WORKDIR /notebooks
```


### CI Multi-Stage dockerfile
``` shell
FROM python:3.6 as base
RUN pip wheel --no-cache-dir --no-deps --wheel-dir /wheels -r flask
COPY . /app
# What happens if the tests fail?
RUN py.test

FROM python:3.6-alpine
COPY --from=base /wheels /wheels
RUN pip install --no-cache /wheels/*
COPY . /app

```




_______
######################*****************************************
## DOCKER COMPOSE
### [Docker Compose Webdev Ex](https://github.com/testdrivenio/docker-python-devs/tree/master/web/05_compose/project)
``` shell
###########
	# BUILDER #
	###########
	
	# Base Image
	FROM python:3.6 as builder
	
	# Install Requirements
	COPY requirements.txt /
	RUN pip wheel --no-cache-dir --no-deps --wheel-dir /wheels -r requirements.txt
	
	
	#########
	# FINAL #
	#########
	
	# Base Image
	FROM python:3.6-slim
	
	# Create directory for the app user
	RUN mkdir -p /home/app
	
	# Create the app user
	RUN groupadd app && useradd -g app app
	
	# Create the home directory
	ENV HOME=/home/app
	ENV APP_HOME=/home/app/web
	RUN mkdir $APP_HOME
	WORKDIR $APP_HOME
	
	# Install Requirements
	COPY --from=builder /wheels /wheels
	COPY --from=builder requirements.txt .
	RUN pip install --no-cache /wheels/*
	
	# Copy in the Flask code
	COPY . $APP_HOME
	
	# Chown all the files to the app user
	RUN chown -R app:app $APP_HOME
	
	# Change to the app user
	USER app
	
	# run server
	CMD gunicorn -b 0.0.0.0:5000 manage:app


```


#### Docker Compose





























_______



## Dockerfile Tips
**Order Dockerfile commands**

Docker caches the steps in a Dockerfile to speed up subsequent builds. When a change is made to a step, all steps following it will be redone.
Avoid invalidating the cache by-

   1. Starting your Dockerfile with commands that are less likely to change
   2. Putting commands that are more likely to change (like COPY .) as late as possible
   3.  Adding only the necessary files (use a .dockerignore file!)

Example
``` shell
FROM python:3.6-alpine
WORKDIR /app
# What happens when a change is made to sample.py?
COPY sample.py /app
COPY requirements.txt /
RUN pip install -r /requirements.txt  # flask and gunicorn

```

Move the COPY sample.py /app statement to the bottom!



**Minimize the Number of Layers**
Combine RUN steps that are related to prevent caching (since each RUN step will create a new layer) and using unnecessary disc space.
Things to note
    1. RUN, COPY, and ADD steps will create layers.
    2. Each layer contains the differences from the previous layer.
    3. Layers increase the size of the final image.

Tips
    1. Put related commands (apt-get update/install) in the same RUN step.
    2. Remove files in the same RUN step that created them.
    3. Avoid using apt-get upgrade since it upgrades all packages to the latest version... Why?
    4. Use multi-stage builds as much as possible!





_____
## DOCKER COMPOSE
Docker Compose is an orchestration tool used for running **multi-container apps**. It helps streamline building, running, and connecting multiple containers together. To use Docker Compose, you'll need to define how to build your containers with YAML in a **docker-compose.yml** file.

[webdev docker compose ex\(https://github.com/testdrivenio/docker-python-devs/tree/master/web/05_compose)
















______
## FURTHER TOPICS


### Version Docker Images


### Create a Non-Root User
i
If you're root in the container, you'll be root on the host.

#### Webdev Non Root User dockerfile
``` shell
# Base
FROM python:3.6-alpine
	
# Create directory for the app user
RUN mkdir -p /home/app
	
# Create the app user
RUN addgroup -S app && adduser -S -G app app
	
# Create the home directory
ENV HOME=/home/app
ENV APP_HOME=/home/app/web
RUN mkdir $APP_HOME
WORKDIR $APP_HOME
	
# Install requirements
COPY requirements.txt /
RUN pip install -r /requirements.txt  # flask and gunicorn
	
# Copy in the Flask code
COPY . $APP_HOME
	
# Chown all the files to the app user
RUN chown -R app:app $APP_HOME

# Change to the app user
USER app

```

**VERIFY**
``` shell
docker run -p 5000:5000 -i sample id
uid=100(app) gid=101(app) groups=101(app)

docker run -p 8888:8888 -i ds id
uid=100(app) gid=101(app) groups=101(app)
```




#### Data Science Non Root User dockerfile
``` shell
FROM python:3.6-alpine
	
RUN apk --no-cache add --virtual build-dependencies \
                build-base \
                python3-dev
	
# Create directory for the app user
RUN mkdir -p /home/app
	
# Create the app user
RUN addgroup -S app && adduser -S -G app app
	
# Create the home directory
ENV HOME=/home/app
ENV APP_HOME=/home/app/notebooks
RUN mkdir $APP_HOME
WORKDIR $APP_HOME
	
# Install requirements
RUN pip install jupyter pandas
	
# Chown all the files to the app user
RUN chown -R app:app $APP_HOME
	
# Change to the app user
USER app

```


## DO NOT STORE SECRETS IN AN IMAGE


| adsfads | adsfdas | adsffdsa |
|---------|---------|----------|
| adsf    | asdf    | adsfsda
[SOURCE](https://mherman.org/presentations/dockercon-2018)
[Dockerhub python repos](https://hub.docker.com/_/python)
