2024-12-18 08:09

Tags: [[Docker]]

---

## List all container

```sh
docker ps
```

## Build image from Dockerfile
```sh
docker build -t tag-name .
```
- `-t`: tag - give the image a tag to run later
- `.`: the path to the `Dockerfile`

## List all images
```sh
docker images
```

## Run a container from image
```sh
docker run -d --name [container_name] -p 1234:2345 [image_name]
```
- `-d`: run container in detached mode
- `--name`: give container a name
- `-p`: map port (1234) on the host machine to port (2345) of container
## Stop a running container
```sh
docker stop [contianer_name_or_id]
```
## If using docker-compose
- Add `docker-compose.yml`
```yml
version: '3.8'

  

services:

  

  zookeeper:

    image: wurstmeister/zookeeper:latest

    ports:

      - "2181:2181"

  

  kafka:

    build:

      context: ./kafka

    environment:

      KAFKA_ZOOKEEPER_CONNECT: "zookeeper:2181"

      KAFKA_ADVERTISED_LISTENERS: "PLAINTEXT://localhost:9092"

      KAFKA_LISTENERS: "PLAINTEXT://0.0.0.0:9092"

      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1

    ports:

      - "9092:9092"

    depends_on:

      - zookeeper

  

  activemq:

    build:

      context: ./activemq

    environment:

      ACTIVEMQ_ADMIN_LOGIN: "admin"

      ACTIVEMQ_ADMIN_PASSWORD: "admin"

      ACTIVEMQ_OPTS_MEMORY: "-Xms512M -Xmx2G"

    ports:

      - "61616:61616"

      - "8161:8161"

      - "61613:61613"
```

---
# References