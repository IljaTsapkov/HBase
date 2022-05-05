# HBase brief introduction

## Content:
1. [What is HBase?](#what-is-hbase)
   1. [Features](#features-of-hbase)
   2. [Advantages](#advantages-of-hbase)
2. [What is Cloudera Quickstart VM?](#what-is-cloudera-quickstart-vm)
3. [What is Hue?](#what-is-hue)

## What is HBase?
HBase is an open-source, NoSQL, distributed big data store. Used when you need random, realtime read/write access to your Big Data. Its goal is the hosting of very large tables -- billions of rows X millions of columns -- atop clusters of commodity hardware.

### Features of HBase
- Linear and modular scalability.
- Strictly consistent reads and writes.
- Automatic and configurable sharding of tables
- Automatic failover support between RegionServers.
- Convenient base classes for backing Hadoop MapReduce jobs with Apache HBase tables.
- Easy to use Java API for client access.
- Block cache and Bloom Filters for real-time queries.
- Query predicate push down via server side Filters

### Advantages of HBase
- It can handle very large volumes of data
- Supports scaling out in coordination with Hadoop file system even on commodity hardware
- Fault tolerance
- License free
- Very flexible on schema design/no fixed schema
- Can be integrated with Hive for SQL-like queries, which is better for DBAs who are more familiar with SQL queries
- Auto-sharding
- Auto failover
- Simple client interface

## What is Cloudera Quickstart VM?
Cloudera QuickStart VM includes many things. It requires VirtualBox and has Cloudera Manager which is the main feature we are going to use because it controls everything. It has many services but we are interested in HBase, Hue and Impala. Overall Cloudera Quickstart is just a thing from Cloudera company which includes most of their products.

## What is Hue?
Hue is a web-based interactive query editor that enables you to interact with data warehouses. You can use the HBase Browser application in Hue to create and browse HBase tables.
The HBase Hue app enables you to insert a new row or bulk upload CSV files, TSV files, and type data into your table. You can also insert columns into your row.


## Starting with Cloudera Quickstart VM
After downloading, mounting and launching you will be greeted wit this screen
![image](https://user-images.githubusercontent.com/70970346/166999932-3816e44e-1155-423a-a9b4-e46135bf1690.png)
