# HBase brief introduction

## Content:
1. [What is HBase?](#what-is-hbase)
   1. [Features](#features-of-hbase)
   2. [Advantages](#advantages-of-hbase)
2. [HBase architecture](#hbase-architecture)
   1. [HBase Regions](#hbase-regions) 
   2. [HBase Master](#hbase-master)
   3. [Zookeeper](#zookeeper)
3. [Starting to work with HBase](#starting-to-work-with-hbase)
4. [Playing with commands](#playing-with-commands)
   1. [Creating table and filling it](#creating-table-and-filling-it)
   2. [Scan and disable](#scan-and-disable)
   3. [Altering existing table](#altering-existing-table)
5. [Conclusion](#conclusion)

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
- Auto-sharding
- Auto failover
- Simple client interface

## HBase architecture

![image](https://miro.medium.com/max/1400/1*GhFrq32hXR7XNPNp6ywmmg.png)

### HBase Regions

In HBase Architecture, a region consists of all the rows between the start key and the end key which are assigned to that Region. And, those Regions which we assign to the nodes in the HBase Cluster, is what we call “Region Servers”.

Basically, for the purpose of reads and writes these servers serves the data. While talking about numbers, it can serve approximately 1,000 regions. However, we manages rows in each region in HBase in a sorted order.

### HBase Master

HBase master in the architecture of HBase is responsible for region assignment as well as DDL (create, delete tables) operations.

There are two main responsibilities of a master in HBase architecture:

a. Coordinating the region servers
Basically, a master assigns Regions on startup. Also for the purpose of recovery or load balancing, it re-assigns regions.
Also, a master monitors all RegionServer instances in the HBase Cluster.

b. Admin functions
Moreover, it acts as an interface for creating, deleting and updating tables in HBase.

### Zookeeper

To maintain server state in the HBase Cluster, HBase uses ZooKeeper as a distributed coordination service.

Basically, which servers are alive and available is maintained by Zookeeper, and also it provides server failure notification.

## Starting to work with HBase

First download a docker compose file from this repository and extract it in a folder.

After that open Gut bash in this folder and input this `docker-compose up --build -d`.

After that input this command to enter HBase shell `docker-compose exec hbase-master hbase shell`.

(If you're on windows and it doesn't work try adding `winpty` infront of commands)

Now we're ready for work!


## Playing with commands

(You can write just `create` and it will show you how to use that comand and all different formats)
![image](https://user-images.githubusercontent.com/70970346/167012612-01a7f9ee-73ee-4620-84e4-32f252c09cf7.png)

Now let's create our firts table using this command `create 'newtbl', 'knowledge'`

After that you can write `list` which this time will show our newly created table

![image](https://user-images.githubusercontent.com/70970346/167012822-af55a586-e72a-422a-8363-a3260d5cd181.png)

Now you can write `describe 'newtbl'` which will show you different information about our table
![image](https://user-images.githubusercontent.com/70970346/167013139-74f80402-83e9-41ad-a13f-6b9f10b3698c.png)

You can also write `status` or `status 'summary'`(they both show the same) and now you can see all masters running, for now we have only 1 which is hbase itself

![image](https://user-images.githubusercontent.com/70970346/167013568-ea4925ca-017a-4597-b37e-465666c9f3bf.png)

Now we can actually fill our table with something, to do that we can use command `put`.
`put 'newtbl', 'r1', 'knowledge:sports', 'cricket'`, ok so here the insert is at `r1`, column `knowledge:sports`, with a value of `cricket`. Columns in HBase are comprised of a column family prefix, `knowledge` in this example, followed by a colon and then a column qualifier suffix, `sports` in this case.
Let's add some more so that our table is not so empty, for example:

`put 'newtbl', 'r1', 'knowledge:science', 'chemistry'`

`put 'newtbl', 'r1', 'knowledge:science', 'physics'`

`put 'newtbl', 'r2', 'knowledge:economics', 'macro economics'`

`put 'newtbl', 'r2', 'knowledge:music', 'pop music'`

### Scan and disable

Now, to see what we have done, we can write `scan 'newtbl'` to see inside

![image](https://user-images.githubusercontent.com/70970346/167015651-3add7a59-83d9-4db9-b917-a21d0f4f5c5d.png)

This will show every row and time of when it was created and as you can see `'knowledge:science'` has a value of `'physics'` instead of `'chemistry'`. It happended because if you try to put another value into existing one it will just overwrite existing and put will itself there.

To scan only 1 row u can use `scan 'newtbl', 'r1'` and it will show you information about this exact row.

Or u can use `get 'newtbl', 'r1'` to get all r1 rows

![image](https://user-images.githubusercontent.com/70970346/167018085-518fd425-e0bf-481b-ba4b-8bf2552cdc2c.png)


We can also check if our table is enabled using this command `is_enabled 'newtbl'`, we have it enabeld so you will see true but now we can try to disable it using `disable 'newtbl'`.

And if we  try to scan it now we will get an error, so once it's disabled u can't do anything with it.

### Altering existing table

While it's disabled we can write `alter 'newtbl', 'test_info'` and if we will write `describe 'newtbl'` now we can see a new family `'test_info'`

![image](https://user-images.githubusercontent.com/70970346/167018728-1c5f81e8-7427-4f19-9efb-5e8237010a21.png)

## Conclusion

HBase provides a NoSQL layer to HDFS(The Hadoop Distributed File System is a distributed file system designed to run on commodity hardware.). It uses a four dimensional data model to quickly run table scans and perform real time reads/writes. HBase provides highly available and consistent reads/writes while also leveraging MapReduce for batch processing.
