# Cassandra
+ Apache Cassandra is a highly available, distributed, partitioned row store
+ one of the more popular NoSQL databases used by both small and large companies all over the world to store and efficiently retrieve large amounts of data

## Why was Cassandra created?
Cassandra a CAP designation as an AP database

## Cassandra's ring architecture
+ A single-instance running in Cassandra is known as a node. 
+ A group of nodes serving the same dataset is known as a cluster or ring
+ Data written is distributed around the nodes in the cluster. 
+ The partition key of the data is hashed to determine it's token. 
+ The data is sent to the nodes responsible for the token ranges that contain the hashed token value.

## Partitioners
+ The component that helps to determine the nodes responsible for specific partitions of data is known as the partitioner. 
+ Apache Cassandra installs with three partitioners.

## Cassandra Tables
+ Also known as Cassandra column families(in older versions of Cassandra)
+ The first column of the primary key combination is known as the partition key

### Cassandra Query Language (CQL)