### Databases: Introduction and Types

**What is a Database?**:

- A database is an organized collection of data, typically stored electronically. It's designed to efficiently store, manage, and retrieve data.
- Databases play a crucial role in modern software development, enabling applications to store and manage vast amounts of information.

**Types of Databases**:

1. **Relational Databases**:

   - **Description**: Store data in structured tables with rows and columns.
   - **Example**: MySQL, PostgreSQL, SQLite, Oracle.
   - **Pros**:
     - Well-established, proven technology.
     - Support for ACID (Atomicity, Consistency, Isolation, Durability) transactions.
     - > **🔔 Good to Know: ACID Properties in Databases**
        >
        > - **Atomicity**: Ensures all operations in a transaction are completed successfully as a single unit. If any operation fails, the entire transaction is rolled back.
        > - **Consistency**: Guarantees that a transaction will bring the database from one valid state to another, maintaining all predefined rules.
        > - **Isolation**: Ensures that transactions are executed in isolation from each other, preventing transactions from seeing intermediate results.
        > - **Durability**: Once a transaction is committed, it is permanent, even in the event of a system failure. This ensures data integrity post-transaction.
        >
        > ACID properties are essential for systems that require reliable data transactions, such as financial and banking systems.

   - **Cons**:
     - Not always suitable for highly dynamic or unstructured data.
     - Schema changes can be challenging.

2. **NoSQL Databases**:
   - **Description**: Databases that store data in formats other than traditional rows and columns.
   - **Example**: MongoDB, Cassandra, Redis.
   - **Pros**:
     - Suitable for handling dynamic, unstructured, or semi-structured data.
     - Flexible schema allows easy adaptation to changing data requirements.
   - **Cons**:
     - May not support ACID transactions as well as relational databases.
     - Learning curve for those accustomed to relational databases.

---

### MongoDB: A NoSQL Database

**Introduction to MongoDB**:

- **Description**: MongoDB is a popular open-source NoSQL database.
- **Key Feature**: It uses a flexible, document-based model to store data, where each record is a document containing fields and values.
- **Use Cases**: Web applications, mobile apps, content management systems, IoT, and more.

**Advantages of MongoDB**:

1. **Flexibility**:

   - Schema-less design allows you to store heterogeneous data in the same collection.
   - Changes to data structure can be made without affecting existing records.

2. **Scalability**:

   - Horizontal scaling is easily achieved through sharding, distributing data across multiple servers.
   - Suitable for applications that require handling large volumes of data.

3. **Query Language**:

   - MongoDB's query language is powerful and expressive.
   - Supports a wide range of queries, including aggregation and text search.

4. **Speed**:
   - No complex joins, as data is often stored in a denormalized format.
   - Well-suited for read-heavy workloads.

**When to Choose MongoDB**:

- Choose MongoDB when you need to handle dynamic, unstructured data, require quick iteration, and prefer flexibility over rigid schema requirements.
- Consider it for projects where speed and scalability are important.

**MongoDB vs. Other NoSQL Databases**:

- MongoDB is just one of several NoSQL databases. Each has its strengths and weaknesses, so it's essential to choose the one that best fits your project's requirements.

---

### MongoDB: Fundamental Operations and Terminologies

**1. Terminology**:

- **Database**: A MongoDB instance can host multiple databases. Each database is a set of collections, similar to how traditional databases host tables.

- **Collection**: Equivalent to a table in relational databases. It holds a set of documents.

- **Document**: A single data entity with fields and values, similar to a row in relational databases. Documents are stored in JSON-like format called BSON.

- **Field**: A name-value pair inside a document. Similar to a column in relational databases.

---

**2. Basic Database Operations**:

- **Create a New Database**:

  ```javascript
  use myNewDatabase;
  ```

  **Description**: This command switches to the specified database. If the database doesn't exist, MongoDB will create it once you add data.

- **List All Databases**:

  ```javascript
  show dbs;
  ```

  **Description**: Displays a list of all databases on the MongoDB server.

- **Switch Between Databases**:

  ```javascript
  use anotherDatabase;
  ```

  **Description**: Switches to the specified database.

- **Drop a Database**:
  ```javascript
  db.dropDatabase();
  ```
  **Description**: Deletes the current database.

---

**3. Collections Management**:

- **Create a Collection**:
  MongoDB creates collections automatically when you insert data. However, you can also create them explicitly:

  ```javascript
  db.createCollection("myCollection");
  ```

  **Description**: Creates a new collection named "myCollection" in the current database.

- **List All Collections**:

  ```javascript
  show collections;
  ```

  **Description**: Displays a list of all collections in the current database.

- **Drop a Collection**:
  ```javascript
  db.myCollection.drop();
  ```
  **Description**: Deletes the specified collection and its data.

---

**4. Documents Management**:

- **Insert a Document**:

  ```javascript
  db.myCollection.insertOne({ name: "Alice", age: 25 });
  ```

  **Description**: Inserts a single document into the specified collection.

- **Find Documents**:

  ```javascript
  db.myCollection.find();
  ```

  **Description**: Retrieves all documents from the specified collection.

- **Update a Document**:

  ```javascript
  db.myCollection.updateOne({ name: "Alice" }, { $set: { age: 26 } });
  ```

  **Description**: Updates the first document that matches the query.

- **Delete a Document**:
  ```javascript
  db.myCollection.deleteOne({ name: "Alice" });
  ```
  **Description**: Deletes the first document that matches the query.

---

**5. Indexing**:

- **Create an Index**:

  ```javascript
  db.myCollection.createIndex({ name: 1 });
  ```

  **Description**: Creates an ascending index on the "name" field of the specified collection. Indexing speeds up query performance.

- **List All Indexes**:
  ```javascript
  db.myCollection.getIndexes();
  ```
  **Description**: Displays a list of all indexes on the specified collection.

---

Alright, let's move on to the practical aspects of MongoDB.

### MongoDB: Practical Introduction

**1. Installing MongoDB**:

To install MongoDB, you'd typically follow the instructions provided in the official MongoDB documentation based on your operating system. Here's a general outline:

- **Windows**: Download the MongoDB installer and follow the installation instructions.
- **Mac**: Use a package manager like Homebrew: `brew install mongodb`.
- **Linux**: Use the package manager specific to your distribution (like `apt` for Ubuntu) to install MongoDB.

**2. Starting MongoDB**:

- Once installed, you can start MongoDB using the `mongod` command.
- To interact with MongoDB, you can use the `mongo` shell.

**3. Basic CRUD Operations in MongoDB**:

- **Create**: Use the `insertOne()` or `insertMany()` method.

  ```javascript
  db.collectionName.insertOne({ name: "John", age: 30 });
  ```

- **Read**: Use the `find()` method.

  ```javascript
  db.collectionName.find({ name: "John" });
  ```

- **Update**: Use the `updateOne()` or `updateMany()` method.

  ```javascript
  db.collectionName.updateOne({ name: "John" }, { $set: { age: 31 } });
  ```

- **Delete**: Use the `deleteOne()` or `deleteMany()` method.
  ```javascript
  db.collectionName.deleteOne({ name: "John" });
  ```

**4. MongoDB Atlas**:

- For those who prefer a cloud solution, MongoDB Atlas provides a fully managed database service. You can create a cluster, connect your application, and start using MongoDB without managing the underlying infrastructure.

---

### MongoDB: Descriptive Queries and Operations

**1. Inserting Data**:

- **Insert a Single Document**:

  ```javascript
  db.collectionName.insertOne({
  	name: "Alice",
  	age: 25,
  	profession: "Engineer",
  });
  ```

  **Description**: Inserts a single document into the collection with the specified fields: name, age, and profession.

- **Insert Multiple Documents**:
  ```javascript
  db.collectionName.insertMany([
  	{ name: "Bob", age: 30, profession: "Doctor" },
  	{ name: "Charlie", age: 28, profession: "Artist" },
  	{ name: "David", age: 35, profession: "Lawyer" },
  ]);
  ```
  **Description**: Inserts multiple documents into the collection in one operation.

**2. Querying Data**:

- **Find All Documents in a Collection**:

  ```javascript
  db.collectionName.find();
  ```

  **Description**: Retrieves all documents from the specified collection.

- **Find Specific Documents**:

  ```javascript
  db.collectionName.find({ name: "Bob" });
  ```

  **Description**: Searches for and retrieves documents where the name is "Bob".

- **Query with Conditions**:

  ```javascript
  db.collectionName.find({ age: { $gt: 30 } });
  ```

  **Description**: Retrieves documents where the age is greater than 30.

- **Projection**:
  ```javascript
  db.collectionName.find({}, { name: 1, _id: 0 });
  ```
  **Description**: Retrieves only the `name` field for all documents in the collection, excluding the `_id` field.

**3. Updating Data**:

- **Update a Single Document**:

  ```javascript
  db.collectionName.updateOne({ name: "Alice" }, { $set: { age: 26 } });
  ```

  **Description**: Updates the age of the first document where the name is "Alice" to 26.

- **Update Multiple Documents**:

  ```javascript
  db.collectionName.updateMany({}, { $inc: { age: 1 } });
  ```

  **Description**: Increases the age of all documents in the collection by 1.

- **Upsert**:
  ```javascript
  db.collectionName.updateOne(
  	{ name: "Eve" },
  	{ $set: { age: 40, profession: "Teacher" } },
  	{ upsert: true }
  );
  ```
  **Description**: Updates the document with the name "Eve" if it exists. If it doesn't, a new document with the specified fields is inserted.

**4. Deleting Data**:

- **Delete a Single Document**:

  ```javascript
  db.collectionName.deleteOne({ name: "David" });
  ```

  **Description**: Deletes the first document where the name is "David".

- **Delete Multiple Documents**:
  ```javascript
  db.collectionName.deleteMany({ age: { $lt: 30 } });
  ```
  **Description**: Deletes all documents where the age is less than 30.

**5. Advanced Queries**:

- **Logical Operators**:

  ```javascript
  db.collectionName.find({ $or: [{ name: "Alice" }, { name: "Bob" }] });
  ```

  **Description**: Retrieves documents where the name is either "Alice" or "Bob".

- **Regular Expressions**:

  ```javascript
  db.collectionName.find({ name: /^A/ });
  ```

  **Description**: Searches for documents where the name starts with the letter "A".

- **Count Documents**:

  ```javascript
  db.collectionName.countDocuments({ age: { $gt: 30 } });
  ```

  **Description**: Counts the number of documents where the age is greater than 30.

- **Sorting**:

  ```javascript
  db.collectionName.find().sort({ age: -1 });
  ```

  **Description**: Retrieves all documents, sorted by age in descending order.

- **Limit and Skip**:
  ```javascript
  db.collectionName.find().limit(10).skip(20);
  ```
  **Description**: Retrieves documents with pagination, showing 10 documents starting from the 21st document.

---
