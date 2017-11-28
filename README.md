# Apache Kafka Producer Application

## Table of Contents

  * [Run Zookeeper](#run-zookeeper)
  * [Run three instances of Broker](#run-three-instances-of-broker)
  * [Prequisites](#prequisites)


## Run Zookeeper
```sh
$ cd kafka_2.12-1.0.0

$ .\bin\windows\zookeeper-server-start.bat config\zookeeper.properties

```

## Run three instances of Broker

Copy `server.properties` from `config` directory and make three copies of it and rename to `server2.properties` and `server3.properties` 

```sh
$ cd kafka_2.12-1.0.0

$ .\bin\windows\kafka-server-start.bat config\server.properties

$ .\bin\windows\kafka-server-start.bat config\server2.properties

$ .\bin\windows\kafka-server-start.bat config\server3.properties

```

### Create `Topic` with three partitions and three replicas
```sh
$ cd kafka_2.12-1.0.0

$ .\bin\windows\kafka-topics.bat --create --topic my-topic --zookeeper localhost:2181 --replication-factor 3 --partitions 3

```

### Start `Consumer`
```sh
$ cd kafka_2.12-1.0.0

$ .\bin\windows\kafka-console-consumer.bat --zookeeper localhost:2181 --topic my-topic --from-beginning
```

### Run `Producer` 
```sh
$ mvn clean install
$ mvn exec:java
```

## Prequisites
- Kafka 2.12-1.0.0
- Scala 2.12.4
- Jdk 1.8
