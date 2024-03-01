
# Practical related Questions
### 1. Create a keyspace named "ecommerce" with a replication strategy of 'NetworkTopologyStrategy' and replication factor of 3, placing replicas in 'DC1' and 'DC2'.
```
CREATE KEYSPACE ecommerce WITH replication = {'class': 'NetworkTopologyStrategy', 'DC1': 3, 'DC2': 3};
```
### 2. Alter the keyspace "ecommerce" to change the replication strategy to 'SimpleStrategy' with a replication factor of 2.

```
ALTER KEYSPACE ecommerce
WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 2};
```
### 3. Create a table named "products" with columns: product_id (UUID, primary key), product_name (TEXT), price (DOUBLE), and stock_quantity (INT).
```
CREATE TABLE ecommerce.products ( product_id UUID PRIMARY KEY, product_name TEXT, price DOUBLE, stock_quantity INT );
```
### 4. Alter the table "products" to add a new column "manufacturer" of type TEXT.
```
ALTER  TABLE ecommerce.products ADD manufacturer TEXT;
```
### 5. Create an index named "idx_product_name" on the "products" table for the "product_name" column.
```
CREATE INDEX idx_product_name ON ecommerce.products (product_name);
```
### 6. Insert a new product into the "products" table with the following values: (uuid(), 'Laptop', 1200.0, 50, 'Dell').
```
INSERT  INTO ecommerce.products (product_id, product_name, price, stock_quantity, manufacturer) VALUES (uuid(), 'Laptop', 1200.0, 50, 'Dell');
```
### 7. Select all products from the "products" table.
```
SELECT * FROM ecommerce.products;
```
### 8. Update the stock_quantity of the product with product_id 'some_id' to 40.
```
UPDATE ecommerce.products SET stock_quantity =  40  WHERE product_id =  'some_id';
```
### 9. Delete the product with product_id 'some_id' from the "products" table.
```
DELETE FROM ecommerce.products WHERE product_id = 'some_id';
```
### 10. Use `nodetool status` to check the status of the Cassandra nodes in the cluster.
```
nodetool status
```
### 11. Use `nodetool compactionstats` to view information about ongoing compactions.
```
nodetool compactionstats
```
### 12. Take a snapshot of the "ecommerce" keyspace using `nodetool snapshot ecommerce`.
```
nodetool snapshot ecommerce
```
### 13. Truncate the "products" table.
```
TRUNCATE ecommerce.products;
```
### 14. Drop the index "idx_product_name."
```
DROP INDEX idx_product_name;
```
### 15. Drop the table "products."
```
DROP TABLE ecommerce.products;
```
### 16. Drop the keyspace "ecommerce."
```
DROP KEYSPACE ecommerce;
```

### 1. Design a data model for a music streaming service. Consider entities such as users, songs, playlists, and play history. Define tables and relationships to efficiently support queries for user-specific playlists, recently played songs, and popular songs.
```
CREATE TABLE users (
    user_id UUID PRIMARY KEY,
    username TEXT,
    email TEXT,
    password TEXT,
    playlists SET<UUID>,
    play_history LIST<UUID>
);

CREATE TABLE songs (
    song_id UUID PRIMARY KEY,
    title TEXT,
    artist TEXT,
    album TEXT,
    release_year INT,
    genre TEXT,
    tempo TEXT
);

CREATE TABLE playlists (
    playlist_id UUID PRIMARY KEY,
    user_id UUID,
    playlist_name TEXT,
    songs LIST<UUID>,
    created_at TIMESTAMP,
    PRIMARY KEY (user_id, playlist_id)
);
```
### 2. Write a CQL query to find the top 5 most played songs in the last month. Consider using appropriate aggregation functions and time-based filtering.
```
SELECT song_id, COUNT(*) AS play_count
FROM play_history
WHERE played_at >= dateadd(now(), 'month', -1)
GROUP BY song_id
ORDER BY play_count DESC
LIMIT 5;
```
### 3. Create a secondary index on a non-primary key column of the songs table. Write a query to retrieve all songs released in a specific year using this secondary index.
```
CREATE INDEX ON songs (release_year);

SELECT * FROM songs WHERE release_year = 2023;
```
### 4. Implement a batch operation to update the order of songs in a user's playlist. Demonstrate how batching can be utilized to ensure atomicity for multiple update operations.
```
BEGIN BATCH
    UPDATE playlists SET songs = [uuid1, uuid2, uuid3] WHERE user_id = uuid;
    APPLY BATCH;
```
### 5. Design a table to store real-time analytics data for user interactions (likes, shares, skips) with songs. Write a query to retrieve songs with the highest engagement in the last 24 hours.
```
CREATE TABLE song_engagement (
    song_id UUID PRIMARY KEY,
    likes INT,
    shares INT,
    skips INT,
    engagement_score INT
);

SELECT * FROM song_engagement WHERE writetime(song_id) >= dateadd(now(), 'day', -1) ORDER BY engagement_score DESC LIMIT 10;
```
### 6. Identify a slow-performing query in your data model. Use appropriate techniques (indexes, denormalization) to optimize the query's performance, and compare the execution times before and after optimization.
```
-- Before Optimization
SELECT * FROM songs WHERE genre = 'Rock' AND release_year = 2021;

-- After Optimization
CREATE INDEX ON songs (genre, release_year);
SELECT * FROM songs WHERE genre = 'Rock' AND release_year = 2021;
```
### 7. Simulate a scenario with a large data set of songs and users. Write a query to retrieve songs that have not been played by a specific user, considering efficient handling of large data.
```
SELECT * FROM songs WHERE song_id NOT IN (SELECT song_id FROM play_history WHERE user_id = 'user_id');
```
### 8. Create a query to retrieve songs based on a user's preferences, considering factors like genre, tempo, and artist. Optimize the query for minimal response time.
```
SELECT * FROM songs WHERE genre = 'Pop' AND tempo = 'Fast' AND artist = 'ArtistName' LIMIT 10;
```
## True/False Statements:
 1. Creating an index improves the performance of queries. : **True**
 2. Truncating a table removes the table structure along with its data. : **False**
 3. ALTER KEYSPACE is used to modify replication strategies. : **False**
 4. The `nodetool status` command provides information about the cluster's data consistency. : **False**
