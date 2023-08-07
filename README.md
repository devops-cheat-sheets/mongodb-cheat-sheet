# MongoDB Cheat Sheet

## MongoDB Cheat Sheet
 
### Database Operations

| Command | Description |
|---------|-------------|
| `use <database>` | Switches to the specified database |
| `show dbs` | Lists all databases |
| `show collections` | Lists all collections in the current database |
| `db.dropDatabase()` | Drops the current database |

### Collection Operations

| Command | Description |
|---------|-------------|
| `db.createCollection(<name>)` | Creates a new collection with the specified name |
| `db.<collection>.insert(<document>)` | Inserts a new document into the collection |
| `db.<collection>.find()` | Retrieves all documents from the collection |
| `db.<collection>.findOne(<query>)` | Retrieves the first document that matches the query |
| `db.<collection>.update(<query>, <update>)` | Updates documents that match the query |
| `db.<collection>.remove(<query>)` | Removes documents that match the query |
| `db.<collection>.drop()` | Drops the collection |

### Querying

| Command | Description |
|---------|-------------|
| `db.<collection>.find()` | Retrieves all documents from the collection |
| `db.<collection>.find(<query>)` | Retrieves documents that match the query |
| `db.<collection>.findOne(<query>)` | Retrieves the first document that matches the query |
| `db.<collection>.find().sort(<field>)` | Sorts the result by the specified field |
| `db.<collection>.find().limit(<num>)` | Limits the number of documents returned |
| `db.<collection>.find().skip(<num>)` | Skips the specified number of documents |

### Indexing

| Command | Description |
|---------|-------------|
| `db.<collection>.createIndex(<keys>)` | Creates an index on the specified keys |
| `db.<collection>.getIndexes()` | Lists all indexes in the collection |
| `db.<collection>.dropIndex(<index>)` | Drops the specified index |

### Aggregation Framework

| Command | Description |
|---------|-------------|
| `db.<collection>.aggregate(<pipeline>)` | Performs an aggregation operation on the collection |
| `db.<collection>.aggregate([{$match: <query>}, {$group: <fields>}])` | Performs a basic aggregation with matching and grouping |
| `db.<collection>.aggregate([{$lookup: <options>}])` | Performs a lookup to join collections |
| `db.<collection>.aggregate([{$sort: <fields>}])` | Sorts the result of the aggregation |

### Updates

| Command | Description |
|---------|-------------|
| `db.<collection>.update(<query>, <update>)` | Updates documents that match the query |
| `db.<collection>.update(<query>, <update>, {multi: true})` | Updates multiple documents that match the query |
| `db.<collection>.update(<query>, {$set: <fields>})` | Sets the specified fields in the matching documents |
| `db.<collection>.update(<query>, {$unset: <fields>})` | Removes the specified fields from the matching documents |
| `db.<collection>.update(<query>, {$inc: <fields>})` | Increments the specified numeric fields in the matching documents |
| `db.<collection>.update(<query>, {$push: <fields>})` | Appends elements to an array field in the matching documents |
| `db.<collection>.update(<query>, {$addToSet: <fields>})` | Adds elements to an array field only if they do not already exist |
| `db.<collection>.update(<query>, {$pull: <fields>})` | Removes elements from an array field that match the specified criteria |

### Deletion

| Command | Description |
|---------|-------------|
| `db.<collection>.remove(<query>)` | Removes documents that match the query |
| `db.<collection>.remove({})` | Removes all documents from the collection |
| `db.<collection>.deleteOne(<query>)` | Removes a single document that matches the query |
| `db.<collection>.deleteMany(<query>)` | Removes multiple documents that match the query |

### Backup and Restore

| Command | Description |
|---------|-------------|
| `mongodump` | Creates a binary export of the entire MongoDB database |
| `mongorestore` | Restores data from a binary export created with `mongodump` |
| `mongodump --db <database> --collection <collection>` | Creates a binary export of a specific database or collection |
| `mongorestore --db <database> --collection <collection>` | Restores data to a specific database or collection |

### Miscellaneous

| Command | Description |
|---------|-------------|
| `db.stats()` | Provides statistics about the current database |
| `db.<collection>.stats()` | Provides statistics about the specified collection |
| `db.<collection>.count()` | Returns the number of documents in the collection |
| `db.<collection>.distinct(<field>)` | Returns an array of distinct values for the specified field |
| `db.getCollectionNames()` | Returns an array of collection names in the current database |
| `db.drop()` | Drops the current database |

Apologies for the incomplete response earlier. Here are more MongoDB commands:

### Aggregation Pipeline

| Command | Description |
|---------|-------------|
| `db.<collection>.aggregate([{$match: <query>}, {$group: <fields>}])` | Performs a basic aggregation with matching and grouping |
| `db.<collection>.aggregate([{$lookup: <options>}])` | Performs a lookup to join collections |
| `db.<collection>.aggregate([{$sort: <fields>}])` | Sorts the result of the aggregation |
| `db.<collection>.aggregate([{$project: <fields>}])` | Includes or excludes fields in the aggregation output |
| `db.<collection>.aggregate([{$unwind: <field>}])` | Deconstructs an array field into separate documents |
| `db.<collection>.aggregate([{$group: <fields>}])` | Groups documents by specified fields |
| `db.<collection>.aggregate([{$limit: <num>}])` | Limits the number of documents passed to the next stage |
| `db.<collection>.aggregate([{$skip: <num>}])` | Skips the specified number of documents in the pipeline |
| `db.<collection>.aggregate([{$sort: <fields>}])` | Sorts documents in the pipeline |

### Text Search

| Command | Description |
|---------|-------------|
| `db.<collection>.createIndex({<field>: "text"})` | Creates a text index on the specified field |
| `db.<collection>.find({$text: {$search: "<query>"}})` | Performs a text search on the collection |
| `db.<collection>.find({$text: {$search: "<query>", $caseSensitive: true}})` | Performs a case-sensitive text search |
| `db.<collection>.find({$text: {$search: "<query>", $language: "<language>"}})` | Performs a text search with a specific language |
| `db.<collection>.find({$text: {$search: "<query>", $diacriticSensitive: true}})` | Performs a diacritic-sensitive text search |
| `db.<collection>.find({$text: {$search: "<query>"}}).sort({<field>: {$meta: "textScore"}})` | Performs a text search and sorts results by text score |

### Geospatial Queries

| Command | Description |
|---------|-------------|
| `db.<collection>.createIndex({<field>: "2dsphere"})` | Creates a 2dsphere index on the specified field for geospatial queries |
| `db.<collection>.find({<field>: {$near: {$geometry: {type: "Point", coordinates: [<longitude>, <latitude>]}}}})` | Performs a near query to find documents near a specific location |
| `db.<collection>.find({<field>: {$geoWithin: {$geometry: {type: "Polygon", coordinates: [[<long1>, <lat1>], [<long2>, <lat2>], ...]}}}})` | Performs a geospatial query to find documents within a polygon |
| `db.<collection>.find({<field>: {$geoIntersects: {$geometry: {type: "Point", coordinates: [<longitude>, <latitude>]}}}})` | Performs a geospatial query to find documents that intersect a point |

### User Management

| Command | Description |
|---------|-------------|
| `use admin` | Switches to the admin database |
| `db.createUser({user: "<username>", pwd: "<password>", roles: ["<role1>", "<role2>", ...]})` | Creates a new user with the specified username, password, and
| `db.updateUser("<username>", {<update>})` | Updates the user with the specified username |
| `db.dropUser("<username>")` | Drops the user with the specified username |
| `db.grantRolesToUser("<username>", ["<role1>", "<role2>", ...])` | Grants additional roles to the user |
| `db.revokeRolesFromUser("<username>", ["<role1>", "<role2>", ...])` | Revokes roles from the user |
| `db.getUser("<username>")` | Retrieves information about the user |
| `db.changeUserPassword("<username>", "<newPassword>")` | Changes the password for the user |

### Replication

| Command | Description |
|---------|-------------|
| `rs.initiate()` | Initializes a replica set |
| `rs.add("<hostname>:<port>")` | Adds a member to the replica set |
| `rs.remove("<hostname>:<port>")` | Removes a member from the replica set |
| `rs.status()` | Retrieves the status of the replica set |
| `rs.isMaster()` | Checks if the current node is the primary in the replica set |
| `rs.secondaryOk()` | Allows read operations on secondary members |
| `db.isMaster()` | Retrieves information about the MongoDB replica set configuration |

### Sharding

| Command | Description |
|---------|-------------|
| `sh.enableSharding("<database>")` | Enables sharding for the specified database |
| `sh.shardCollection("<namespace>", {<shardKey>})` | Shards the collection based on the specified shard key |
| `sh.addShard("<hostname>:<port>")` | Adds a shard to the cluster |
| `sh.removeShard("<shard>")` | Removes a shard from the cluster |
| `sh.status()` | Retrieves the status of the sharded cluster |
| `sh.disableBalancing("<collection>")` | Disables balancing for a specific collection |
| `sh.enableBalancing("<collection>")` | Enables balancing for a specific collection |
| `sh.getBalancerState()` | Retrieves the current state of the balancer |

### Administration

| Command | Description |
|---------|-------------|
| `db.runCommand({<command>})` | Executes a database command |
| `db.adminCommand({<command>})` | Executes an administrative command |
| `db.currentOp()` | Retrieves information about current operations |
| `db.killOp(<opid>)` | Terminates the operation with the specified opid |
| `db.repairDatabase()` | Repairs the current database |
| `db.shutdownServer()` | Shuts down the MongoDB server |

This provides you with a broader range of MongoDB commands covering various areas such as user management, replication, sharding, and administration. Remember to refer to the official MongoDB documentation for detailed explanations and the most up-to-date information on these commands.