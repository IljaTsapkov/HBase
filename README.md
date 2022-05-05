# HBase brief introduction

## Content:
1. [What is HBase?](#what-is-hbase)
   1. [Features](#features-of-hbase)
   2. [Advantages](#advantages-of-hbase)
2. [What is Cloudera Quickstart VM?](#what-is-cloudera-quickstart-vm)
3. [What is Hue?](#what-is-hue)
4. [Starting with Cloudera Quickstart VM](#starting-with-cloudera-quickstart-vm)
5. [Playing with commands](#playing-with-commands)

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
After downloading, mounting and launching you will be greeted wit this screen:
![image](https://user-images.githubusercontent.com/70970346/166999932-3816e44e-1155-423a-a9b4-e46135bf1690.png)
After that you can press the browser icon:
![image](https://user-images.githubusercontent.com/70970346/167001875-f44efd76-3f0a-4357-9558-3626ff659d98.png)
After opening browser you will be greeted with a welcoming page but we are going straight to Hue:
![image](https://user-images.githubusercontent.com/70970346/167003112-ab0527ee-30db-4eb2-9219-d757c7de6112.png)
You will see a login screen and here are credentials:
- User: couldera
- Password: couldera

## Playing with commands
After entering Hue you should open terminal where we will write all commands.
Terminal is located here:
![image](https://user-images.githubusercontent.com/70970346/167005555-5a315e5e-174f-4500-a268-6f6df679312f.png)
Now you can start writing commands.

First we will enter hbase shell, write `hbase shell`

After that you can write `list` to see all tables(this won't show anything because we haven't created any tables yet).

Now we can create our first table using this command `create 'newtbl', 'knowledge'`, this will create table 'newtbl' with family of 'knowledge'.


(You can write just `create` and it will show you how to use that comand and all different formats)
![image](https://user-images.githubusercontent.com/70970346/167012612-01a7f9ee-73ee-4620-84e4-32f252c09cf7.png)

After that u can write `list` which this time will show our newly created table

![image](https://user-images.githubusercontent.com/70970346/167012822-af55a586-e72a-422a-8363-a3260d5cd181.png)


