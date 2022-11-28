
# Design Tiktok

![tiktok doc](Untitled.png)

##Requirements:

- User is able to share videos
- User is able to watch videos on the FYP
- User is able to watch vdeos on "Following" Page
- User is able to Comment on the videos
- User is able to like the videos



- User is able to authicate
- User is able to create account
- User is able to modify profile and setting configuration. Private account. Change name, change location.
- The username cannot change


Extra
- User is able to livestream
- Chat in the livestream
- send stickers in livestream


1B Users

Non-Functional Requirements:
- Scalability
- Availablity. 99.999% 
(Redundancy, Replication )
Computer: Mutliple server, node, cluster
Storage: Eventual consistency

- Robustness 
- Reliability


other:
- Cost
- Deployability
- Sustaibility, modularityh, extendibility



CAP Theorem:

Sacrifice Consistency for Availability

RDBMS. ACID properties. 

Instagram, Netflix, Facebook

NoSQL -> Cassandra, 

Banq Consistency, Stock Market


LMAX System (One node) No Partition - Stock market




Capapcity Estiamtes:
- 1B Users

User Data:
-Username 
-DOB
-CreationDate
-LastLogin

1B x 100KB = 100 TB Mistake

-Statistics
-Comments
-Likes


Video Data:

1 video per user per day on average?

1B vidoes per day shared

10 MB?

10 PB per day shared

7 Gb per minute
100 MB Per second 

Video MetaData:
- Title
- Description
- Creation data
- CreatorId
- VideoId Mistake


Followers: 

UserId
Follower UserId


DataLake with Statistics
Video watch time etc.
Likes watch etc.
ML - Analytics


Grocking - System Design
Alex XU - System design interview
Youtube Videos


excalidraw.com/
alidraw.com/


https://excalidraw.com/#room=272723ef74217500ed11,b4e2uDda6aLSoa4cm9aThA
