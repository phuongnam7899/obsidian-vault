
# Common
## Create Gitlab SSH Key
- Follow this link to create new SSH key in local machine: [Ssh · User · Help · GitLab](https://git.vti.com.vn/help/user/ssh.md)
- Enter [SSH Keys · User Settings · GitLab](https://git.vti.com.vn/-/user_settings/ssh_keys)
- Select "Add new key"
- Paste the created key -> "Add key"

# Back-end Setup
## Pre-install
- VS Code with extensions:
	- Extension Pack for Java (Follow this link to setup Java in VS Code: [Getting Started with Java in VS Code](https://code.visualstudio.com/docs/java/java-tutorial))
	- Prettier
- Java 17
- Docker Desktop
- DBeaver
- Postman

## Setup Steps

### Clone repositories

> [!i] Using the "Clone with SSH" link

- [TMA - LMA Refresh / P360-BE · GitLab](https://git.vti.com.vn/tma-lma-refresh/p360)
- If developing PMA:
	- [TMA - LMA Refresh / PMA-BE · GitLab](https://git.vti.com.vn/tma-lma-refresh/pma-be)
- If developing TMA:
	- [TMA - LMA Refresh / TMA-BE · GitLab](https://git.vti.com.vn/tma-lma-refresh/tma-be)
- If developing LMA:
	- [TMA - LMA Refresh / LMA-BE · GitLab](https://git.vti.com.vn/tma-lma-refresh/lma-be)

### Setup Kafka + ActiveMQ containers
- Create a `/tma-lma-docker` folder
- Create `/kafka` folder inside `/tma-lma-docker`
- Create `Dockerfile` inside `/kafka`:
```Dockerfile
FROM wurstmeister/kafka:2.13-2.7.0

ENV KAFKA_BROKER_ID=1
ENV KAFKA_ZOOKEEPER_CONNECT=zookeeper:2181
ENV KAFKA_ADVERTISED_LISTENERS=10.1.43.136:9092
ENV KAFKA_LISTENERS=10.1.43.136:9092
ENV KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR=1

EXPOSE 9092

CMD ["start-kafka.sh"]
```
- Create `docker-compose.yml` inside `/tma-lma-docker`:
```yml

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
    image: apache/activemq-classic:5.19.0
    environment:
      ACTIVEMQ_ADMIN_LOGIN: "admin"
      ACTIVEMQ_ADMIN_PASSWORD: "admin123"
      ACTIVEMQ_OPTS_MEMORY: "-Xms912M -Xmx3G"
    ports:
      - "61616:61616"
      - "8161:8161"
      - "61613:61613"
    volumes:
      - ./activemq/data:/var/lib/activemq/data
      - ./activemq/logs:/var/log/activemq
      - ./activemq/conf:/opt/activemq/conf
      - ./activemq/data:/var/lib/activemq/data


```
- Start the containers: `docker-compose up -d`

### Change the local application properties
- In `application-azuredesktop.properties`, update the following fields to your IP:
```properties
spring.activemq.broker-url=tcp://[your_ip_address]:61616
stomp.broker.relay.server.host=[your_ip_address]
spring.kafka.bootstrap-servers=[your_ip_address]:9092
```

> [!i] To check your IP address, run `ipconfig` in the CMD -> Find for IPv4 value

### Start the application

> [!i] To make sure the DB is working well, you can try using DBeaver to connect to the DB by the `spring.datasource` configs (in the `application-azuredesktop.properties`) first

- Select any `.java` file
- Press `F5` (make sure you install mentioned extenstions and the JDK first)

# Front-end Setup
## Pre-install
- NodeJs v22
## Setup Steps
### Clone repositories

> [!i] Using the "Clone with SSH" link

- If developing PMA:
	- [TMA - LMA Refresh / PMA-UI · GitLab](https://git.vti.com.vn/tma-lma-refresh/pma-ui)
- If developing TMA:
	- [TMA - LMA Refresh / TMA-UI · GitLab](https://git.vti.com.vn/tma-lma-refresh/tma-ui)
- If developing LMA:
	- [TMA - LMA Refresh / LMA-UI · GitLab](https://git.vti.com.vn/tma-lma-refresh/lma-ui)

### Change the environment config
- In `environment.ts`, update the following field to connect to correct BE:

```ts

export const environment: EnvironmentMode = {
	// ...
	apiUrl:'http://{your_be_url}:9002/lma-api/logistic',
	webSocketEndPoint:`http://{your_be_url}:9002/lma-api/logistic/notifications/ws/stomp`,
	// ...
}

```

### Start the application
- Install modules: `npm install`
- Start the application: `npm  start`
- Try login with one of these accounts:
	- `ATTLICY1@globalpsa.com` / `P@ssw0rd321`
	- `ATTNHUP1@globalpsa.com` / `P@ssw0rd321`
	- `ATTMIND1@globalpsa.com` / `P@ssw0rd321`
	- `ATTLING1@globalpsa.com` / `P@ssw0rd321`