### What is MongoDB ?

MongoDB is an open-source document oriented database management system (DBMS) that uses a JSON- like format to store and manage data.

#### Features:

MongoDB is a NOSQL database that uses flexible documents instead of tables and rows. It supports unstructured data, full indexing, and replication. MongoDB also offers ad-hoc query support, which allow, developers to update queries in real time.

#### Benefits:

MongoDB offers:
 - consistent performance
 - Advanced security
 - Unlimited Scaling

#### Use cases:

MongoDB is good choice for enterprise applications that require realtime analytics.

- Single-Page (Dynamic) Web applications built using Angular
- Workflow management  tools.
- News aggregation sites.
- To-do and Calender applications.
- Interactive forums.




### Installation:

1. Download MongoDB community server from - [https://www.mongodb.com/try/download/community](https://www.mongodb.com/try/download/community)
2. After installation Go to Environment variables in system settings Add path
   
   ```
   C:\Program Files\MongoDB\Server\4.4<version>\bin
   ```
3. Check Wheather the MongoDB server installed correctly (or) not on your system. In terminal
   
   ```
   mongod
   ```
   
### MongoDB Shell:

MongoDB shell is a modern command-line experience, full with features to make it easier to work with the database.

Download - [https://www.mongodb.com/try/download/shell](https://www.mongodb.com/try/download/shell)

- To Use MongoDB shell on windows. Type this in terminal:

  ```
  mongosh
  ```

### MongoDB Compass:

The GUI For MongoDB. Compass is a free interactive tool for querying,optimizing,and analyzing MongoDB data

Download - [https://www.mongodb.com/products/tools/compass](https://www.mongodb.com/products/tools/compass)

### Documents & Collections in MongoDB:

- Document: similar to rows (or) records in a relational database table, documents contains one or more fields.
  - Documents are data records

- Collections: similar to tables in a relational database system, collection group documents together. A collection can contain multiple documents.

![image](https://github.com/user-attachments/assets/86a8de67-d20e-4fc0-b6a9-6ccb992aaad1)

#### Example for a document:
- Documents are stored as JSON (mainly BSON)

```
{
"title" : "My first blog post",
"author" : "Prasad Raju",
"tags" : ["video games", "reviews"],
"upvotes" : 20,
"body" : "Lorem ipsum"
}

```

## Working with MongoDB shell:

- Show all the databases
  
  ```
  show dbs
  ```
- Create Or Switch Database - Ex: use books

  ```
  use <database name>
  ```
- Clear the Screen

  ```
  cls
  ```

- Show the current Database

  ```
    db
  ```

- Shows the all collections in that database

  ```
    show collections
  ```

- list of all commands

  ```
    help
  ```
- Exit MongoDB shell

  ```
  exit
  ```

- Drop the Database

  ```
  db.dropDatabase()
  ```
- Create Collection

  ```
  db.createCollection('<collection name>')
  ```

- Inserting one document into a collection

   ```
   db.<collection>.insertOne({})
   ```
     - Example:
      
       ```
       db.<collection>.insertOne({
                                     title : "The color of Magic",
                                     author : "Prasad Raju",
                                     pages : 300,
                                     rating : 7,
                                     genres : ["fantasy","magic"]
                                })
       ```
- Inserting more documents into the database at a time.

  ```
  db.<collection>.insertMany([{}])
  ```

- Returns all documents in the collection.

  ```
  db.<collection>.find()
  ```

- Using filters on find method.

  ```
  db.<collectio>.find({field : value})
  
  (or)
  
  db.collection.find( <query>, <projection>, <options> )
  ```
   - Examples:
     
      ```
      db.books.find({author: "Prasad Raju"}) 
      ```

      ```
      db.books.find({ author : "Prasad Raju", rating : 7})
      ```

      ```
      db.books.find({ author : "Prasad Raju"}, { title : 1, author : 1})

      This query only returns title and author field on this filter
      ```

      ```
      db.books.find({}, {title: 1, author: 1})
      ```
 - Return only one document with a filter
      ```
      db.<collection>.findOne({<field: value>})
      ```
### Chaining the methods:

- Return the count of the documents in that collection.

  ```
  db.<collection>.find().count()
  ```

  - Example:

    ```
    db.books.find({ author: "Prasad Raju"}).count()
    ```

- Return the first three documents, if we chain count() method it will return the number 3.

  ```
  db.<collection>.find().limit(3)
  ```

- Return the all documents sorted by their field value.

  ```
  db.<collection>.find().sort({field : value})
  ```
   - Example: Returns the three sorted documents by title.
          ```
          db.books.find().sort({title : 1}).limit(3)
         ```
# MongoDB Cheat Sheet

## Show All Databases

```
show dbs
```

## Show Current Database

```
db
```

## Create Or Switch Database

```
use acme
```

## Drop

```
db.dropDatabase()
```

## Create Collection

```
db.createCollection('posts')
```

## Show Collections

```
show collections
```

## Insert Row

```
db.posts.insert({
  title: 'Post One',
  body: 'Body of post one',
  category: 'News',
  tags: ['news', 'events'],
  user: {
    name: 'John Doe',
    status: 'author'
  },
  date: Date()
})
```

## Insert Multiple Rows

```
db.posts.insertMany([
  {
    title: 'Post Two',
    body: 'Body of post two',
    category: 'Technology',
    date: Date()
  },
  {
    title: 'Post Three',
    body: 'Body of post three',
    category: 'News',
    date: Date()
  },
  {
    title: 'Post Four',
    body: 'Body of post three',
    category: 'Entertainment',
    date: Date()
  }
])
```

## Get All Rows

```
db.posts.find()
```

## Get All Rows Formatted

```
db.posts.find().pretty()
```

## Find Rows

```
db.posts.find({ category: 'News' })
```

## Sort Rows

```
# asc
db.posts.find().sort({ title: 1 }).pretty()
# desc
db.posts.find().sort({ title: -1 }).pretty()
```

## Count Rows

```
db.posts.find().count()
db.posts.find({ category: 'news' }).count()
```

## Limit Rows

```
db.posts.find().limit(2).pretty()
```

## Chaining

```
db.posts.find().limit(2).sort({ title: 1 }).pretty()
```

## Foreach

```
db.posts.find().forEach(function(doc) {
  print("Blog Post: " + doc.title)
})
```

## Find One Row

```
db.posts.findOne({ category: 'News' })
```

## Find Specific Fields

```
db.posts.find({ title: 'Post One' }, {
  title: 1,
  author: 1
})
```

## Update Row

```
db.posts.update({ title: 'Post Two' },
{
  title: 'Post Two',
  body: 'New body for post 2',
  date: Date()
},
{
  upsert: true
})
```

## Update Specific Field

```
db.posts.update({ title: 'Post Two' },
{
  $set: {
    body: 'Body for post 2',
    category: 'Technology'
  }
})
```

## Increment Field (\$inc)

```
db.posts.update({ title: 'Post Two' },
{
  $inc: {
    likes: 5
  }
})
```

## Rename Field

```
db.posts.update({ title: 'Post Two' },
{
  $rename: {
    likes: 'views'
  }
})
```

## Delete Row

```
db.posts.remove({ title: 'Post Four' })
```

## Sub-Documents

```
db.posts.update({ title: 'Post One' },
{
  $set: {
    comments: [
      {
        body: 'Comment One',
        user: 'Mary Williams',
        date: Date()
      },
      {
        body: 'Comment Two',
        user: 'Harry White',
        date: Date()
      }
    ]
  }
})
```

## Find By Element in Array (\$elemMatch)

```
db.posts.find({
  comments: {
     $elemMatch: {
       user: 'Mary Williams'
       }
    }
  }
)
```

## Add Index

```
db.posts.createIndex({ title: 'text' })
```

## Text Search

```
db.posts.find({
  $text: {
    $search: "\"Post O\""
    }
})
```

## Greater & Less Than

```
db.posts.find({ views: { $gt: 2 } })
db.posts.find({ views: { $gte: 7 } })
db.posts.find({ views: { $lt: 7 } })
db.posts.find({ views: { $lte: 7 } })
```
