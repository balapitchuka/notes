# Apache Spark

## Big Data History

### References
- [Google File Systeem -2003](https://ai.google/resarch/pubs/pub51)
  - Data storage and management problems
- [MapReduce - 2004](https://ai.google/research/pubs/pub62)
  - Data processing and transformation problems

After google published these papers, open source community liked the ideas very much and that formed the basis for the design and development of similar open source implementation
- HDFS (Hadoop Distributed File System)
  - Distriubted file system over a cluster of computer/nodes
  - Helps us to combine storage capacity of hundreds of computers and use it as a unified storage system
- Hadoop MapReduce
  - Distributed processing over and above HDFS 

Because of this popularity of Hadoop, many other solutions are developed on the top of Hadoop and open sourced by many organisations
Examples:
- Pig
- Hive
- Spark
  - Started as an effort to simplify and improve the Map Reduce Framework


## Spark
- Distributed processing engine
- Does not do cluster management and storage management
- All we can do with spark is to run data processing workloads and that part is managed by spark compute engine
- Spark compute engine is responsible for 
  - Breaking the data processing work into smaller tasks and scheduling those tasks on the cluster for parallel execution providing data to these tasks, managing and monitoring the tasks,provide us fault tolerance when job fails
  - It also interacts with cluster manager and storage manager to achieve above things

Spark Cluster Manager
- YARN
- Kubernetes
- Mesos

Spark Storage Manger
- HDFS
- s3
- Azure Blob
- GCS
- CFS

Data crunching refers to key initial steps required to prepare large volumes of raw data for analysis


