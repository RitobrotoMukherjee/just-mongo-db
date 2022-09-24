## To create `learning` db
> `use('learning')` **OR** `use learning`

## To create `mongo-first` collection
> In MongoDB `collection` ~ `table` in `SQL`
> `db.createCollection('mongo-first')`
> `db.createCollection('test-two')`
> `db.createCollection('testing')`

## Show created DB
> `show.dbs`

## Show Collections inside a DB
> `show collections`

## Switch to another DB or create DB
> - To switch to admin db
>    - `use admin`

> - To create new DB
>   - `use new-db` **OR** `use('new-db')`

## Drop a collection

### Switch to the db
- > `use learning`

### Dropping Collection
**Collection name without special characters**
- > `db.testing.drop()`
**Collection names with special character**
- > `db.getCollection('mongo-first').drop()`

## Drop DB
- > `use learning`
- > `db.dropDatabase()`
