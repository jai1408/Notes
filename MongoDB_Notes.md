# Notes

## Types of NoSQL databases

* Key-Value Stores - Redis, Dynamo, Riak
* Column-Oriented - BigTable, Cassandra, SimpleDB
* Graph - OrientDB, Neo4J, Titan
* Document Oriented - **MongoDB**, CouchDB

## find queries
*  db.passengers.find().forEach((passengersData) => {printjson(passengersData.name)})
*  db.passengers.findOne()
*  db.passengers.find().pretty()
*  db.passengers.find().toArray()
*  db.passengers.findOne({"_id": ObjectId("annudenvn563257jksn")})
*  db.passengers.findOne({age: {$gt: 35})
*  db.passengers.find({age: {$gt: 35}).pretty()

## Insert, Update, Delete Queries
* **db.collection.insertOne()** 	Insert a new document into the collection.
* **db.collection.insertMany()** 	Insert multiple new documents into the collection.
* **db.collection.updateOne()** 	Update a single existing document in the collection.
* **db.collection.updateMany()** 	Update multiple existing documents in the collection.
* **db.collection.save()** 	Insert either a new document or update an existing document in the collection.
* **db.collection.deleteOne()** 	Delete a single document from the collection.
* **db.collection.deleteMany()** 	Delete documents from the collection.
* **db.collection.drop()** 	Drops or removes completely the collection.
* **db.collection.createIndex()** 	Create a new index on the collection if the index does not exist; otherwise, the operation has no effect.
* **db.getSiblingDB()** 	Return a reference to another database using this same connection without explicitly switching the current database. This allows for cross database queries.
* **db.dropdataBase()** Drop the current db
***
you could get rid of a single collection in a database via `db.myCollection.drop()`.

MongoDB has a couple of hard limits - most importantly, a single document in a collection (including all embedded documents it might have) must be <= **16mb**. Additionally, you may only have **100 levels of embedded documents**.

You can find all limits (in great detail) here: https://docs.mongodb.com/manual/reference/limits/

For the data types, MongoDB supports, you find a detailed overview on this page: https://docs.mongodb.com/manual/reference/bson-types/
### Important data type limits are:
* Normal integers (int32) can hold a maximum value of +-2,147,483,647
* Long integers (int64) can hold a maximum value of +-9,223,372,036,854,775,807
* Text can be as long as you want - the limit is the 16mb restriction for the overall document

It's also important to understand the difference between int32 (NumberInt), int64 (NumberLong) and a normal number as you can enter it in the shell. The same goes for a normal double and NumberDecimal.

**NumberInt** creates a int32 value => `NumberInt(55)`  
**NumberLong** creates a int64 value => `NumberLong(7489729384792)`

If you just use a number (e.g. `insertOne({a: 1}`), this will get added as a **normal double** into the database. The reason for this is that the shell is based on JS which only knows float/ double values and doesn't differ between integers and floats.

**NumberDecimal** creates a high-precision double value => `NumberDecimal("12.99")` => This can be helpful for cases where you need (many) exact decimal places for calculations.

When not working with the shell but a MongoDB driver for your app programming language (e.g. PHP, .NET, Node.js, ...), you can use the driver to create these specific numbers.

Example for Node.js: http://mongodb.github.io/node-mongodb-native/3.1/api/Long.html

This will allow you to build a NumberLong value like this:
```
const Long = require('mongodb').Long;
db.collection('wealth').insert( {
    value: Long.fromString("121949898291")
});
```
By browsing the API docs for the driver you're using, you'll be able to identify the methods for building int32s, int64s etc.

#### Helpful Articles/ Docs:
* The MongoDB Limits: https://docs.mongodb.com/manual/reference/limits/
* The MongoDB Data Types: https://docs.mongodb.com/manual/reference/bson-types/
* More on Schema Validation: https://docs.mongodb.com/manual/core/schema-validation/
***

`db.companies.insertOne({name: "Apples Inc", isStartup: true, employees: 33, fundings: 12345678901234567890, details: {ceo: "Steve Jobs", cto: "Steve Wozniak"}, tags: [{title: "SDE I"}, {title: "SDE II"}], foundingDate: new Date(), insertedAt: new Timestamp()})`

```
{
        "acknowledged" : true,
        "insertedId" : ObjectId("5d99946bc60a80a2db894d99")
}
```
`> db.companies.find().pretty()`
```
{
        "_id" : ObjectId("5d99946bc60a80a2db894d99"),
        "name" : "Apples Inc",
        "isStartup" : true,
        "employees" : 33,
        "fundings" : 12345678901234567000,
        "details" : {
                "ceo" : "Steve Jobs",
                "cto" : "Steve Wozniak"
        },
        "tags" : [
                {
                        "title" : "SDE I"
                },
                {
                        "title" : "SDE II"
                }
        ],
        "foundingDate" : ISODate("2019-10-06T07:14:51.882Z"),
        "insertedAt" : Timestamp(1570346091, 1)
}
```

