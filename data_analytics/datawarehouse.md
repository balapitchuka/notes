
## BigData


## Data Warehouse vs Database#

## Big Data vs Data Warehouse

# What is Data Warehouse?

- A Data Warehouse is a large store of data that’s collected from multiple different sources within a business.A data warehouse is used as storage for data analytic work (OLAP systems), leaving the transactional database (OLTP systems) free to focus on transactions. With a significant amount of data kept in one place, it’s now easier for businesses to analyze and make better-informed decisions.

- A data warehouse is a dumping ground for data from various systems (e.g., sales stack, marketing stack, CRM, etc.) that uses online analytic processing (OLAP) to query that data for better business insights.

- Data warehouses help you run logical queries, build accurate forecasting models, and identify impactful trends throughout your organization.


### What is Data Mart?
- A data mart is an area within a data warehouse that stores data for a specific business function.

Example:
- So, let's say that you build your entire data warehouse. That's great! But, your sales team is going to be using that data warehouse in a vastly different way than your legal team. And, certain workflows and data sets are only valuable to certain teams. Data marts are where all of those team-specific data sets are stored, and queries are processed.


Data modeling typically takes place at the data mart level and branches out into your data warehouse. It's the logic of how you're storing data in relation to other data.

The three most popular data models for warehouses are:

- Snowflake Schema
- Star Schema
- Galaxy Schema



### Apache Parquet
- Parquet is an open source file format available to any project in the Hadoop ecosystem. 
- Apache Parquet is designed for efficient as well as performant flat columnar storage format of data compared to row based files like CSV or TSV files.




### What is Presto?

- 100% open source distributed ANSI SQL query engine for Big Data(for running interactive analytical queries against datasources of all sizes
  ranging from gigabytes to petabytes)
- Presto was designed and written from the ground up for interactive analytics while scaling to the size of organisations
  like Facebook
- Facebook uses presto for interactive queries against several internal datastores including that 300 petabytes data
  warehouse 
- A huge testament to Preesto's scalability and performance distributed under the apache license and now supported by   teradata
- Modern architecture and implementation
- Proven scalability and performance
- Optimized for `low latency`, `interactive querying`
- Cross platform query capability, not only SQL on Hadoop
- Distributed under the Apache license, now supported by  Teradata
- Used by a community of well known, well respected technology companies like Facebook, Airbnb, Netflix, Groupon etc


### History of Presto
- FALL 2018 : Facebook open sources `Hive`
- FALL 2012 : 6 developers start Presto development
- Facebook commence development effort of presto in 2012
- Spring 2013 :  Presto rolled out within Facebook
- FALL 2013 : Facebook opensources Presto
- FALL 2014  : 88 Releases, 41 Contributors, 3943 Commits
- Spring 2015 :  98 Releases, 65 Contributors, 4587 Commits  and Teradata joins Presto community and offers support 


## OLAP
- Online Analytical Processing

## Big Data file formats

- **Text/CSV Files**: These are the usual delimited files that you normally see for most raw.
- **Avro**: Apache Avro is a data serialization system that provides a compact, fast binary format. It relies on schemas to make sense of the data in the file.
- **Parquet**: Apache Parquet is a columnar storage format that can be used by different projects in the Hadoop ecosystem. It is built to support very efficient compression and encoding schemes.
- **ORC (optimized Row Columnar)**: In this format data is stored in a hybrid fashion, it stores collections of rows and within a collection different columns. It also introduces indexing and statistics like min and max.


## HDFS

## Map Reduce

## YARN(Yet Another Resource Manager)
- YARN can be thought of as analogous of an operating system for a cluster.

YARN has two major responsibilities
- Management of cluster resources such as compute, network, and memory
- Scheduling and monitoring of jobs

YARN achieves these goals through two long-running daemons:
- Resource Manager
- Node Manager

## Flume
- Flume is known as a distributed, trusted, and accessible service for efficiently gathering, aggregating, and moving a lot of log data

## SQOOP

## Hive
- Map Reduce is difficult and for a few developers, a totally unique method for handling data processing than they are conversant with
- The most widely recognized language to manage data is SQL, also, Apache Hive is referred to as a project that allows you develop SQL alike warehouse of your data on Hadoop top.
## Pig
- Apache Pig offers a high-level scripting language, popularly used for the writing of data pipelines in the world of Hadoop.
- The scripting language is known as Pig Latin.

## Spark

## HBase


