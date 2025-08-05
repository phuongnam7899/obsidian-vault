- docker-compose stop kafka-redhat
- docker-compose rm -f kafka-redhat
- docker-compose up -d kafka-redhat
- docker exec -it kafka-redhat bash

- Update connector config:
```
curl -X PUT http://localhost:8083/connectors/{connector-name}/config \

  -H "Content-Type: application/json" \

  -d @config-file.json
```
- Restart worker
```
curl -X POST http://localhost:8083/connectors/{connector-name}/tasks/{task-id}/restart
```
- View message in parttion of topic by offset: 
```sh 
/opt/kafka/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic topic-1 --partition 0 --offset 2 --max-messages 1
```

- Start the auto restart failed tasks:
```
chmod +x auto-restart-failed-tasks.sh  
nohup ./auto-restart-failed-tasks.sh > restart-monitor.log 2>&1 &
```