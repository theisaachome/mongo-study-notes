# Mongodb Study Guide

## [Table of Contents](#table-of-contents)

- ### [Section 01: Introduction](https://github.com/theisaachome/mongo-study-notes/blob/main/section-01.md)

- ### [Section 01: Understanding Crud Operation](https://github.com/theisaachome/mongo-study-notes/blob/main/section-02.md)


## database User

### create new User 
```sh
db.createUser({user:"root",pwd:"pwd@root",roles:["userAdminAnyDatabase"]});
```

### login with authentication 

```sh
mongosh -u {user-name} -p {password}
```
