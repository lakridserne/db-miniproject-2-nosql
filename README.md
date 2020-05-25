# db-miniproject-2-nosql

## Overview
In this assignment we have used MongoDB and Neo4J since it is a requirement using NoSQL Database and comparing them. The other reason we choose MongoDB and Neo4J was because we had already installed them. 
What we then did was we tried to import a 24 Gb file into our databases. 
The file contained listed over user’s id and who they are following. 
We encountered that the file was to large so what we did was we had the files size reduced to 2GB which worked
 
## Intro
Our assigment is to select two or more databases of different NoSQL types and to compare their features
and performance in storing, scaling, providing, and processing big data.

The reason we have chosen to use MongoDB and Neo4j for this project assignment, is because we figured out that those
two databases are completely different and we thought it then would give great diffrent results, when we are comparing
the data, so we could get a better overview for what each database is best suited for after reviewing our results
 
## Problem statement 
its interesting to analyze twitter followers. For this reason we desidef to import the data into our databases. We selected the two databases and want to compairer to each other. 

## Motivation 

 We want to research and experiment the difference bewtween mongodb and Neo4j in reagads to scalability, perfomence and compare the two databases features. 
Our first thoughs is to do research on how to use on of the following operations by inserting data into the to the two databases. Then based on the speed on two databases we want to compairer the time. Antoher thought is to do rerearsh on grafe and see to see if its possible to create a grafe on mongodb which we are not sure about if its possible. We allredy know it is possiible to create it with Neo4j. 

Last it would be intressting to use som big-data so we can better see the difference bewteen each database and get overview on how it effects our two databases. 

## Activity
// desciption of file
We have a big file that has a size around 24GB that tells us how many followers each twitter profile has. The file contains a list of IDs on all the follwers and the profiles being followed.

1)  Import stament: This statement import the "Twitter_data.csv" file.

  Neo4J
               
        USING PERIODIC COMMIT 500
        LOAD CSV FROM 'file:///twitter_data.csv' AS line
        CREATE (:Twitter_follower { following: line[0], follower: line[1] } );
 


     
     
   MongoDB
                   
        mongoimport --type csv -d twitterFollowers -c followers --headerline --drop 2G.csv
     
     During the import we could clearly see that MongoDB is more suited for large datasets, whereas Neo4J is more tailered to make   graphs. This was for example due to the way the import worked - MongoDB was able to hadnle a much larger file.

2)    Database operations:
   Our goal is to compare Neo4J and MongoDB to compare performance, scaling and storage in processing big data.
   We will select 1 million rows from the database so we can inspect which users follows who.


3)  Selecting appropriate criteria for comparison( Storage space);
    
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
     if you optionally enable reading from the secondaries then MongoDB becomes eventually consistent where
     it's possible to read out-of-date results.
     
     Neo4j:
     
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
      
     We have concluded that MongoDB compared to Neo4J. 
     That there are both advantages and disadvantages depending on what criteria is being used. 
     We personal feel that MongoDB is more comfortable using contra Neo4J in regards complexity.
   
     
     
     
     
  

     
  Misc 
  
 Technical Specifications for our Machine, we ran the scripts on:
 
 CPU: Intel Core i7-8700K
 
 GPU: Gtx 1070 8gb
 
 Memory: Ddr4 16gb RAM
 
 OS: Windows 10 (64-bit)
 
 Hard Drive: ssd 250gb
     
     
