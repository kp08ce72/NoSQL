# Practical related Questions
### Create `Products` collections and perform following queries on it. [2 hr]
```
{
  "_id": ObjectId("5f8a4c261c9d4400001a4af4"),
  "name": "Laptop",
  "price": 1200.99,
  "category": "Electronics",
  "stock": 50
}
```
   - Create a database named `OnlineStore` and a collection named `Products` with at least 4 fields.
   - Insert at least 10 records into the `Products` collection with various product details.
   - Retrieve and display all the documents inserted into the `Products` collection.
   - Update the price of a product in the `Products` collection based on a given condition.
   - Find and display records in the `Products` collection based on a specific criterion, e.g., category.
   - Retrieve and display the documents in the `Products` collection, sorted by price in ascending order.
   - Delete a record from the `Products` collection based on a given condition.
```
// Create a database named `OnlineStore` and a collection named `Products` with at least 4 fields.
use OnlineStore
db.createCollection("Products")

// Insert at least 10 records into the `Products` collection with various product details.
db.Products.insertMany([
  {
    "name": "Laptop",
    "price": 1200.99,
    "category": "Electronics",
    "stock": 50
  },
  {
    "name": "Smartphone",
    "price": 699.99,
    "category": "Electronics",
    "stock": 100
  },
  {
    "name": "T-shirt",
    "price": 19.99,
    "category": "Clothing",
    "stock": 200
  },
  // Add more documents here to fulfill the requirement of at least 10 records
])

// Retrieve and display all the documents inserted into the `Products` collection.
db.Products.find()

// Update the price of a product in the `Products` collection based on a given condition.
db.Products.updateOne(
  { "name": "Laptop" }, // Condition: Update the price of the laptop
  { $set: { "price": 1299.99 } } // New price
)

// Find and display records in the `Products` collection based on a specific criterion, e.g., category.
db.Products.find({ "category": "Electronics" })

// Retrieve and display the documents in the `Products` collection, sorted by price in ascending order.
db.Products.find().sort({ "price": 1 })

// Delete a record from the `Products` collection based on a given condition.
db.Products.deleteOne({ "name": "T-shirt" }) // Delete a T-shirt record, for example
```

### 2. Create `Books` collections and perform following queries on it. [2 hr]
```
{
  "_id": ObjectId("5f8a4c261c9d4400001a4af7"),
  "title": "The Great Gatsby",
  "author": "F. Scott Fitzgerald",
  "genre": "Classic",
  "year": 1925
}
```
   - Create a database named `Library` and a collection named `Books` with at least 4 fields.
   - Insert at least 10 records into the `Books` collection with details about various books.
   - Retrieve and display all the documents inserted into the `Books` collection.
   - Update the publication year of a book in the `Books` collection based on a given condition.
   - Find and display records in the `Books` collection based on a specific criterion, e.g., genre.
   - Retrieve and display the documents in the `Books` collection, sorted by publication year in ascending order.
   - Delete a record from the `Books` collection based on a given condition.

```
// Create a database named `Library` and a collection named `Books` with at least 4 fields.
use Library
db.createCollection("Books")

// Insert at least 10 records into the `Books` collection with details about various books.
db.Books.insertMany([
  {
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "genre": "Classic",
    "year": 1925
  },
  {
    "title": "To Kill a Mockingbird",
    "author": "Harper Lee",
    "genre": "Fiction",
    "year": 1960
  },
  {
    "title": "1984",
    "author": "George Orwell",
    "genre": "Dystopian",
    "year": 1949
  },
  // Add more documents here to fulfill the requirement of at least 10 records
])

// Retrieve and display all the documents inserted into the `Books` collection.
db.Books.find()

// Update the publication year of a book in the `Books` collection based on a given condition.
db.Books.updateOne(
  { "title": "The Great Gatsby" }, // Condition: Update the publication year of The Great Gatsby
  { $set: { "year": 1926 } } // New publication year
)

// Find and display records in the `Books` collection based on a specific criterion, e.g., genre.
db.Books.find({ "genre": "Fiction" })

// Retrieve and display the documents in the `Books` collection, sorted by publication year in ascending order.
db.Books.find().sort({ "year": 1 })

// Delete a record from the `Books` collection based on a given condition.
db.Books.deleteOne({ "title": "1984" }) // Delete the record of 1984, for example

```

### 3. Consider following collections and perform following queries on it. [4 hr]
```
   - Collection: `users`
   {
     "_id": ObjectId("5f8a49e11c9d4400001a4af1"),
     "name": "John Doe",
     "age": 25,
     "email": "john.doe@example.com"
   }
   - Collection: `blog_posts`
   {
     "_id": ObjectId("5f8a4a491c9d4400001a4af2"),
     "title": "MongoDB Blog",
     "content": "Introduction to MongoDB...",
     "author": "Jane Smith",
     "comments": [
       {
         "content": "Great post!",
         "author": "Alice",
         "timestamp": ISODate("2022-01-01T12:00:00Z")
       },
       {
         "content": "Thanks for sharing.",
         "author": "Bob",
         "timestamp": ISODate("2022-01-02T09:30:00Z")
       }
     ]
   }
   - Collection: `recipes`
   {
     "_id": ObjectId("5f8a4b431c9d4400001a4af3"),
     "name": "Spaghetti Bolognese",
     "ingredients": ["spaghetti", "ground beef", "tomato sauce", "onions"],
     "steps": ["Boil spaghetti", "Cook ground beef", "Mix with tomato sauce and onions"]
   }
```
   - Create a document for a "user" with fields for name, age, and email.
   - Design a document structure for a "blog post" that includes nested comments with fields for content, author, and timestamp.
   - Create a document structure for a "recipe" with an array field for ingredients and another for steps.
   - Perform CRUD operations on a "students" collection: insert a new student, retrieve a student by ID, update a student's grade, and delete a student.
   - Retrieve all documents from a "products" collection where the price is greater than $50.
   - Retrieve the top 5 highest-priced products from the "electronics" category.
   - Use the aggregation framework to calculate the average rating for a "movie" collection based on user reviews.
   - Create an index on the "timestamp" field of a "logs" collection and explain how it improves query performance.
   - Implement a text search query to find all documents in a "books" collection that contain the word "MongoDB" in the title or description.
    - Update a specific comment within a "post" document, changing its content.
    - Add a new ingredient to the array field of a "recipe" document.
    - Use the aggregation pipeline to group "sales" data by month and calculate the total revenue for each month.
    - Implement sharding for a large "sensor_data" collection, considering an appropriate shard key.
    - Set up a replica set with three nodes and demonstrate a failover scenario.
    - Create a text search index on multiple fields in a collection, allowing for efficient text searches.

```
// Create a document for a "user" with fields for name, age, and email.
db.users.insertOne({
  "name": "John Doe",
  "age": 25,
  "email": "john.doe@example.com"
})

// Design a document structure for a "blog post" that includes nested comments with fields for content, author, and timestamp.
db.blog_posts.insertOne({
  "title": "MongoDB Blog",
  "content": "Introduction to MongoDB...",
  "author": "Jane Smith",
  "comments": [
    {
      "content": "Great post!",
      "author": "Alice",
      "timestamp": new Date("2022-01-01T12:00:00Z")
    },
    {
      "content": "Thanks for sharing.",
      "author": "Bob",
      "timestamp": new Date("2022-01-02T09:30:00Z")
    }
  ]
})

// Create a document structure for a "recipe" with an array field for ingredients and another for steps.
db.recipes.insertOne({
  "name": "Spaghetti Bolognese",
  "ingredients": ["spaghetti", "ground beef", "tomato sauce", "onions"],
  "steps": ["Boil spaghetti", "Cook ground beef", "Mix with tomato sauce and onions"]
})

// Perform CRUD operations on a "students" collection: insert a new student, retrieve a student by ID, update a student's grade, and delete a student.
db.students.insertOne({ "_id": 1, "name": "Alice", "grade": "A" })
db.students.findOne({ "_id": 1 })
db.students.updateOne({ "_id": 1 }, { $set: { "grade": "B" } })
db.students.deleteOne({ "_id": 1 })

// Retrieve all documents from a "products" collection where the price is greater than $50.
db.products.find({ "price": { $gt: 50 } })

// Retrieve the top 5 highest-priced products from the "electronics" category.
db.products.find({ "category": "electronics" }).sort({ "price": -1 }).limit(5)

// Use the aggregation framework to calculate the average rating for a "movie" collection based on user reviews.
db.movies.aggregate([
  { $unwind: "$reviews" },
  { $group: { _id: null, avgRating: { $avg: "$reviews.rating" } } }
])

// Create an index on the "timestamp" field of a "logs" collection and explain how it improves query performance.
db.logs.createIndex({ "timestamp": 1 })

// Implement a text search query to find all documents in a "books" collection that contain the word "MongoDB" in the title or description.
db.books.find({ $text: { $search: "MongoDB" } })

// Update a specific comment within a "post" document, changing its content.
db.blog_posts.updateOne(
  { "_id": ObjectId("5f8a4a491c9d4400001a4af2"), "comments.author": "Alice" },
  { $set: { "comments.$.content": "Updated content" } }
)

// Add a new ingredient to the array field of a "recipe" document.
db.recipes.updateOne(
  { "_id": ObjectId("5f8a4b431c9d4400001a4af3") },
  { $push: { "ingredients": "garlic" } }
)

// Use the aggregation pipeline to group "sales" data by month and calculate the total revenue for each month.
db.sales.aggregate([
  {
    $group: {
      _id: { $month: "$date" },
      totalRevenue: { $sum: "$amount" }
    }
  }
])

// Implement sharding for a large "sensor_data" collection, considering an appropriate shard key.
sh.shardCollection("database.collection", { "shard_key": 1 })

// Set up a replica set with three nodes and demonstrate a failover scenario.
rs.initiate()
rs.add("node2.example.com")
rs.add("node3.example.com")
rs.stepDown()

// Create a text search index on multiple fields in a collection, allowing for efficient text searches.
db.collection.createIndex({ "field1": "text", "field2": "text" })

```