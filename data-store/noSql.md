**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [No SQl data storages](#no-sql-data-storages)
	- [Redis](#redis)
	- [Cassandra](#cassandra)
	- [MongoDB](#mongodb)
	- [CouchDB](#couchdb)
	- [Apache HBase](#apache-hbase)
	- [Accumulo](#accumulo)
	- [Gora](#gora)
	- [Trevni](#trevni)
	- [References](#references)

No SQl data storages
====================

Redis
-----
strong point - storing moderate amount of fast changing data  
live/structured data  
everything in memory -  hence large memory usage  
complex data strucures like hash, sorted set  
ideal for caching  
logs updates to disk sequentially, low overhead persistence  
written in C  
single threaded  
no multicore support  
transaction  
pub-sub - extremely fast  

Cassandra
---------


MongoDB
-------


CouchDB
-------
strong point - storing large amount of rarely changing but heavily indexed data  
document store  
complex indexes but simple structure  
require regular compaction - everyhting re-read and re-written back to disk  
very low memory usage  
multicore support  
clustering using BigCouch  
written in Erlang  

Apache HBase
------------


Accumulo
--------

Gora
----
in memory data model and persistence for big data  

Trevni
------
columnar file format for hdfs  
designed afer google's Dremel  

References
----------
http://kkovacs.eu/cassandra-vs-mongodb-vs-couchdb-vs-redis  
CouchDB vs Redis - http://ai.mee.nu/is_couchdb_the_anti-redis  
https://moot.it/blog/technology/redis-as-primary-datastore-wtf.html  

