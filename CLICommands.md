# Kafka CLI

## Kafka-Topics

### Create

Creates a topic called orders, with six partitions and two replications.

```
kafka-topics --bootstrap-server 127.0.0.1:9092 --topic orders --create --partitions 6 --replication-factor 2
```

### Describe

```
kafka-topics --bootstrap-server 127.0.0.1:9092 --topic orders --describe

```

### List

```
kafka-topics --bootstrap-server 127.0.0.1:9092 --list
```

### Delete

```
kafka-topics --bootstrap-server 127.0.0.1:9092 --topic orders --delete
```

## Kafka Producer

```
kafka-console-producer --broker-list 127.0.0.1:9092 --topic orders
kafka-console-producer --broker-list 127.0.0.1:9092 --topic orders --producer-property acks=1
kafka-console-producer --broker-list 127.0.0.1:9092 --topic orders --property parse.key=true --property key.separator=,
<!-- key, value -->
```

## Kafka Consumer

```
kafka-console-consumer --bootstrap-server=127.0.0.1:9092 --topic orders
kafka-console-consumer --bootstrap-server=127.0.0.1:9092 --topic orders --from-beginning
kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --topic orders --property print.key=true --property key.separator=,
```

### Consumer Groups

```
kafka-console-consumer --bootstrap-server=127.0.0.1:9092 --topic orders --group my-first-application
kafka-consumer-groups --bootstrap-server=127.0.0.1:9092 --list
kafka-consumer-groups --bootstrap-server=127.0.0.1:9092 --describe --group my-first-application
```

Running more consumer groups than there are partitions will result in an inactive group.

1. kafka-topics.bat --bootstrap-server 35.239.241.212:9092,35.239.230.132:9092,34.69.66.216:9092 --topic question-1 --describe
2. kafka-topics --bootstrap-server 35.239.241.212:9092,35.239.230.132:9092,34.69.66.216:9092 --topic question-2-safna1 --create --partitions 3 --replication-factor 3   
3. kafka-console-consumer --bootstrap-server 35.239.241.212:9092,35.239.230.132:9092,34.69.66.216:9092 --topic question-3 --from-beginning --max-messages 10
4. kafka-console-producer --bootstrap-server 35.239.241.212:9092,35.239.230.132:9092,34.69.66.216:9092 --topic question-4
   kafka-console-consumer --bootstrap-server 35.239.241.212:9092,35.239.230.132:9092,34.69.66.216:9092 --topic question-4