# MONGODB
## The hell it is?
MongoDB is a free and open-source cross-platform document-oriented database program. Classified as a **NoSQL database** program, MongoDB uses JSON-like documents with schemas.


## The hell is NoSQL?
"non SQL", "non relational" or "not only SQL"
database provides a mechanism for storage and retrieval of data which is modeled in means other than the tabular relations used in relational databases.

## Why sould we care?
I could address this but let's watch a video instead
[mongoDB Atlas](https://www.youtube.com/watch?v=H3P0lW94L2Q)
- Data Control
- Encryption
- Deployed across availability zones

 In Mongo, we don’t work with tables and rows, we work with collections and documents. Documents contain JSON/BSON hashes, so any data that can be represented as a hash can be stored in Mongo. Mongo is a schemaless database, meaning there’s no requirements nor enforcement about the structure of the data in a document.  

## What we are used to
SQLite, MySQL, Postgres, Active Record in general -> Use an Object Relational Mapper to translate the things in your code and the relational representation in the database.
ODM 
## What we mongoDB needs
Since it is an Object-Document-Mapper (ODM) it doesn't use active record and for ruby we can use something else instead: The almighty magical Mongoid 

# HOW TO
```
$ brew install mongodb
```
```
$ rails new whatever-app --skip-active-record
```
in the Gemfile add:
```
gem "mongoid"
```
*The hell in mongoid?* -> Basically does on MongoDB what ActiveRecord does on normal databases.
```
$ rails generate mongoid:config
```
```
rails generate scaffold person name street city state
```
MongoDB doesn't have database, so no migration needed!
Check the model:
```
class Person
  include Mongoid::Document
  field :name, type: String
  field :street, type: String
  field :city, type: String
  field :state, type: String
end
```

[Learn MongoDB](https://university.mongodb.com/)
[Github Repo](https://github.com/mongodb)
[Ruby driver](https://github.com/mongodb/mongo-ruby-driver)
[What is NoSQL](https://www.mongodb.com/nosql-explained)
[Quick intro with Rails](http://kerrizor.com/blog/2014/04/02/quick-intro-to-mongodb-in-rails)
[Using on Rails 5](http://www.traversymedia.com/using-mongodb-ruby-rails-5/)
[MongoDB with Mongoid](http://ianthro.com/using-mongodb-with-rails)
[Mongoid Github](https://github.com/mongodb/mongoid)
[Foreign Keys](https://stackoverflow.com/questions/17475913/foreign-keys-and-mongoid)
