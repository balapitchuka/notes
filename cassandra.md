- Apache Cassandra
  - Overview
  - NoSQL

- Installation
- Architecture
  - Partitions
  - Replication
  - Data Versioning
  - Consistency
  - Failovers
  - Query Service
  - Storage
 
- Cassandra Query Language(CQL)
  - Data Type
  - User Defined Types
  - Create, Use, Alter, Drop - KeySpace
  - Create, Alter, Drop, Truncate - Table
  - Select, Insert, Update, Delete and Batch Statement
  - Arithmetic Operatorss
  - Secondary Indexes
  - Functions - Scalar and Aggregate
- Apache Cassandra - Architecture Overview
  - Storage Engine
  - Guarantees
  - Snitch
- Data Model
- Operations Development/Admin Operations
- Tools for development and admin functionality



## Overview
- Apache Cassandra is a 
  - Free and open source 
  - Scalable and Distributed wide column store NoSQL database management system 
  - Designed to handle large amount of data across multiple commodity servers providing high availability with no single point of failure
  - Multiple nodes called as cluster, data is distributed across multiple nodes
  - Highly performant database (read and write are efficient)
  - Fault Tolerant (if any node goes down still it operates)
  - Supports multiple peta bytes of storage without satrifying efficient read and write operations

## Architecture
Partitioning (How Apache Cassandra distributes data in the cluster)
- When ever we store data in cassandra it is distributed across nodes in cluster using partitioning
- For partitioning, it uses `Consistent Hashing`
  - Cassandra is a key value store, key being the primary key
  - Internally Cassandra does hashing of key and decides which nodes to store the data
  - Normal hashing technique will have issues with hashing key and chossing the node in case we remove some node or add more nodes, also some nodes may store more data then other
  - Hence Cassandra uses something called as Consistent Hashing
  - Consistent Hashing works on the principle of Tokens and Rings


Ring & Token



## Why Writes in Cassandra Are So Fast?
- Cassandra is a distributed database that support incredible write throughout and is known for its scalability and availability. It’s great at supporting applications with very high write throughput.
- To achieve this high performance, Cassandra has a unique write pattern. Cassandra has a few different data structures that it uses
  - Commit Log (Disk)
    - The first thing Cassandra does when a write comes in is write it to its commit log. The commit log is an append only log of records for durability purposes. If a node goes down during a write or data is damaged, Cassandra can use its commit log to replay all the events and reconstruct the database.
  - Memtable (Memory)
    - Cassandra maintains an in-memory data structure called Memtable. After writing to the commit log, Cassandra will write your data in its Memtable which resides in memory. Once the data is written to the memtable, the node acknowledges the write as successful.
    - Cassandra is able to recover in those cases because of its commit log and write redundancy. The commit log lets Cassandra recover lost data in case the Memtable is wiped out. The write is also replicated to multiple other nodes, so if one node loses its Memtable data, there are mechanisms in place for eventual consistency.
    - Memtable is used as a temporary buffer by Cassandra. Periodically, Cassandra flushes its content from Memtable to its disk data structure called SSTable. Let’s look at that now.
  - SSTable (Disk)
    - Cassandra contains multiple SSTables in disk where data is actually persisted.
    - There are two ways Cassandra can decide when to flush its Memtable content to disk:
    - Periodically. It will write its content to disk after a fixed period of time passes.
      Memtable size. It will flush the memtable every time the memtable reaches a fixed size, let’s say 4 MB.
    - Once data is written in the SSTables, the Memtables are wiped clean, ready for more incoming data.
- All three of these data structures are involved in every write process.


