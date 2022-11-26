https://github.com/donnemartin/system-design-primer




![Screenshot](screenshot.png)



TYPICAL SIZE CALCULATION REFERNCES

number= 4 bytes
20 bytes
100 bytes per thing

Get the data storage for each things
1 number = 8 bytes
1 float = 8 bytes
date. = 8 bytes
char = 2 bytes * character (sometimes 1 byte)
1 string = 4 bytes * length = 200
pastebin averge = 10kb
UUID is a 128-bit number  = 16 bytes

1 video = 10 mb 
1 picture = 1 mb

video view 1:200  ratio

one minute of video needs 50MB of storage  on youtube pass video chunks
 (a video chunk)

a photo is 200KB
video is 2MB  on twitter

Get the limits

Memory limits
Up to 100 gb in memory at the same time

SQL db limits  for one instance
1,000,000 row reads per second
100,00 row updates per second

50K concurrent connections at any time for any server
10K such servers for 500M connections

GB or TB or GB would require either SQL or bigData

Let’s say each tweet has 140 characters and we need two bytes to store a character without compression. Let’s assume we need 30 bytes to store metadata with each tweet (like ID, timestamp, user ID, etc.). Total storage we would need:  Tweet
100M * (280 + 30) bytes => 30GB/day 


ElasticSerach latency 250ms

7x10 times faster grpc



TYPICAL SERVICES NEEDED
User Service
Search Service
Notification Service  (email?,sms?,page?)(with queue before)
Authentication Service
RateLimiting Service
Recommendation Service 
Data Verification Service 
Tracking / Monitoring
Internalizaiton Service
Hot Trending Service (inputs from live data of stream processor cache)
Cleanup Service (batch service)
Pre-generate Data for key lookup
Synchronization Service (with message queue before and after)
Chunking ( seperating in chunks)
Indexing Service (with queue before)
Duplication Service (with queue before)
User Status Service 
Encoding Service ( with queue before)
Personalisation Service (history, search, location, language)
Ranking Service







Questions to ask:

Is it Mobile App? Browser App? or Both? 

Is the app in english only?

What are the most important features for the product? 

How many users? Rate of Growth new users per month?

 How fast does the company anticipate to scale up? What are the anticipated scales in 3 months, 6 months, and a year? 

Who are the people who will use this?

Read to Write Ratio?

How much data needs to be supported?

Requirements in terms of Latency?

How many nines of availability?

Is this running in the cloud or on premise?

What is the company’s technology stack? What existing services you might leverage to simplify the design? 

What about cost, deployability, agility, configurability, elasticity, evolvability, fault-tolerance, integration, simplicity, scalability, performance, testability?



Is there a predefined architecture style or communication style or storage type?

What actions do we need to support for this system? 


Test ? Photos? Videos?

Front-end?

Trending Topics?

Push Notification?

Offline Access?







Steps in the system design:

1. Understand and clarify
2. List the Nonfunctional Requirements Scope
3. List the Functional Requirements Scope
4. Do memory BOE estimation for total memory if needed In memory?
5. Do processing BOE estimation for QPS  if needed Distributed?
6. Design
	1. Identify Architecture Style Approaches if needed
	2. Find the Actors / Actions or Event Storming  if needed
	3. List APIs 
	4. Find the Domain Entities or Objects if needed
	5. Draw E/R  diagram if needed 
	6. Draw the class diagram if needed
	7. Draw the High Level Architecture Technical Digram and Domain Diagram of Approaches
7. Special DS and Algorithms
	1. DB specific optimization approaches if needed
	2. Cache Specific optimization  approaches if needed
	3. Load Balancing Specific optimization approaches if needed
	4. Application Specific optimization approaches if needed
	5. Communication Specific Optimization approaches if needed
	6. Best Approach Overall
8. End to End what happens to a user


Extra Topics:

- Architecture Fitness Functions 
- DevOps 
- Security
- Networking
- User Interface
- Cost Analysis
- Risk Analysis
- Extra functionalities 


Architecture Domain Styles
- monolith 
- microservices
- service based

Architecture Technical Styles
- event-driven
- server less (deployment style)
- layered
- Service Oriented Architecture
- Multi-tenant
- Kernel Based
- LMAX 
- Space Based

Architecture communication choice
- Asynchronous vs Synchronous
- Orchestrated vs Choreographed
- Consistent vs Eventually consistent


Databases

- RDBMS stores rows
	- Relational: Mysql, Oracle, SQLServer, MariaDB, H2, SQLite
	- Object-relational: Postgresql
	- Embedded Cache: H2, SQLite
	- Distributed: CockroachDB
- NoSQL stores objects
	- Distributed Documents: Mongodb, CouchDB
	- Distributed Columns: Cassandra, HBase, ScyllaDB
	- Distributed Key-value: DynamoDb
	- Embedded Key-value: RocksDB
	- Graph: Neo4J , Neptune
	- Distributed Graph: Nebula, Titan 
	- Distributed Search: Elastic Search
	- Distributed TimeSeries: Druid
	- TimeSeries: Prometheus
	- Distributed File: HDFS, Cloud File
	- Distributed Object Store: S3
	- Distributed Key-value Cache: Redis, memcached


Typical Storage Combos

Combo 1: S3  + Spark + EMR or Glue.  Or Cloud file
Benefit: Cost+ and Scale
Downside: Slow search and processing

Combo 2: HDFS + Hive + Hadoop
Benefit: Cost++ and Scale
Downside: setup the nodes, slow search

Combo 3: ElasticSearch or ELK 
Benefit: Fast Search, Custom Search: Fuzzy Search, Negative search, customer search
Downside: Setup the nodes, Cost

Combo 4: Dynamo + Indexes
Benefit:Cost, Fast Search
Downside: Cost, Only Exact Search


Messaging Technology 
Stream Brokers: Kafka, Spark Streaming, Kinesis
Queue Broker: RabbitMQ, SQS
Notification Broker: SNS

Data Processing Technologies
Big Data: Spark, Hadoop, Hive, EMR, Serverless Glue
Stream Processor: Kafka Streams, Spark Streaming, Flink, Storm, Kinesis Firehose, Kinesis Analytics






General techniques to scale

- Distributed computing
- Load Balancing
- Auto Scaling
- Multiple DataCenter
- Caching
- Sharding Databases
- Separating read and writes
- Removing ACID and Consistency
- Indexing
- Removing Joins 
- Reactive design
- Asynchronous design
- Stateless design
- LMAX for large amount of in memory transactions
- Space Based for high elasticity



- Axes of Scale
- Vertical
- Horizontal
- Sharding


Distributed Patterns
- Bloom Filters to find the location of data
- Consistent Hashing to balance load when the number of servers varies
- HeadBulk 
- Circuit break
- Rate Limiting 
- Backpressure 
- Distributed Locks
- Gossip protocol
- 2PC
- 3PC
- BFF Pattern -one backend for each type of frontent
- Lazy Evaulation




Extra concepts

- Cloud vs On Premise
- Auto Scaling - helps (EBS, Kubernetes)
- Containers - helps to Standardize environments
- Observability
	- Logs
	- Metrics
	- Traces


Security
- Encrypted Communication using HTTPS TLS SSL
- Store sensitive information in encrypted format
- Remove unwanted sensitive information from logs and databases
- Use Firewalls, Subnets, VPC
- Use Least Privilege Permissions
- DDOS prevention


Event Driven Architecture
- Type of Events:
	- Event Source  e.g. git changes can be reconstructed
	- Notification
	- State change
- Saving Data To both messaging system and database:
	- 2PC
	- Use triggers
	- CDC 
	- Use a batch with an Outbox table
	- Use a batch with last Update Date
- Patterns
	- event forward: confirm with ACK from last recipient
	- Thread delegate
	- Multiple Broker for load balancing
	- Supervisor or orchestrator for elasticity
	- Ambulance for different priority messaging


Types of Communication:
- REST
- Web Sockets
- RPC
- SOAP
- Server Side Events
- GraphQL
- HTTP
- UDP
- TCP
- Specialized
	- SMTP
	- APMQ
- RTMP / SRP


Caching Techniques
- Cache Policy
	- LRU
	- Random
	- LFU
	- MRU
	- LIFO
	- FIFO
- Distributed 
	- Sharded 
	- Replicated 
- Embedded
- Multi Thread vs single Thread
- Type of Write
	- write through cache
	- write back cache


Load Balancing Techniques
- Policies
	- Round Robin
	- Random
	- Based on Server Load
		- number of connections
		- response time
		- bandwith
	- User IP
	- User Location
	- Content Specific
- Types
	- Network 
	- Application 
	- Gateway








Least Connection Method — This method directs traffic to the server with the fewest active connections. This approach is quite useful when there are a large number of persistent client connections which are unevenly distributed between the servers. 
• Least Response Time Method — This algorithm directs traffic to the server with the fewest active connections and the lowest average response time. 
• Least Bandwidth Method - This method selects the server that is currently serving the least amount of traffic measured in megabits per second (Mbps). 
• Round Robin Method — This method cycles through a list of servers and sends each new request to the next server. When it reaches the end of the list, it starts over at the beginning. It is most useful when the servers are of equal specification and there are not many persistent connections. 
• Weighted Round Robin Method — The weighted round-robin scheduling is designed to better handle servers with different processing capacities. Each server is assigned a weight (an integer value that indicates the processing capacity). Servers with higher weights receive new connections before those with less weights and servers with higher weights get more connections than those with less weights. 
• IP Hash — Under this method, a hash of the IP address of the client is calculated to redirect the request to a server. 








Distributed Search
	- Store Index in one DB and data in another DB
		- Use a cache for the Index
	- Use Elastic Search
		- Use a cache for the Index

Encoding
- sha256
- md5
- Using base64 encoding, a 6 letter long key would result in 64^6 = ~68.7 billion possible strings Using base64 encoding, an 8 letter long key would result in 64^8 = ~281 trillion possible strings 

When To Split Services? Granularity
- Clear Logically / Simplicity
- Code Changes Frequently (deployment)
- Scalability
- Fault Tolerance
- Access Control
- Distributed Transaction
- Data Dependency
- Lots of Choreography

When to choreograph?
- responsive
- performant
- less couple

When to orchestrate?
- centralized
- control
- error handling




Integration Patterns
- Shared File
- Shared DB
- Message
- RPC


Main Differences SQL and noSQL
- SCALE
	- max out at a couple thousand query per second... varies based on many things... 
	- 100,000 or millions of QPS
	- Partition a RDBMS, it's not recommended
	- NoSQL are typically partionned
	- Master slave like Mongodb vs Ring Consistent hash like cassandra, dynamo, bigtable
- FORMAT
	- Row oriented
	- Column Oriented
	- Document Oriented
	- Graph DB
	- Search DB 
- STRUCTURE
	- structured data vs unstructured data
	- document
	- Most DB were RDBMS 90s - beginning 2000s
	- Cheap storage and fast storage and more large scale 
- CONSISTENCY (CAP THEOREM) 
	- eventual consisten, RDBMS are consistent
- JOINS 
	- possibility to join