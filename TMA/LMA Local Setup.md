
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
- Create `docker-compose.yml` inside `/tma-lma-docker`:
```yml

services:

  kafka:
    image: confluentinc/cp-kafka:7.6.1
    hostname: kafka
    container_name: kafka
    user: "0:0"  # Run as root to avoid permission issues
    environment:
      # KRaft mode configuration
      KAFKA_NODE_ID: 1
      KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: 'CONTROLLER:PLAINTEXT,PLAINTEXT:PLAINTEXT'
      KAFKA_ADVERTISED_LISTENERS: 'PLAINTEXT://localhost:9092'
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1
      KAFKA_GROUP_INITIAL_REBALANCE_DELAY_MS: 0
      KAFKA_TRANSACTION_STATE_LOG_MIN_ISR: 1
      KAFKA_TRANSACTION_STATE_LOG_REPLICATION_FACTOR: 1
      KAFKA_JMX_PORT: 9104
      KAFKA_JMX_HOSTNAME: localhost
      KAFKA_PROCESS_ROLES: 'broker,controller'
      KAFKA_CONTROLLER_QUORUM_VOTERS: '1@kafka:29093'
      KAFKA_LISTENERS: 'PLAINTEXT://0.0.0.0:9092,CONTROLLER://kafka:29093'
      KAFKA_INTER_BROKER_LISTENER_NAME: 'PLAINTEXT'
      KAFKA_CONTROLLER_LISTENER_NAMES: 'CONTROLLER'
      KAFKA_LOG_DIRS: '/tmp/kraft-combined-logs'
      # Cluster ID for KRaft mode (generate with kafka-storage.sh random-uuid)
      CLUSTER_ID: 'MkU3OEVBNTcwNTJENDM2Qk'
    ports:
      - "9092:9092"
      - "9104:9104"
    volumes:
      - kafka-data:/tmp/kraft-combined-logs
    healthcheck:
      test: ["CMD-SHELL", "kafka-broker-api-versions --bootstrap-server localhost:9092"]
      interval: 30s
      timeout: 10s
      retries: 3
    restart: unless-stopped

  activemq:
    image: apache/activemq-classic:6.1.6
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

volumes:
  kafka-data:
    driver: local

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
- Press `F5` (make sure you install mentioned extensions and the JDK first)

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


# P360 Setup

## Pre-install
- Same as TMA/LMA
## Setup Steps
### Clone the repository
- [TMA - LMA Refresh / P360-BE · GitLab](https://git.vti.com.vn/tma-lma-refresh/p360)

### Setup Database
- Open DBeaver and connect to the P360 database (the connection info is stored at `application-azuredev.properties`)
- Create a new database named `p360_[yourname]`
- Dump the `p360_nam` database
- 