# Apache Kafka

Apache Kafka helps you decouple your data streams. It is a distributed system.

How we use it at the time of writing...

## General concepts

### Topics

- Topics are a stream of data, kind of like a database without all the constraints
- One can have as many topics as you want
- topic is identified by it name
- Topics are split into partitions
- each partitions is ordered
- each message within a partition gets and incremental id, called and offset
- once data has been written to a partition it cannot be changed aka `IMMUTABILITY`

## Brokers

- A Kafka cluster is composed of multiple brokers (servers)
- broker is identified by an ID
- after connecting to any broker (called bootstrap broker), you are effectively connected to the entire cluster
- if one broker dies, we will still have 2 live brokers to serve data

## Leader

At any given time only one can only have a leader. Only that leader can receive and send data, all other brokers copy whats going on in the leader.

## Producer

Producers write data to a topic. They only have to specif a topic name and the data will be written to the broker.

### ssh into kafka pod

docker run --rm -it --net=host landoop/fast-data-dev bash

## What is it

Kafka is a message a streaming data pipeline.

### Commands

Here are some basic commands once you have got an instance of Kafka running.

#### Create topic

```bash
kafka-topics --zookeeper 127.0.0.1:2181 --create --topic first_topic --partitions 3 --replication-factor 1
```

#### List

```bash
kafka-topics --zookeeper 127.0.0.1:2181 --list
```

#### Delete topic

```bash
kafka-topics --zookeeper 127.0.0.1:2181 --topic first_topic --delete
```

#### Describe topic

```bash
kafka-topics --zookeeper 127.0.0.1:2181 --topic first_topic --describe
```

#### Consuming data from from topic using console

```bash
kafka-console-consumer --botstrap-server 127.0.0.1:9092 --topic first_topic --from-beginning
```