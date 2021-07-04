# SQL vs NoSQL Database Differences 
![dgsgss](https://i.ytimg.com/vi/QwevGzVu_zk/maxresdefault.jpg)

SQL | NoSQL
-|-
1|2
-|-
SQL databases are primarily called as Relational Databases (RDBMS)   |    NoSQL database are primarily called as non-relational or distributed database.
 
SQL databases are table based databases                              |        NoSQL databases are document based, key-value pairs, graph databases or wide-column stores.

SQL databases have predefined schema                                 |        NoSQL databases have dynamic schema for unstructured data.

SQL databases are vertically scalable                                |     the NoSQL databases are horizontally scalable.

SQL databases are increasing the horse-power of the hardware         |    NoSQL databases are scaled by increasing the databases servers in the pool of resources to reduce the load.

SQL databases uses SQL ( structured query language ) for defining and manipulating the data, which is very powerful |   In NoSQL database, queries are focused on collection of documents. Sometimes it is also called as UnQL (Unstructured Query Language).


SQL database examples: MySql, Oracle, Sqlite, Postgres and MS-SQL.    | NoSQL database examples: MongoDB, BigTable, Redis, RavenDb, Cassandra, Hbase, Neo4j and CouchDb

SQL databases are good fit for the complex query intensive environment   |  NoSQL databases are not good fit for complex queries. On a high-level, NoSQL don’t have standard interfaces to perform complex queries.


SQL query language is powerful                                        | the queries themselves in NoSQL are not powerful as SQL For the type of data to be stored.
SQL databases are not best fit for hierarchical data storage         |  NoSQL database fits better for the hierarchical data storage as it follows the key-value pair way of storing data similar to JSON data.
 
 
For scalability: In most typical situations, SQL databases are vertically scalable. You can manage increasing load by increasing the CPU, RAM, SSD, etc, on a single server.   |       On the other hand, NoSQL databases are horizontally scalable. You can just add few more servers easily in your NoSQL database infrastructure to handle the large traffic.

### MySQL Community Edition
> ***MySQL database is very popular open-source database. It is generally been stacked with apache and PHP, although it can be also stacked with nginx and server side javascripting using Node js. The following are some of MySQL benefits and strengths:***

1. Replication: By replicating MySQL database across multiple nodes the work load can be reduced heavily increasing the scalability and availability of business application
2. Sharding: MySQL sharding os useful when there is large no of write operations in a high traffic website. By sharding MySQL servers, the application is partitioned into multiple servers dividing the database into small chunks. As low cost servers can be deployed for this purpose, this is cost effective.
3. Memcached as a NoSQL API to MySQL: Memcached can be used to increase the performance of the data retrieval operations giving an advantage of NoSQL api to MySQL server.
4. Maturity: This database has been around for a long time and tremendous community input and testing has gone into this database making it very stable.
Wide range of Platforms and Languages: MySql is available for all major platforms like Linux, Windows, Mac, BSD and Solaris. It also has connectors to languages like Node.js, Ruby, C#, C++, C, Java, Perl, PHP and Python.
5. Cost effectiveness: It is open source and free.



### MS-SQL Server Express Edition
***It is a powerful and user friendly database which has good stability, reliability and scalability with support from Microsoft. The following are some of MS-SQL benefits and strengths:***
#### What kind of data is a good fit for an SQL database?

1. Integrated Development Environment: Microsoft visual studio, Sql Server Management Studio and Visual Developer tools provide a very helpful way for development and increase the developers productivity. 


#### What kind of data is a good fit a NoSQL database?

2. Disaster Recovery: It has good disaster recovery mechanism including database mirroring, fail over clustering and RAID partitioning.

#### Which type of database is best for scalability?


3. Cloud back-up: Microsoft also provides cloud storage when you perform a cloud-backup of your database.

### Redis
***Redis is another Open Source NoSQL database which is mainly used because of its lightening speed. It is written in ANSI C language. The following are some of Redis benefits and strengths:***

1. Data structures: Redis provides efficient data structures to an extend that it is sometimes called as data structure server. The keys stored in database can be hashes, lists, strings, sorted or unsorted sets.
2. Redis as Cache: You can use Redis as a cache by implementing keys with limited time to live to improve the performance.

3. Very fast: It is consider as one of the fastest NoSQL server as it works with the in-memory dataset.




### What does SQL stand for?
> SQL stands for Structured Query Language, a language for manipulating and talking about data in databases. ... SQL, as a data retrieval language, is an industry standard; All relational database products, SQL is the mechanism, language and syntax used to retrieve data from ar database.


### What is a realational database?
> A relational database is a type of database that stores and provides access to data points that are related to one another. ... The columns of the table hold attributes of the data, and each record usually has a value for each attribute, making it easy to establish the relationships among data points.

### What type of structure does a relational database work with?
> The relational model means that the logical data structures—the data tables, views, and indexes—are separate from the physical storage structures. This separation means that database administrators can manage physical data storage without affecting access to that data as a logical structure.

### What is a ‘schema’?
> A schema is a cognitive framework or concept that helps organize and interpret information. Schemas can be useful because they allow us to take shortcuts in interpreting the vast amount of information that is available in our environment.

### What is a NoSQL database?
> MongoDB, CouchDB, CouchBase, Cassandra, HBase, Redis, Riak, Neo4J are the popular NoSQL databases examples. MongoDB, CouchDB, CouchBase , Amazon SimpleDB, Riak, Lotus Notes are document-oriented NoSQL databases,. Neo4J, InfoGrid, Infinite Graph, OrientDB, FlockDB are graph databases.

### How mongo  does it work?
> MongoDB is an object-oriented, simple, dynamic, and scalable NoSQL database. It is based on the NoSQL document store model. The data objects are stored as separate documents inside a collection — instead of storing the data into the columns and rows of a traditional relational database.

### What does a MongoDB collection consists of?
> A document is a representation of a single entity of data in the MongoDB database. A collection consists of one or more related objects. A major difference exists between MongoDB and SQL, in that documents are different from rows. Row data is flat, with one column for each value in the row.

### Which is more flexible - SQL or MongoDB? and why?
> sQL Databases Record While MongoDB is more flexible and ensures high and diverse data availability, a SQL Database operates with the ACID (Atomicity, Consistency, Isolation, and Durability) properties and ensures greater reliability of transactions


### Why is SQL better than MongoDB?
> MongoDB is almost 100 times faster than traditional database system like RDBMS, which is slower in comparison with the NoSQL databases. ... MongoDB supports deep query-ability i.e we can perform dynamic queries on documents using the document-based query language that's nearly as powerful as SQL.



### What are the disadvantages of using a NoSQL database like MongoDB?
> There are a few disadvantages of the MongoDB NoSQL database as well.
1. MongoDB uses high memory for data storage.
2. There is a limit for document size, i.e. 16mb.
3. There is no transaction support in MongoDB.


##### References

[thegeekstuff](https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db/?utm_source=tuicool)


[mongoosejs](https://mongoosejs.com/docs/api.html#Model)





