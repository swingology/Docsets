# DOCKER NETWORK

This demo app shows a simple user profile app set up using

    index.html with pure js and css styles
    nodejs backend with express module
    mongodb for data storage

All components are docker-based


## Docker Network Commands
```
docker create network <network>
docker network ls 

```

## Creating a MongoDB Network

Every container inside a docker network - JUST NEED DOCKER CONTAINER NAMES
FROM OUTSIDE the network you need to manage all the ports

```
# Create Network
docker network create <network name>

# Start mongodb
docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    

# Start mongo express
docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express

```


















## Docker file for 2 Containers working in a network



