# Notes [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

## Table of Contents
 - [Database](#Database)
   - [MySQL](#MySQL)
 - [Caching](#Caching)
   - [Redis](#Redis)
 - [WebServices](#WebServices)
 - [Reference](#Reference)
 

## Database
  ### MySQL  
  * [Data Types](https://dev.mysql.com/doc/refman/8.0/en/data-type-overview.html)
      * [Numeric Type](https://dev.mysql.com/doc/refman/8.0/en/numeric-type-overview.html)
      * [Date and Time Type](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-type-overview.html)
      * [String Type](https://dev.mysql.com/doc/refman/8.0/en/string-type-overview.html)
  * [ACID Model](https://dev.mysql.com/doc/refman/8.0/en/mysql-acid.html)（InnoDB Engine)
    * Atomicity
      * **Transactions** are atomic units of work that can be committed or rolled back. When a transaction makes multiple changes to the database, **either all the changes succeed when the transaction is committed, or all the changes are undone when the transaction is rolled back**.
    * Consistency
      * The database remains in a consistent state at all times, if related data is being updated across multiple tables, **queries see either all old values or all new values, not a mix of old and new values**. 
    * Isolation
      * Transactions are protected (isolated) from each other while they are in progress; they cannot interfere with each other or see each other's uncommitted data. 
      * [Isolation Level](https://dev.mysql.com/doc/refman/8.0/en/innodb-transaction-isolation-levels.html)
        - READ UNCOMMITTED
        - READ COMMITTED
        - REPEATABLE READ
        - SERIALIZABLE
      * Durability
        * The results of transactions are durable: once a commit operation succeeds, the changes made by that transaction are safe from power failures, system crashes, race conditions, or other potential dangers that many non-database applications are vulnerable to. 
    * [Security]
      * SQL Injection
    * [Normalization](https://www.mysql.tw/2013/03/normalization.html)
    * [Partitions](https://dev.mysql.com/doc/refman/8.0/en/partitioning.html)
    * [Stored Objects](https://dev.mysql.com/doc/refman/8.0/en/stored-objects.html)
      * Stored procedure
      * Trigger
      * Event
      * View
    * [Optimization](https://dev.mysql.com/doc/refman/8.0/en/optimization.html)
    * Profiling
      * [explain](https://medium.com/@sj82516/mysql-explain%E5%88%86%E6%9E%90%E8%88%87index%E8%A8%AD%E5%AE%9A%E6%9F%A5%E8%A9%A2%E5%84%AA%E5%8C%96-3e0708206ebf)
    
  * MongoDB
    * [ACID](https://www.mongodb.com/transactions) (MongoDB 4.0)
    * [CAP](https://stackoverflow.com/questions/11292215/where-does-mongodb-stand-in-the-cap-theorem)
   
## Caching  
  ### [Memcached vs. Redis](https://stackoverflow.com/questions/10558465/memcached-vs-redis)
  * Redis is more powerful, more popular, and better supported than memcached. Memcached can only do a small fraction of the things Redis can do. Redis is better even where their features overlap. For anything new, use Redis
  ### [Redis](https://redis.io/)
  * Document
  * [Persistence](https://redis.io/topics/persistence)
    * By default redis persists your data to disk using a mechanism called snapshotting.
  * [Eviction Policies](https://redis.io/topics/lru-cache)
    - noneviction
    - allkeys-lru
    - volatile-lru
    - allkeys-random
    - volatile-random
    - volatile-ttl 
  * [Data Types](https://redis.io/topics/data-types-intro)
    * Strings
    * Hashed
    * Lists
    * Sets
    * Sorted Sets
    * Geo
    * Bitmap
    * HyperLoglog
  * Transactions and Atomicity
  * [Lua Scripting](https://redis.io/commands/eval)
    * You can kind of think of lua scripts like redis's own SQL or stored procedures. It's both more and less than that, but the analogy mostly works.
  * [Pipelining](https://redis.io/topics/pipelining)
    * If you have many redis commands you want to execute you can use pipelining to send them to redis all-at-once instead of one-at-a-time.
    * ```python
      import redis
      r = redis.Redis(host='localhost', port=6379, db=0)

      # Create a pipeline instance 
      pipe = r.pipeline()

      # Send the commands to be executed in batch
      pipe.set("key1", "value1")
      pipe.get("key2")
      pipe.hgetall("key3")
      pipe.set("key4","value4")

      # execute all the buffered commands
      responses = pipe.execute()

      # get the results
      for response in responses:
          print(response)
      ```
  * Design Patterns
    * [Reliable queue](https://redis.io/commands/rpoplpush)
    * [Circular list](https://redis.io/commands/rpoplpush)
    * [Pub/Sub](https://redis.io/topics/pubsub)
      * [example](https://github.com/andymccurdy/redis-py/#publish--subscribe)
      * [Only one client can get the message.](https://stackoverflow.com/questions/7196306/competing-consumer-on-redis-pub-sub-supported) (not one to many)
    * [Distributed lock](https://redis.io/topics/distlock) (Redlock algorithm)
      * [python implementation](https://github.com/SPSCommerce/redlock-py)
      
      
## WebServices
## Reference 
  * [awsesome-interview-questions](https://github.com/MaximAbramchuck/awesome-interview-questions)
