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
>db.Students.find().sort({ No: -1 }).pretty()



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

```

## Count Documents

```js
>db.Students.find().count()

5


>db.Students.find({ Course: 'MSc DA' }).count()

2


```

## Limit Documents

```js
>db.Students.find().limit(2).pretty()


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


```

## Chaining

```js
>db.Students.find().limit(3).sort({Name:1}).pretty()



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

```

## Find One Document

```js
>db.Students.findOne({ Age: { $gt: 20 } })


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

```

## Update Document

```js
>db.Students.updateOne({ Name: 'Navas' },
{
  $set: {
    Age: 23
  }
})


{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }

```
## After Updation

```js
>db.Students.findOne({ Name:'Navas' })


{
        "_id" : ObjectId("63638af8c3e198ff6a8392d6"),
        "Name" : "Navas",
        "Age" : 23,
        "Course" : "MSc MI",
        "No" : 16,
        "Interest" : [
                "Sports"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}

```

## Update Document or Insert if not Found

```js
>db.Students.updateOne({ Name: 'Ardra' },
{
  $set: {
  Name: 'Ardra Rajeesh',
  Age: 22,
  Course: 'MSc DA',
  No: 7,
  Interest: ['Reading', 'Music','Travel'],
  date: Date()
  }
},
{
  upsert: true
})


{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }

```

## Increment Field (`$inc`)

```js
>db.Students.updateOne({ Name:'Stalin' },
{
  $inc: {
    Age:1
  }
})


{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }


>db.Students.findOne({ Name:'Stalin' })



{
        "_id" : ObjectId("63638af8c3e198ff6a8392d5"),
        "Name" : "Stalin",
        "Age" : 23,
        "Course" : "MSc GA",
        "No" : 4,
        "Interest" : [
                "Dance",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}

```

## Update Multiple Documents

```js
>db.Students.updateMany({}, {
  $inc: {
    No: 1
  }
})


{ "acknowledged" : true, "matchedCount" : 5, "modifiedCount" : 5 }



>db.Students.find().pretty()



{
        "_id" : ObjectId("63638a03c3e198ff6a8392cf"),
        "Name" : "Ardra Rajeesh",
        "Age" : 22,
        "Course" : "MSc DA",
        "No" : 8,
        "Interest" : [
                "Reading",
                "Music",
                "Travel"
        ],
        "date" : "Thu Nov 03 2022 16:30:11 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638af8c3e198ff6a8392d4"),
        "Name" : "Aleena",
        "Age" : 22,
        "Course" : "MSc DA",
        "No" : 10,
        "Interest" : [
                "Reading",
                "Writing"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638af8c3e198ff6a8392d5"),
        "Name" : "Stalin",
        "Age" : 23,
        "Course" : "MSc GA",
        "No" : 5,
        "Interest" : [
                "Dance",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("63638af8c3e198ff6a8392d6"),
        "Name" : "Navas",
        "Age" : 23,
        "Course" : "MSc MI",
        "No" : 17,
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
        "No" : 19,
        "Interest" : [
                "Reading",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}

```

## Rename Field

```js
>db.Students.updateOne({ Name: 'Aleena' },
{
  $rename: {
    Interest: 'Hobby'
  }
})



{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 1 }



>db.Students.find({Name:'Aleena'}).pretty()



{
        "_id" : ObjectId("6363a94f7ce8d232c5d49067"),
        "Name" : "Aleena",
        "Age" : 22,
        "Course" : "MSc DA",
        "No" : 9,
        "date" : "Thu Nov 03 2022 17:13:11 GMT+0530 (India Standard Time)",
        "Hobby" : [
                "Reading",
                "Writing"
        ]
}

```

## Delete a Document

```js
>db.Students.deleteOne({ Name: 'Ajmala' })


{ "acknowledged" : true, "deletedCount" : 1 }


```

## Delete Multiple Documents

```js
>db.Students.deleteMany({ Course: 'MSc MI' })


{ "acknowledged" : true, "deletedCount" : 1 }

```

## Greater & Less Than

```js
>db.Students.find({ Age: { $gt: 20 } }).pretty()




{
        "_id" : ObjectId("63638af8c3e198ff6a8392d5"),
        "Name" : "Stalin",
        "Age" : 23,
        "Course" : "MSc GA",
        "No" : 5,
        "Interest" : [
                "Dance",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("6363a8e45881447be22f55b8"),
        "Name" : "Ardra Rajeesh",
        "Age" : 22,
        "Course" : "MSc DA",
        "Interest" : [
                "Reading",
                "Music",
                "Travel"
        ],
        "No" : 7,
        "date" : "Thu Nov 03 2022 17:11:24 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("6363a94f7ce8d232c5d49067"),
        "Name" : "Aleena",
        "Age" : 22,
        "Course" : "MSc DA",
        "No" : 9,
        "date" : "Thu Nov 03 2022 17:13:11 GMT+0530 (India Standard Time)",
        "Hobby" : [
                "Reading",
                "Writing"
        ]
}



>db.Students.find({ No: { $gte: 8 } }).pretty()



{
        "_id" : ObjectId("6363a94f7ce8d232c5d49067"),
        "Name" : "Aleena",
        "Age" : 22,
        "Course" : "MSc DA",
        "No" : 9,
        "date" : "Thu Nov 03 2022 17:13:11 GMT+0530 (India Standard Time)",
        "Hobby" : [
                "Reading",
                "Writing"
        ]
}




>db.Students.find({ No: { $lt: 7 } }).pretty()



{
        "_id" : ObjectId("63638af8c3e198ff6a8392d5"),
        "Name" : "Stalin",
        "Age" : 23,
        "Course" : "MSc GA",
        "No" : 5,
        "Interest" : [
                "Dance",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}




>db.Students.find({ No: { $lte: 7 } }).pretty()



{
        "_id" : ObjectId("63638af8c3e198ff6a8392d5"),
        "Name" : "Stalin",
        "Age" : 23,
        "Course" : "MSc GA",
        "No" : 5,
        "Interest" : [
                "Dance",
                "Music"
        ],
        "date" : "Thu Nov 03 2022 15:03:44 GMT+0530 (India Standard Time)"
}
{
        "_id" : ObjectId("6363a8e45881447be22f55b8"),
        "Name" : "Ardra Rajeesh",
        "Age" : 22,
        "Course" : "MSc DA",
        "Interest" : [
                "Reading",
                "Music",
                "Travel"
        ],
        "No" : 7,
        "date" : "Thu Nov 03 2022 17:11:24 GMT+0530 (India Standard Time)"
}


```
