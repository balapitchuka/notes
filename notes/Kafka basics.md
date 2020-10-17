---
title: Kafka basics
tags: [Import-b418]
created: '2019-11-24T05:21:40.521Z'
modified: '2020-10-17T20:06:49.983Z'
---

## Kafka basics:

1. Topic : A Particular stream of data.
   - A topic is identified by its name.
   - topics are split into partitions.
   - Each message within a partition gets an incremental id, called offset.
   - offset only have a meaning for a specific partition.
   - order is guaranteed only within a partition (not across partitions)
   - data is kept only for a limited time (default to a week)
   - once the data is written to a partition, it can't be change(immutability)
   - data is assigned randomly to a partition unless a key is provided.
   
 Reallife Example:  **truck_gps**
 > Say you have a fleet of trucks, each truck reports its GPS to kafka.<p>
 We can here have a kafka topic trucks_gps, that contains the position of all the trucks.<p>
 Each truck will send a message say every 20 seconds indicating its position. Each message will contain the truckid and truck    position(latitude and longitude)

2. Broker:
  - A Kafka cluster is composed of multiple brokers(servers)
  - Each broker is identified with its ID(integer)
  - Each broker contains certain topic partitions.
  - After connecting to any broker (called a bootstrap broker), you willl be connected to entire cluster.
  - A good number to get started in 3 brokers, but some big clusters have over 100 brokers.
