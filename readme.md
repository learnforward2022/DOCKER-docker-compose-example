This is an example of an basic docker setup for a node api

### Build image:

    docker build -t webapp:latest .

## create network

    docker network create node-api-network

## Start MYSQL:
    
    docker run \
    --rm \
    -d \
    --name database \
    -e MYSQL_DATABASE='my_database' \
    -e MYSQL_ROOT_PASSWORD='password' \
    --network node-api-network \
    mysql:8.0 

    
## Start node-api

    docker run \
    --rm \
    --name webapp \
    --network node-api-network \
    -p 3003:3000 \
    -v $(pwd):/app \
    node-api:v1 

## Stop running container using

    docker stop webapp
    docker stop database

## or start using

    docker-compose up

## and stop using

    docker-compose down
    