# MongoDB
## Check `monosh` Version

```js
mongosh --version
```

## Start the Mongo Shell

```js
mongosh "YOUR_CONNECTION_STRING" --username YOUR_USER_NAME
```

## Show Current Database

```js
db
```

## Show All Databases

```js
show dbs
```

## Create Or Switch Database

```js
use Big_Data
```

## Drop Database

```js
db.dropDatabase()
```

## Create Collection

```js
db.createCollection('Students')
```

## Show Collections

```js
show collections
```

## Insert Document

```js
db.Students.insertOne({
  Name: 'Ardra',
  Age: 22,
  Course: 'MSc DA',
  No: 8,
  Interest: ['Reading', 'Music'],
  date: Date()
})
```

## Insert Multiple Documents

```js
db.Students.insertMany([
  {
  Name: 'Aleena',
  Age: 22,
  Course: 'MSc DA',
  No: 9,
  Interest: ['Reading', 'Writing'],
  date: Date()
  },
  {
  Name: 'Stalin',
  Age: 22,
  Course: 'MSc GA',
  No: 4,
  Interest: ['Dance', 'Music'],
  date: Date()
  },
  {
  Name: 'Navas',
  Age: 22,
  Course: 'MSc MI',
  No: 16,
  Interest: ['Sports'],
  date: Date()
  },
  { Name: 'Ajmala',
  Age: 22,
  Course: 'MSc MI',
  No: 18,
  Interest: ['Reading', 'Music'],
  date: Date()
  }
])
```

## Find All Documents

```js
db.Students.find()
```

## Find All Documents with pretty

```js
db.Students.find().pretty()
```

## Find Documents with Query

```js
db.Students.find({ Name:'Aleena' })
```

## Sort Documents

### Ascending

```js
db.Students.find().sort({ title: 1 })
```

### Descending

```js
db.Students.find().sort({ title: -1 })
```

## Count Documents

```js
db.Students.find().count()
db.Students.find({ category: 'news' }).count()
```

## Limit Documents

```js
db.Students.find().limit(2)
```

## Chaining

```js
db.Students.find().limit(2).sort({ title: 1 })
```

## Find One Document

```js
db.Students.findOne({ likes: { $gt: 3 } })
```

## Update Document

```js
db.Students.updateOne({ title: 'Post 1' },
{
  $set: {
    category: 'Tech'
  }
})
```

## Update Document or Insert if not Found

```js
db.Students.updateOne({ title: 'Post 6' },
{
  $set: {
    title: 'Post 6',
    body: 'Body of post.',
    category: 'News'
  }
},
{
  upsert: true
})
```

## Increment Field (`$inc`)

```js
db.Students.updateOne({ title: 'Post 1' },
{
  $inc: {
    likes: 2
  }
})
```

## Update Multiple Documents

```js
db.Students.updateMany({}, {
  $inc: {
    likes: 1
  }
})
```

## Rename Field

```js
db.Students.updateOne({ title: 'Post 2' },
{
  $rename: {
    likes: 'views'
  }
})
```

## Delete a Document

```js
db.Students.deleteOne({ title: 'Post 6' })
```

## Delete Multiple Documents

```js
db.Students.deleteMany({ category: 'Tech' })
```

## Greater & Less Than

```js
db.Students.find({ views: { $gt: 2 } })
db.Students.find({ views: { $gte: 7 } })
db.Students.find({ views: { $lt: 7 } })
db.Students.find({ views: { $lte: 7 } })
```
