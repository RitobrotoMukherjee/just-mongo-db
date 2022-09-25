# CRUD Operation Learning

---
## It's a MongoDB(NoSQL) for learning application.

## Create DB
- > `use learning`

## Create Collection
- > `db.createCollection('topics')`
- > `db.createCollection('source')`

## Insert Datum

### Insert into `topics` collection - insertOne
> Never use `id` column as MongoDB generates `id` on it's own.
- > `db.topics.insertOne({ name: "Test", type: 1234 })`
- > `db.topics.insertOne({ name: 'Test CRUD', type: 'Testing' })`
- > `db.topics.insertOne({ name: 'Test CRUD 2', type: 'Testing' })`
- > `db.topics.insertOne({ name: "Full stack development", type: "Software" })`

### Insert into `topics` collection - insertMany
> Never use `id` column as MongoDB generates `id` on it's own.
- > `db.topics.insertMany([ { name: "Mobile Development", type: "Software" }, { name: "Wrestling", type: "Combat Sports", topic: "Game" }, { name: "MMA", type: "Combat Sports", topic: "Game" }])`

## View All `topics`
- > `db.topics.find()`

## Update queries **Collection `topics`**

- > Update One: `db.topics.updateOne( { name: 'Test' }, {$set: { type: 54321 } })`
- > Update Many: `db.topics.updateMany( { type: 'Software' }, { $set: { topic: 'Technology' } })`

## Delete Record:
- > Delete One: `db.topics.deleteOne({type: 54321 })`
- > Delete Many: `db.topics.deleteMany({ type: 'Testing' })`

---
## Insert data into `source`
```
db.source.insertMany([
    {
        topic_name: "Technology",
        source: ["Books", "Online"]
    },
    {
        topic_name: "Game",
        source: ["Coach", "Seniors"]
    }
])
```