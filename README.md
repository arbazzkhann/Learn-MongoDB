# MongoDB

## What is MongoDB?
MongoDB is an **open-source**, **document-oriented**, **nosql** database management system.


## What is a Document Database?
* A document database (also known as **document oriented database** or a **document store**) is a database that stores information in documents.

* MongoDB is designed for **flexibility**, **scalability**, and **performance** in handling ***unstructured*** and ***semi-structured*** data.


## SQL and NoSQL:

### SQL:
* SQL database are **relational databases**.
* They are structured tables to store data in **rows** and **columns**.
* Suitable for applications with well-defined schemas and fixed data structures.
* E-Commerce plaform, HR Management, etc.
* ***Example***: MySQL, PostgreSQLm, Oracle.

### NoSQL:
* NoSQL database are **non-relational databases**.
* They provide **flexibility in data storage**, allowing **varied data types** and **structures**.
* Ideal for applications with dynamic or evolving data models.
* Used for - **CMS**, **Social media platforms**, **Gaming**, etc.
* ***Example***: **MongoDB**, **Cassandra**, etc.

### Example:
```json
[
    {
        "_id": "1",
        "full_name": {
            "first_name": "Arbaz",
            "last_name": "Khan"
        },
        "age":"22",
        "grade":"12",
        "subjects": [
            {"subject_name": "Mathematics", "marks": 92},
            {"subject_name": "Computer", "marks": 100}
        ]
    }
]
```

> MongoDB Structure: <br/>
<img src="mongo_structure.png" height="250px"/>


## Features of MongoDB:
* **Flexible Schema Design**: 
    * MongoDB allows *dynamic*, *schema-less* data sturectures.
    * Easily accommodate changing data requirements.

* **Scalability and Performance**:
    * ***Horizontal scaling*** *supports large datasets* and *high traffic*.
    * **Optimized read** and **write** operations for *fast performance*.

* **Document-Oriented Storage**:
    * Data is stored in flexible, **JSON-like BSON documents**.
    * Self contained units with **rich data types** and **nasted arrays**.

* **Dynamic Queries**:
    * **Rich query languages** with **support for complex queries**.
    * Utilize indexes to speed-up queries execution.

* **Aggregration Framework**:
    * Perform **advanced data transformations** and **analysis**.
    * **Process data using multiple pipelines stages**.

* **Open-Source Community**;
    * MongoDB is a **open-source** with a **large comunity support**
    * **Regular updates**, **imporvement** and **support**.


## Required files and Softwares:
1. MongoDB Community Server: [Download](https://www.mongodb.com/try/download/community)
2. MongoDB Shell: [Download](https://www.mongodb.com/try/download/shell)
3. MongoDB Database Tools: [Download](https://www.mongodb.com/try/download/database-tools)


## Some Basic MongoDB Commands:

### 1. Check Version:
```bash
mongod --version
```

---

### 2. Starting MongoDB Server:
```bash
mongosh
```

---

### 3. Showing Databases:
```bash
show dbs
# OR
show databases
```

---

### 4. Creating Database:
```bash
use <database_name>
```

---

### 5. Deleting Database:
```bash
db.dropDatabase()
```

---

### 6. Showing Collections:
```bash
show collections
```

---

### 7. Creating Collection:
```bash
db.createCollection('<collection_name>')
```

---

### 8. Deleting Collection:
```bash
db.<collection_name>.drop()
```

---

### 9. Showing Documents:
```bash
db.<collection_name>.find()
```
