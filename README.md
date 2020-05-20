# db-miniproject-2-nosql

Overview:

In this assignment we have used MongoDB and Neo4J since it is a requirement using NoSQL Database and comparing them. The other reason we choose MongoDB and Neo4J was because we had already installed them. 
What we then did was we tried to import a 24 Gb file into our databases. 
The file contained listed over user’s id and who they are following. 
We encountered that the file was to large so what we did was we had the files size reduced to 2GB which worked


1)  Import stament:

      Neo4J
               
               neo4j-admin import --node=2G.csv
     
      MongoDB
                   
               mongoimport --type csv -d twitterFollowers -c followers --headerline --drop 2G.csv

2)    Database operations:
   We will select 1 million rows from the database so we can inspect which users follows who.


3)  Selecting appropriate criteria for comparison( Storage space);
    
      Neo4J:
      
      ```
      8.898GB
      ```
     
     MongoDB:
     
     ```
      3.364GB  
      ```
4)
  
      Neo4J:
      returns 1000000 users id in 7 sec
      ```
      Match(n) RETURN n limit(1000000)
      ```
      MongoDb
      returns 1000000 users id in 115 sec
      ```
      DBQuery.shellBatchSize = 1000000
      db.followers.find()
      ```
5)   Conclusion
      
     We have concluded that MongoDB compared to Neo4J. That there are both advantages and disadvantages depending on what criteria is        being used. 
     We personal feel that MongoDB is more comfortable using contra Neo4J in regards complexity.
     The other thing is that mongoDB feels more opensource where as Neo4J feels more like enterprise software
     
     
     
     Cap
     
     MongoDB:
     
     MongoDB is strongly consistent by default - if you do a write and then do a read,
     assuming the write was successful you will always be able to read the result of the write you just read.
     This is because MongoDB is a single-master system and all reads go to the primary by default.
     if you optionally enable reading from the secondaries then MongoDB becomes eventually consistent where
     it's possible to read out-of-date results.
     
     Neo4j:
     
     In our understanding Neo4j has no facility for partitioning or sharding and so is not a distributed database.
     So the CAP theorem doesn’t really apply. However there are two clustering modes available in the enterprise edition.
     
     
     
     ACID
     
     MongoDB:
      
      After the release of version 4.0, MongoDB now has support for multi-document ACID transactions,
      which now make it a ACID-compilant at the document level.
     
     
     Neo4j:
     
     Neo4j is ACID compliant and supports properties of ACID, a link to full overview can be found [here] (https://www.graphgrid.com/neo4j-is-designed-to-be-your-source-of-truth-database)

     
  Misc 
  
 Technical Specifications for our Machine, we ran the scripts on:
 
 CPU: Intel Core i7-8700K
 GPU: Gtx 1070 8gb
 Memory: Ddr4 16gb RAM
 OS: Windows 10 (64-bit)
 Hard Drive: ssd 250gb
     
     
