# Docker Compose example for mongodb-express-nodejs Network



```
version: '3'
services:
    mongodb:
        image: mongo
        ports: 
            - 27017:27017
        environment:
            - MONGO_INITDB_ROOT_USERNAME=ADMIN
            - MONGO_INITDB_ROOT_PASSWORD=password
    mongo-express:
        image:mongo-express
        ports : 
            - 8080:8081
        environment:
            - ME_CONFIG-MONGODB_ADMINEUSERNAME=admin
            - ME_CONFIG-MONGODB_ADMINEPASSWORD=password
            - ME_CONFG_MONGODB_SERVER=mongodb

```
