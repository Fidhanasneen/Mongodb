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
db.posts.insertMany([
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
db.posts.find().sort({ title: 1 })
```

### Descending

```js
db.posts.find().sort({ title: -1 })
```

## Count Documents

```js
db.posts.find().count()
db.posts.find({ category: 'news' }).count()
```

## Limit Documents

```js
db.posts.find().limit(2)
```

## Chaining

```js
db.posts.find().limit(2).sort({ title: 1 })
```

## Find One Document

```js
db.posts.findOne({ likes: { $gt: 3 } })
```

## Update Document

```js
db.posts.updateOne({ title: 'Post 1' },
{
  $set: {
    category: 'Tech'
  }
})
```

## Update Document or Insert if not Found

```js
db.posts.updateOne({ title: 'Post 6' },
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
db.posts.updateOne({ title: 'Post 1' },
{
  $inc: {
    likes: 2
  }
})
```

## Update Multiple Documents

```js
db.posts.updateMany({}, {
  $inc: {
    likes: 1
  }
})
```

## Rename Field

```js
db.posts.updateOne({ title: 'Post 2' },
{
  $rename: {
    likes: 'views'
  }
})
```

## Delete a Document

```js
db.posts.deleteOne({ title: 'Post 6' })
```

## Delete Multiple Documents

```js
db.posts.deleteMany({ category: 'Tech' })
```

## Greater & Less Than

```js
db.posts.find({ views: { $gt: 2 } })
db.posts.find({ views: { $gte: 7 } })
db.posts.find({ views: { $lt: 7 } })
db.posts.find({ views: { $lte: 7 } })
```
