# MongoDB Cheat Sheet

## Table of Contents
1. [Installation](#installation)
2. [Basics of MongoDB](#basics-of-mongodb)
3. CRUD
 3.1 [Create](#create)
 3.2 [Read](#read)
 3.3 [Update](#update)
 3.4 [Delete](#delete)



## Installation
To install MongoDB, follow the official [MongoDB installation guide](https://docs.mongodb.com/manual/installation/).




## Basics of MongoDB
To **Start** database, use the following command:

```bash
mongod
```

To **Connect** database, use the following command:

```bash
mongo
```

[PS : mongo vs mongod](https://stackoverflow.com/questions/4883045/mongodb-difference-between-running-mongo-and-mongod-databases)


To **Show name of current database** database, use the following command:

```bash
db
```


To **Show all databases**, use the following command:

```bash
show dbs
```


To **Switch to database db**, use the following command:

```bash
use db
```


To **Display current database collec­tions**, use the following command:

```bash
show collec­tions
```







## CRUD

### Create
To **insert document(s) returns write result**, use the following command:

```bash
insert­(data)
```


To **insert one document**, use the following command:

```bash
insertOne (data, options)
```



To **insert many documents**, use the following command:

```bash
insert­Man­y(data, options)
```




To **insert many documents**, use the following command:

```bash
insert­Man­y(data, options)
```

if **needs square brackets**, use the following command:

```bash
insert­Man­y([­{},­{},{}])
```

### Read

To **Display documents from collection**, use the following command:

```bash
db.co­­lle­­ct­i­o­n.f­­ind()
```

To **find all matching documents**, use the following command:

```bash
find(f­ilter, options)
```


To **find first matching document**, use the following command:

```bash
findOn­e(f­ilter, options)
```

### Update



To **Change one document**, use the following command:

```bash
update­One­(fi­lter, data, options)
```



To **Change many documents**, use the following command:

```bash
update­Man­y(f­ilter, data, options)
```



To **Replace document entirely**, use the following command:

```bash
replac­eOn­e(f­ilter, data, options)
```

### Delete


To **Delete one document**, use the following command:

```bash
delete­One­(fi­lter, options)
```



To **Delete many documents**, use the following command:

```bash
delete­Man­y(f­ilter, options)
```



