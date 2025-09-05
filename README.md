# MongoDB

## What is MongoDB?
MongoDB is an **open-source**, **document-oriented**, **nosql** database management system.
MongoDB is case-sensitive.


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

* **Open-Source Community**:
    * MongoDB is a **open-source** with a **large comunity support**
    * **Regular updates**, **imporvement** and **support**.


## JSON vs BSON:
* In MongoDB, **we write data in JSON**, but internally, it is **stored in BSON** (Binary JSON).

* BSON allows: <br/>
✔️ Faster read & write operations <br/>
✔️ Reduced storage usage <br/>
✔️ Better handling of complex data structures <br/>

### JSON:
```json
{
  "name": "Arbaz",
  "age": 22,
  "isStudent": true,
  "scores": [88, 95],
  "address": {
    "city": "Delhi"
  }
}
```

### BSON:
```bson
\x31\x00\x00\x00
\x02name\x00\x06\x00\x00\x00Arbaz\x00
\x10age\x00\x17\x00\x00\x00
\x08isStudent\x00\x01
\x04scores\x00\x15\x00\x00\x00
\x10\x00\x58\x00\x00\x00
\x10\x01\x5F\x00\x00\x00
\x00
\x03address\x00\x13\x00\x00\x00
\x02city\x00\x06\x00\x00\x00Delhi\x00
\x00
\x00
```


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

---

## Insert Documents:

### Inserting Document (Single):
```js
db.<collection_name>.insertOne({
    "field1":"value1",
    "field2":"value2"
});
```

### Inserting Document (Multiple):
```js
db.<collection_name>.insertMany([
    {"field1":"value1", "filed2": "value2", ...},
    {"field1":"value1", "filed2": "value2", ...}
])
```


## Read Operations:
1. **find()**:

Syntax:
```js
db.<collection_name>.find({key: value});
```

2. **findOne()**:

Syntax:
```js
db.<collection_name>.findOne({key: value});
```

## When to use Quotes and when not?
* **Special Characters**:
If a field name *contains special characters* or *spaces*, or *starts with a numeric digit*, using ***quotes is necessory***.

* **Reserve Words**:
If a field name is a reserved keyword in MongoDB, use quotes distinguish it from the reserved keyword.

### Examples:
```js
db.students.insertOne({
  "1name": "Arbaz",     // starts with a number
  "full name": "Khan",  // contains space
  "e-mail": "arbaz@example.com" // contains special character (-)
  "type": "Admin",   // reserved keyword
  "key": "12345",    // reserved keyword
  "db": "collegeDB"  // reserved keyword
})
```


## Orderd and Unordered Inserts:
When executing bulk write operations, **ordered** and **Unordered** determine the batch behaviour.
* **Ordered Inserts**:
    * Default behavior is ordered, where MongoDB **stops on the first error**.
    * **db.<collection_name>.insertMany([doc1, doc2, ...]);**

* **Unordered Inserts**:
    * When executing bulk write operations with unordered flag, MongoDB ***processing after encountering an error***.
    * **db.<collection_name>.insertMany([doc1, doc2, ...], {ordered: false});**

### Examples:

#### Default Behaviour (*ordered: true*):
If one insert fails, MongoDB stops inserting the rest.

```js
db.students.insertMany(
  [
    { _id: 1, name: "Arbaz" },
    { _id: 1, name: "Duplicate ID" } // ❌ duplicate _id (error)
    { _id: 2, name: "Salman" },
  ]
)
// Only first will inserted, second fails → stops further execution.
```

#### With (*ordered: false*):
If one insert fails, MongoDB continues inserting the rest.

```js
db.students.insertMany(
  [
    { _id: 3, name: "Ali" },
    { _id: 3, name: "Duplicate ID" }, // ❌ duplicate error
    { _id: 4, name: "Khan" }
  ],
  { ordered: false }
)
// Ali ✅ inserted
// Duplicate ❌ skipped
// Khan ✅ still inserted
```


## Importing JSON in MongoDB:

If json is ***not in array***:
```js
mongoimport <json_file_name.json> -d <database_name> -c <collection_name>;
```

If json is ***inside array***:
```js
mongoimport <json_file_name.json> -d <database_name> -c <collection_name>;
```

If json is ***array of object***:
```js
mongoimport <json_file_name.json> -d <database_name> -c <collection_name> --jsonArray;
```

NOTE: *--jsonArray* accepts the import of data expressed with multiple MongoDB documents within a single JSON array.