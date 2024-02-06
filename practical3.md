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