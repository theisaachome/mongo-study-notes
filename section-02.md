## **SECTION 02: CRUD Operations**

### [Table of Contents]

- [Understanding Database Collection Document](#understanding-database-collection-document)
- [Creating Database Collection](#creating-database-collection)
- [Understandinng JSON DATA](#understandinng-jSON-data)
- [Comparing JSON and BSON](#comparing-json-and-bson)
- [CRUD Operation & MongoDB](#crud-operation-&-mongoDB)
- [Finding Inserting Deleting Updating](#finding-inserting-deleting-updating)
- [Understandig InsertMany](#understandig-insertMany)
- [Deeper into finding Data](#deeper-into-finding-data)
- [Update Vs UpdateMany](#update-vs-updatemany)

---

### **Understanding Database Collection Document**

#### **Databases**

- One or more Databases on the server

#### **Collection**

- database can hold one or more Collections

#### **Document**

- In Collection, documents are stored. multiple document can be stored on One Collection.

- Databases, Collections and documents are implicityly created when we store the data.

  ![](section-02/database-collection-document.png)

  **[⬆ back to top](#table-of-contents)**

---

### **Creating Database Collection**

```shell
> show dbs
```

```shell

> use users

> db.userData.insertOne(
    {
        "name": "isaac home",
        "username": "isaac",
        "email": "isaachome@april.biz"
  }
)
```

- find all documents

```shell
db.userData.find().pretty()
```

## Understandinng JSON DATA

```json
{
  "name": "isaac home",
  "username": "isaac",
  "email": "isaachome@april.biz",
  "age": 20,
  "isMarried": false
}
```

- key value paired made up
- key with double qoutation
- value with

  - different type such as boolean or number

  ```shell
  db.userData.insertOne(
      {
        "name": "isaac home",
        "username": "isaac",
        "email": "isaachome@april.biz",
        "age": 20,
        "isMarried": false
      }
  )
  ```

## **Comparing JSON and BSON**

- Mongo use BJSON for storing data.
- User will deal only JSON.
- behind the mongo convert json to bjson
- by using MongoDb Drivers

#### **Why BJSON**

- Efficiennt Storage
- additional data types

  ```shell
  "_id" : ObjectId("6066c3d0baef3a0bdc9d2a3f")
  ```

  ![](section-02/json-vs-bson.png)

---

### CRUD Operation & MongoDB

- what is CRUD
  - creating new document
  - reading documents from collections
  - updating documents
  - delete documents

### CREATE

- important for creating data.
- insertOne(data,options)

  - allow single data with options.
  - directly executed on a collection.

- insertMany(data,options)

  - insert many documents once at a time.

### READ

- find(fileter,options)
  - with some argument filter and options
- findOne(filter,options)

  - first matching document.

### Update

- updateOne(filter,data,options),
- updateMany(filter,data,options)
- replaceOne(filter,data,options)
  - to replace the entire document

### Delete

- deleteOne(filter,options)
- deleteMany(filter,options)

  ![](section-02/crud-2.png)

---

### Why

- We might work with Application , BI tools and database administration.
- where we manupulate our data.

  ![](section-02/crud.png)

---

### Example #1

- with flightData
- user will add a flight ,
- update information
- Cancel flight
- Display flight information

  ![](section-02/crud-example.png)

---

### **Finding Inserting Deleting Updating**

- find all
  - without filter

```shell

  db.userData.find().pretty();

```

- using filter

```shell
 db.userData.find({_id:ObjectId("606be36635ad5404b4c23dfc")}).pretty()
```

- **_findOne()_**
  - find element that match first

```shell
db.userData.findOne();
```

---

### **Insert Document**

- insert new element

```shell

$ db.userData.insertOne(
  {
    "name": "isaac home",
    "username": "isaac",
    "email": "isaachome@april.biz",
    "address": {
    "street": "Kulas Light",
    "suite": "Apt. 556",
    },
    "phone": "1-770-736-8031 x56442",
    "website": "hildegard.org",
    "company": {
    "name": "Romaguera-Crona",
    "catchPhrase": "Multi-layered client-server neural-net",
    "bs": "harness real-time e-markets"
    }
  }
);

```

---

### **Update Document**

- update new field in the document using **_$set operator_**

- $ is reserved operator

- $set to update new field at existing document

```shell
$ db.userData.updateOne(
    {_id:"606be280a4205504b45c7fc4"},
    {
      $set:{
      marker:"raw"
      }
    }
  );
```

- updateMany leave empty filter

```shell

 $ db.userData.updateMany({},{$set:{marker:"raw"}});

 $ db.userData.find({marker:"raw"}).pretty();

```

---

### **Delete Document**

- delete document
  - take filter to match on which key and value.
  - deleteOne({})

```shell

  db.userData.deleteOne({username:"isaac"})

```

- deleteMany({})
  - must all document have common fields
  - or can delete all document with empty filter

```shell
db.userData.deleteMany({marker:'raw'});

db.userData.deleteMany({});
```

---

### **Understandig InsertMany**

- To insert many documentm(array objects) at once.

  - insertMany()

  - it take array []

```shell
db.blog.insertMany(
  [
    {
    "userId": 1,
    "id": 1,
    "title": "sunt aut facere optio reprehenderit",
    "body": "quia et suscipit"
    },
    {
    "userId": 1,
    "id": 2,
    "title": "qui est esse",
    "body": "est rerum tempore "
    }
  ]
);
```

---

### **Deeper into finding Data**

```shell
 db.blog.find({title : "qui est esse"}).pretty()
```

- using operator
  - the general form

```shell
 { field : { $gt : value } }

db.blog.find({age:{$gt:9}}).pretty()

```

---

### **Update Vs UpdateMany**

- updateOne() take filter which to update

- when we want to update specific data (partially)

- updateMany()

#### **caution**

- update() take filter and object to update but it replace the entire document

  ```shell
  db.blog.update({_id:ObjectId("606be9bdf64d9a04b473fea4")},{name:"isaachome"});
  ```

  **note**:

  - _update({},{})_ without $set operator is not allowed in _updateOne()_ and _updateMany()_ but only at _update()_.

- for replace use

```shell
 db.blog.replaceOne({},{});
```
