References
- [DataEngineering Tutorials](https://www.startdataengineering.com/)



#### 10 Key skills, to help you become a data engineer

1. Linux
Most applications are built on linux systems so it is crucial to understand how to work with them. The key concepts to know are

File system commands, such as ls, cd, pwd, mkdir, rmdir

Commands to get metadata about your data, such as head, tail, wc, grep, ls -lh

Data processing commands, such as awk, sed

Bash scripting concepts, such as control flow, looping, passing input parameters

2. SQL
SQL is crucial to access your data whether it be for running analysis or for use by your application. The key concepts to know are

Basic CRUD, such as select, where, join (all types of joins), group by, having, window functions

SQL internals, such as index: different types and how they work, transaction concepts such as locks and race conditions

Data modeling, OLTP data modeling using normalization and OLAP data modeling schemas like star and snowflake schemas.

3. Scripting
Knowledge of a scripting language such as bash scripting or python is very helpful to automate multiple steps required for processing data. The key concepts to know are

Basic DS and concept, such as list, dictionaries, map, filter, reduce

Control flow and looping concepts, such as if, for loop, list comprehension(python)

Popular data processing abstraction library such as pandas or Dask in Python

4. Distributed Data Storage
Knowledge of how distributed data store such as HDFS or AWS S3 works. Concepts like data replication, serialization, partitioned data storage, file chunking

5. Distributed Data processing
Knowledge of how data in processed in a distributed fashion. The key concepts to know are

Distributed data processing concepts, such as Mapreduce, in memory data processing such as Apache Spark

Different types of joins across data sets, such as map side and reduce side joins

Common techniques and patterns for data processing such as, partitioning, reducing data shuffles, handling data skews on partitioning

Optimizing data processing code to take advantage of all the cores and memory available in the cluster

6. Building data pipelines
Knowledge of how to connect different data systems to build a data pipeline. The key concepts to know are

A data orchestration tool, such as airflow

Common pitfalls and how to avoid them, such as data quality checks after processing

Building idempotent data pipelines

7. OLAP database
Knowledge of how OLAP database operates and when to use them. The key concepts to know are

what is a column store and why it is better for most types of aggregation queries

Data modeling concepts such as partioning, fact and dimensions, data skew

Figuring out client data query pattern and designing your database accordingly‍

8. Queuing systems
Knowledge of queuing systems and when and how to use them. The key concepts to know are

What is a data producer and a consumer

Knowledge of offsets and log compaction‍

9. Stream processing
Knowledge of what stream processing and how to use them. The key concepts to know are

What is stream processing and how is it different from batch processing

Different types of stream processing such as Event based processing and micro batching

10. JVM language
Knowledge of a JVM based language such as Java or Scala will be extremely useful, since most open source data processing tools are written using JVM languages. e.g Apache Spark, Apache Flink, etc
