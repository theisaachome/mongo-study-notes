## **SECTION 02: CRUD Operations**

### [Table of Contents]

- [Understanding Database Collection Document](#understanding-database-collection-document)
- [Creating Database Collection](#creating-database-collection)
- [Understandinng JSON DATA](#understandinng-jSON-data)
- [CRUD Operation & MongoDB](#crud-operation-&-mongoDB)

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

## **JSON vs BJOSN**

- Mongo use BJSON for storing data.
- User will deal only JSON.
- behind the mongo convert json to bjson
- by using MongoDb Drivers

### **Why BJSON**

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
