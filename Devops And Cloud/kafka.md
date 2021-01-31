## Kafka Basics:

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

 ### Real life Example:  truck_gps
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