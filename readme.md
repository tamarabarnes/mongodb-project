# Finding everything in the students collection 
``` c
db.students.find()
[
  {
    _id: ObjectId('68a6ce3e4140d4d9b389b03d'),
    name: 'John',
    age: 22,
    course: 'MongoDb',
    skills: [ 'Science', 'Maths' ]
  },
  {
    _id: ObjectId('68a6d2ae4140d4d9b389b03e'),
    name: 'Jack',
    age: 22,
    course: 'Maths',
    skills: [ 'Python', 'Javascript' ]
  },
  {
    _id: ObjectId('68a6d3784140d4d9b389b03f'),
    name: 'Bob',
    age: '27',
    course: 'Science'
  },
  {
    _id: ObjectId('68a6d3784140d4d9b389b040'),
    name: 'Charlie',
    age: '20',
    course: 'Geography'
  }
]
``` 
# Finding a specific condition - age is 20 
``` c 
db.students.find({age:20})

[
  {
    _id: ObjectId('68a6d3784140d4d9b389b040'),
    name: 'Charlie',
    age: 20,
    course: 'Geography'
  }
]
```
# Give me a list with name and course included, and _id is NOT included 
``` c
db.students.find({}, { name: 1, course: 1, _id: 0 })
```
## Return all students, but only display their name and course fields, and don’t show the _id. This gives the result below 

``` c
[
  { name: 'John', course: 'MongoDb' },
  { name: 'Jack', course: 'Maths' },
  { name: 'Bob', course: 'Science' },
  { name: 'Charlie', course: 'Geography' }
]
```

# Comparison operators $ 
## find me a document within the students collection where age is greater than 21 
``` c
db.students.find({ age: {$gt: 21}})
```
### this will give me all students with age over 21 

# UPDATING FIELDS - Update ONE
## updateOne updates one document
## Example of updating fields 
### updating age on the document where the objectID is specified. so this is saying update the age to 22 where the objectID is 68a6d2ae4140d4d9b389b03e
``` c
db.students.updateOne( {_id: ObjectId('68a6d2ae4140d4d9b389b03e')}, { $set: { age: 22 }});
```
# UPDATING FIELDS - update Many 
## here i am updating documents with course: 'MongoDb', and updating skills 
``` c 
school> db.students.updateMany(
... { course: 'MongoDb'},
... {$set: {skills: ['Physics', 'Mathematics', 'Biology']}})
```