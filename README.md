## MongoDB 
- Mongo itself means huge, means it can handle huge amount of data.
- Scalable with nodes and distributed system.
- Replication can be done via sharding.
- Schemaless : Documents with variational fields can be stored in a collection.

Every document is stored in `JSON` for us, but behind the scene, it got stored in `BSON`.
> BSON is a Binary json structure encodes type and length information, which allows it be traversed much more quickly comapred to json.
---
## How to interact with MongoDB
We can interact with MongoDB in two ways : 
1. Using CLI, Command Line Interface (via Mongo-Shell).
2. Using MongoDB Compass, a GUI provided by MongoDB company.

---
## Start/Stop MongoDB service
Install and Run the Mongo-Shell as administrator and run the command below: 

- To **Start** MongoDB service : 

```javascript 
net start MongoDB
``` 

- To **Stop** MongoDB service :
```javascript 
net stop MongoDB
``` 
---
## Database creation in MongoDB

**- Create a DataBase named as latest_db:**
```javascript 
use latest_db
```
- If the latest_db is present, it will switch to the latest_db.
- If latest_db is not present than MongoDB is intelligent enough to create it.

**- Insert `Document` (student, in our case) using MongoDB**
```javascript
db.students.insertOne(name:"Ram",age:12)
```
- Create a collection `students` and insert a `document` in it.

**- Find all `documents` present in the database**
```shell
db.students.find({})
```
- List all the documents present in the document

---

### Embedding documents in MongoDB

- To Update documents in MongoDB, we use `set` update operator, **used to embed document and arrays.**

```shell
db.students.updateOe({name:"Ram"},{
    $set : {
        idCards : {
            hasPanCard : false,
            hasAadharCard : true
        }
    }
})
```
**- What `$set` operator do?**
- If the field is not present, it will create it for you.
- If the field already exists, it will update it for you.

>MongoDB documents can be nested till `100 levels` and 1 document can be of at max `16 mb`.

**- Query to update all the documents present in the collection.**
```shell
db.students.updateMany({}, {
    $set : {
        hobbies : ["Coding","Cooking"]
    }
})
```
- If we want to selected students only, we can use `filter` argumented query.
```shell
db.students.updateMany({name:Ram}, {
    $set : {
        hobbies : ["Bhajan","Cooking"]
    }
})
```
- All students with name `Ram` will have `Bhajan` and `Cooking` in their hobbies attribute.

---

### Searching in MongoDB

```shell 
db.students.find({hobbies : 'cooking'}).count()
```
- List all the students, have cooking in their attribute.

```shell
db.students.find({'idCards.hasPanCard' : true})
```
- List all the students, who have Pan-card
> `Keys` are always written in `quotes` while `searching`.

---

### CRUD in MongoDB

- Here, we got overview of the functions used to do **CRUD** operations (step-by-step):

> Create
```shell
insertOne(data,options)
insertMany(data,options)
```

> Read
```shell
find(filter,options)
findOne(filter,options)
```

> Update
```shell
updateOne(filter,data,options)
updateMany(filter,data,options)
replaceOne(filter,data,options)
```

> Delete
```shell
deleteOne(filter,options)
deleteMany(filter,options)
```

---
