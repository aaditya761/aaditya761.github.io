No Sequal Databases:

Advantages:
1) Data is stored as JSon with column names as the key. All the relevant data is stored in one blob so insertions and retrievals are fast as we can do awya without joins. 
2) If new columns are needed to be added for new data and we don't care about old data, NoSequal is better since we can staright away start adding new data without touching old data. In sql we have to add a new column and provide values for laready stored data which is expensive. 
3) Better horizontal partitioning. 
4) Better for aggregation and analytics. Thats why companies use nosql for analytics.

Disadvantages:
1)If there are a lot of updates, it becomes costly.
2) Consistency is a problem - acid is not guranteed. therefore financial institutions don't use nosal  for transactions
3)Are not read optimized. Takes a long time if you have to read many values
4)Relations are not implicit. You can't enforce a foreign key contraint
5) Joins are hard 





MongoDB

SQL              Mongo
Table            Collection
Row              Document
Column           Field

Collection isn't strict about what goes in it.

Create database - use databasename. If databse is present, it will use it. Else it will create it.
Create collection - db.createCollection(CollectionName)
List all collections - show collections 
Inset data - db.collectionName.insert(data)
Insert multiple entries - db.collectionName.insert(array of data)
Fetch all data from a collection - db.collectionName.find()
Find on condition - db.collectionName.find(condition)

example find all where age is greater than 15 - db.myCollection.find({"age":{$gt:15}}) 


And condition - db.collectionName.find({condition1, condition2, ...}) example - db.myCollection.find({"name":"aditya", "age":15})

Or Condition - db.collectionName.find({$or: [{condition1, condition2, ...}]}) example - db.myCollection.find({$or:[{"name":"aditya", "age":15}]})

And Or together - db.collectionName.find({andConditions, $or: [{condition1, condition2, ...}]}}) example - db.myCollection.find({"name":"aditya", $or:[{"name":"aditya", "age":15}]})


Update data:
db.collectionName.update(conditions, dataToBeUpdated) example - db.myCollection.update({"_id":2}, {$set:{"lastName":"kumar"}})
if there are multiple values to be updated - db.myCollection.update({"_id":2}, {$set:{"lastName":"kumar"}, {multi:true}})


