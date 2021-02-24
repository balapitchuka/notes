## Kafka Basics:

Kafka in a nutshell

- **Kafka is a** **service bus**: To connect heterogeneous applications,     we need to implement a message publication mechanism to send and receive     messages among them. A message router is known as message broker. Kafka is     a message broker, a solution to deal with routing messages among clients     in a quick way.
- **Kafka architecture     has two directives**: The first is to not block the producers (in order to deal with     the back pressure). The second is to isolate producers and consumers. The     producers should not know who their consumers are, hence Kafka follows the     dumb broker and smart clients model.
- **Kafka is a real-time messaging system**: Moreover, Kafka is a software solution with a publish-subscribe     model: open source, distributed, partitioned, replicated, and     commit-log-based.



There are some concepts and nomenclature in Apache Kafka:

- **Cluster**: This is  a set of Kafka brokers.
- **Zookeeper**: This is a cluster coordinator—a tool with different services that are part of the     Apache ecosystem.
- **Broker**: This is a Kafka server, also the Kafka server process itself.
- **Topic**: This is a queue (that has log partitions); a broker can run several topics.
- **Offset**: This is an identifier for each message.
- **Partition**: This is an immutable and ordered sequence of records continually appended to a structured commit     log.
- **Producer**: This is the program that publishes data to topics.
- **Consumer**: This is the program that processes data from the topics.
- **Retention period**: This is the time to  keep messages available for consumption.



In Kafka, there are three types of clusters:

- Single node–single broker
- Single node–multiple broker
- Multiple     node–multiple broker



In Kafka, there are three (and just three) ways to deliver messages:

- **Never redelivered**: The messages may be lost because, once delivered, they are not sent again.
- **May be redelivered**: The     messages are never lost because, if it is not received, the message can be     sent again.
- **Delivered     once**:     The message is delivered exactly once. This is the most difficult form of     delivery; since the message is only sent once and never redelivered, it     implies that there is zero loss of any message.



The message log can be compacted in two ways:

- **Coarse-grained**: Log compacted by time
- **Fine-grained**: Log compacted by message





### Topic

- **Topic : A Particular stream of data.**

- A Topic is identified by its name.
- Topics are split into partitions.
- Each message in a single partition in kafka is uniquely identified by `64bit offset`
- To identify messages  in a topic we need:
  - 1. Topic Name
  - 2. Partition Number
  - 3. Offset Number
- Offset only have a meaning for a specific partition.
- Order is guaranteed only within a partition (not across partitions)
- Data is kept only for a limited time (default to a week)
- Once the data is written to a partition, it can't be change(immutability)
- Data is assigned randomly to a partition unless a key is provided.

 ##### Real life Example:  truck_gps
 > Say you have a fleet of trucks, each truck reports its GPS to kafka.<p>
 We can here have a kafka topic trucks_gps, that contains the position of all the trucks.<p>
 Each truck will send a message say every 20 seconds indicating its position. Each message will contain the truckid and truck    position(latitude and longitude)





### Broker

  - A Kafka cluster is composed of multiple brokers(servers)
  - Each broker is identified with its `ID(integer)`
  - Each broker contains certain topic partitions.
  - After connecting to any broker (called a bootstrap broker), you willl be connected to entire cluster.
  - A good number to get started in 3 brokers, but some big clusters have over 100 brokers.




### Zookeeper
- **Zookeeper** is the storage of the state of a Kafka cluster control information
-  Zookeeper tracks all the brokers.
- Zookeeper is used for the `controller election` either in the `very beginning` or when the `current controller crashes`.

**Get the info of Brokers in cluster**
```
zookeeper-shell.bat localhost:2161
ls /
ls /brokers
ls /brokers/ids
```



### Controller

- Controller is one of the broker elected to accept certain responsibilities
- Controller is a Single broker which serves as the active controller which is responsible for state management of partitions and replicas.
- The controller is also responsible for telling other replicas to become partition leaders when the partition leader broker of a topic fails/crashes.
- In a single node cluster, node can serve as a zookeeper  and controller as well
- The first node that starts in cluster is the controller

##### Get the controller node using the zookeeper
```
1. connect to zookeeper through zookeeper cli
./bin/zkCli.sh -server localhost:2181 
2. get the controller info
get /controller
```



### Kafka Commands

##### Command for leaders, followers partitions info
```
kafka-topics.bat --describe --zookeeper localhost:2181 --topic invoice
```

## Avro in a nutshell

- Apache Avro is a binary serialization format. 
- The format is schema-based so, it depends on the definition of schemas in JSON format. 
- These schemas define which fields are mandatory and their types. Avro also supports arrays, enums, and nested fields.
- One major advantage of Avro is that it supports schema evolution. 
- In this way, we can have several historical versions of the schema.



## Kafka Streams in a nutshell

- Kafka Streams is a library and part of Apache Kafka, used to process streams into and from Kafka. In functional programming, there are several operations over collections, such as the following:
  - `filter`
  - `map`
  - `flatMap`
  - `groupBy`
  - `join`



## KSQL in a nutshell

- With Kafka Connect, we can build clients in several programming languages: JVM (Java, Clojure, Scala), C/C++, C#, Python, Go, Erlang, Ruby, Node.js, Perl, PHP, Rust, and Swift. 
- In addition to this, if your programming language is not listed, you can use the Kafka REST proxy. 
- But the Kafka authors realized that all programmers, especially data engineers, can all talk the same language: **Structured Query Language** (**SQL**). 
- So, they decided to create an abstraction layer on Kafka Streams in which they could manipulate and query streams using SQL.
- KSQL is a SQL engine for Apache Kafka. 
- It allows writing SQL sentences to analyze data streams in real time. 
- Remember that a stream is an unbounded data structure, so we don't know where it begins, and we are constantly receiving new data. Therefore, KSQL queries usually keep generating results until you stop them.



## Kafka Connect in a nutshell

- Kafka Connect is an open source framework, part of Apache Kafka
-  It is used to connect Kafka with other systems, such as structured databases, column stores, key-value stores, filesystems, and search engines. 
- Kafka Connect has a wide range of built-in connectors. 
- If we are reading from the external system, it is called a **data source**
- If we are writing to the external system, it is called a **data sink**.
- 

