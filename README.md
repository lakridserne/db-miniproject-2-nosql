# db-miniproject-2-nosql
 
## Intro
Our assigment is to select two or more databases of different NoSQL types and to compare their features
and performance in storing, scaling, providing, and processing big data.

The reason we have chosen to use MongoDB and Neo4j for this project assignment, is because we figured out that those
two databases are completely different and we thought it then would give great diffrent results, when we are comparing
the data, so we could get a better overview for what each database is best suited for after reviewing our results
 
## Problem statement 
It's interesting to analyze twitter followers and by that being able to make statistics on certain things regarding those followers. At the same time, we wanted to better understand Neo4J and MongoDB. For this reason we desided to import the data into our databases. We selected the two databases and want to compare them to each other. 

## Motivation 
 We want to research and experiment the difference bewtween MongoDB and Neo4J in reagads to scalability, performance and compare the two databases features. 
Our first thought was to do research on how to use one of the following operations by inserting data into the to the two databases. Then we want to comparer the speed of the two databases.

It would be intressting to use som big-data so we can better see the difference bewteen each database and get overview on how it effects our two databases. 

## Activity
// desciption of file
We have a big file that has a size around 24GB that tells us how many followers each twitter profile has.
The file contains a list of IDs on all the follwers and the profiles being followed.

1)  Import stament: This statement import the "Twitter_data.csv" file.

  Neo4J
               
        USING PERIODIC COMMIT 500
        LOAD CSV FROM 'file:///twitter_data.csv' AS line
        CREATE (:Twitter_follower { following: line[0], follower: line[1] } );
 


     
     
   MongoDB
                   
        mongoimport --type csv -d twitterFollowers -c followers --headerline --drop twitter_data.csv
     
During the import we could clearly see that MongoDB is more suited for large datasets, whereas Neo4J is more tailered to make   graphs. This was for example due to the way the import worked - MongoDB was able to import a large file relatively quickly comprared with Neo4J.

2)    Database operations:
   Our goal is to compare Neo4J and MongoDB to compare performance, scaling and storage in processing big data.
   In order to see this, we have opted to insert data into MongoDB and Neo4J along with retrieving selected data again.


3)  Selecting appropriate criteria for comparison (storage space);
    
      Neo4J:
      
      ```
      295GB
      ```
     
     MongoDB:
     
     ```
     43GB  
      ```
      
     Cap
     
     CAP is a way to handle if networked database servers loose their connectivity with each other. What will happen? CAP will make us choose between consistency and availablity.
     
     This basically means choosing between cancelling the operation if the network fails, or proceed with the operation. If we choose to proceed with the operation, we get high availablity, but the data might not be very consistent. On the other hand, if we just cancel the operation, consistency is high, however, the database risk not being available if the server cannot talk to the other servers.
     
     MongoDB:
     
     MongoDB is strongly consistent by default - if you do a write and then do a read,
     assuming the write was successful you will always be able to read the result of the write.
     This is because MongoDB is a single-master system and all reads go to the primary by default.
     If you enable reading from the secondaries then MongoDB becomes eventually consistent where it's possible to read out-of-date results.
     
     Neo4J:
     
     In our understanding Neo4j has no facility for partitioning or sharding and so is not a distributed database.
     So the CAP theorem doesn’t really apply. However there are two clustering modes available in the enterprise edition.
     
     
     
     ACID
     
     ACID is practical because we can ensure that a transaction is always successful - and if it's not, none of the transactions go through. This way, we don't end up with inconsistent or corrupted data, or data that doesn't make sense.
     
     MongoDB:
      
      After the release of version 4.0, MongoDB now has support for multi-document ACID transactions,
      which now make it a ACID-compilant at the document level.
     
     
     Neo4j:
     
     Neo4j is ACID compliant and supports properties of ACID, a link to full overview can be found [here] (https://www.graphgrid.com/neo4j-is-designed-to-be-your-source-of-truth-database)
4)
  Neo4J:
  
  Get all users being followed by a specific user ID
      
      MATCH (n {following: '107'}) RETURN n;
      
CREATE Twitter follower

      CREATE (Twitter_follower { follower: '1234', following: '5678' }) RETURN Twitter_follower;
      
![Neo4J INSERT QUERY](https://github.com/lakridserne/db-miniproject-2-nosql/blob/master/100655238_246389093126619_4640154904206245888_n.png "Logo Title Text 1")
      
  MongoDB
  
 Get all users being followed by a specific user ID      
 
      db.followers.find({following: 107 })
      
      
      
 CREATE Twitter follower
 
      db.followers.insertOne( {"following": 1234, "follower": 5678})
      
![MongoDB INSERT QUERY](https://github.com/lakridserne/db-miniproject-2-nosql/blob/master/100495141_1407676352774106_4294128089455132672_n.png "Logo Title Text 1")


## Conclusion
      
    
There are both advantages and disadvantages between choosing MongoDB and Neo4J depending on what criteria is being used and ultimately the use case of the application using the database.
After comparing the databases practically and theoretically, we conclued that Neo4J is optimized for graphs.
MogoDB has a much wider use case for a lot of things. Compared on speed in fetching specific records, MongpDB is clearly 
faster. However Neo4j was never made for speed but was made for graphs. And in regards to size, Neo4J is 7 times larger than 
MongoDB.  
In relation to CAP MongoDB has support for it , where Neo4j does not really support it exepet for maybe the enterprise version.
Both neo4j and MongoDB has a suppport for ACID however MongoDB first for it in veriosn 4.0 on document level.
   
     
     
     
     
  

     
## Misc
  
 Technical Specifications for our Machine, we ran the scripts on:
 
 CPU: Intel Core i7-8750H
 
 GPU: Gtx 1050 6gb
 
 Memory: Ddr4 16gb RAM
 
 OS: Ubuntu 19.10 (64-bit)
 
 Hard Drive: ssd 138gb & SATA 5Tb  
             
     
     
