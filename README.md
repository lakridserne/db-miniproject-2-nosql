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
5)
