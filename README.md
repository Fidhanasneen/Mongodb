# MongoDB
## Check `monosh` Version

```js
>mongosh --version

MongoDB shell version v5.0.13
```


## Start the Mongo Shell

```js
>mongosh "YOUR_CONNECTION_STRING" --username YOUR_USER_NAME
```

## Show Current Database

```js
>db

test
```

## Show All Databases

```js
>show dbs

admin   0.000GB
blog    0.000GB
config  0.000GB
local   0.000GB
```

## Create Or Switch Database

```js
>use Big_Data

switched to db big_data

```

## Drop Database

```js
>db.dropDatabase()

{ "ok" : 1 }
```

## Create Collection

```js
>db.createCollection('Students')

{ "ok" : 1 }

```

## Show Collections

```js
>show collections

Students
```

## Insert Document

```js
>db.Students.insertOne({
  Name: 'Ardra',
  Age: 22,
  Course: 'MSc DA',
  No: 8,
  Interest: ['Reading', 'Music'],
  date: Date()
})



        "acknowledged" : true,
        "insertedId" : ObjectId("63638a03c3e198ff6a8392cf")

```

## Insert Multiple Documents

```js
>db.Students.insertMany([
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



{
        "acknowledged" : true,
        "insertedIds" : [
                ObjectId("63638a28c3e198ff6a8392d0"),
                ObjectId("63638a28c3e198ff6a8392d1"),
                ObjectId("63638a28c3e198ff6a8392d2"),
                ObjectId("63638a28c3e198ff6a8392d3")
        ]
}


```

## Find All Documents

```js
>db.Students.find()


{ "_id" : ObjectId("63638a03c3e198ff6a8392cf"), "Name" : "Ardra", "Age" : 22, "Course" : "MSc DA", "No" : 8, "Interest" : [ "Reading", "Music" ], "date" : "Thu Nov 03 2022 14:59:39 GMT+0530 (India Standard Time)" }
{ "_id" : ObjectId("63638af8c3e198ff6a8392d4"), "Name" : "Aleena", "Age" : 22, "Course" : "MSc DA", "No" : 9, "Interest" : [ "Reading", "Writing" ], "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)" }
{ "_id" : ObjectId("63638af8c3e198ff6a8392d5"), "Name" : "Stalin", "Age" : 22, "Course" : "MSc GA", "No" : 4, "Interest" : [ "Dance", "Music" ], "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)" }
{ "_id" : ObjectId("63638af8c3e198ff6a8392d6"), "Name" : "Navas", "Age" : 22, "Course" : "MSc MI", "No" : 16, "Interest" : [ "Sports" ], "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)" }
{ "_id" : ObjectId("63638af8c3e198ff6a8392d7"), "Name" : "Ajmala", "Age" : 22, "Course" : "MSc MI", "No" : 18, "Interest" : [ "Reading", "Music" ], "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)" }

```

## Find All Documents with pretty

```js
>db.Students.find().pretty()



{
        "_id" : ObjectId("63638a03c3e198ff6a8392cf"),
        "Name" : "Ardra",
        "Age" : 22,
        "Course" : "MSc DA",
        "No" : 8,
        "Interest" : [
                "Reading",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 14:59:39 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638af8c3e198ff6a8392d4"),
        "Name" : "Aleena",
        "Age" : 22,
        "Course" : "MSc DA",
        "No" : 9,
        "Interest" : [
                "Reading",
                "Writing"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638af8c3e198ff6a8392d5"),
        "Name" : "Stalin",
        "Age" : 22,
        "Course" : "MSc GA",
        "No" : 4,
        "Interest" : [
                "Dance",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638af8c3e198ff6a8392d6"),
        "Name" : "Navas",
        "Age" : 22,
        "Course" : "MSc MI",
        "No" : 16,
        "Interest" : [
                "Sports"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638af8c3e198ff6a8392d7"),
        "Name" : "Ajmala",
        "Age" : 22,
        "Course" : "MSc MI",
        "No" : 18,
        "Interest" : [
                "Reading",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}

```

## Find Documents with Query

```js
>db.Students.find({ Name:'Aleena' })

{
        "_id" : ObjectId("63638af8c3e198ff6a8392d4"),
        "Name" : "Aleena",
        "Age" : 22,
        "Course" : "MSc DA",
        "No" : 9,
        "Interest" : [
                "Reading",
                "Writing"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}

```

## Sort Documents

### Ascending

```js
>db.Students.find().sort({ No: 1 }).pretty()


{
        "_id" : ObjectId("63638af8c3e198ff6a8392d5"),
        "Name" : "Stalin",
        "Age" : 22,
        "Course" : "MSc GA",
        "No" : 4,
        "Interest" : [
                "Dance",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638a03c3e198ff6a8392cf"),
        "Name" : "Ardra",
        "Age" : 22,
        "Course" : "MSc DA",
        "No" : 8,
        "Interest" : [
                "Reading",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 14:59:39 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638af8c3e198ff6a8392d4"),
        "Name" : "Aleena",
        "Age" : 22,
        "Course" : "MSc DA",
        "No" : 9,
        "Interest" : [
                "Reading",
                "Writing"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638af8c3e198ff6a8392d6"),
        "Name" : "Navas",
        "Age" : 22,
        "Course" : "MSc MI",
        "No" : 16,
        "Interest" : [
                "Sports"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638af8c3e198ff6a8392d7"),
        "Name" : "Ajmala",
        "Age" : 22,
        "Course" : "MSc MI",
        "No" : 18,
        "Interest" : [
                "Reading",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}

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
