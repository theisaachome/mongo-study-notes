## **SECTION 02: CRUD Operations**

### [Table of Contents]

- [Understanding Database Collection Document](#understanding-database-collection-document)

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

### **Creating Database**

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
