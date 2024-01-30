
# documentation
how to use project
[https://www.conduktor.io/kafka/how-to-start-kafka-using-docker/](https://www.conduktor.io/kafka/how-to-start-kafka-using-docker)

to start standard kafka environment
```
docker compose -f zk-single-kafka-single.yml up
```

after this you can connect your Kafka consumer or producer from another container by address `localhost:9092` or `host.docker.internal:29092`

## useful commands
enter to Kafka container
```
docker exec -it kafka1 /bin/bash
```

to create topic
```
kafka-topics --bootstrap-server localhost:9092 --topic first_topic --create --partitions 3 --replication-factor 1
```

to produce message
```
kafka-console-producer --bootstrap-server localhost:9092 --topic first_topic --property parse.key=true --property key.separator=:
>key_1:message_1
>key_2:message_2
``` 

to consume message
```
kafka-console-consumer --bootstrap-server localhost:9092 --topic first_topic --group my-first-application 
```