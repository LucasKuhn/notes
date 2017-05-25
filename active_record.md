# ACTIVE RECORD
Active Record is a Gem for ORM (Object Relational Mapping)  
It is the M on the MVC, a Model that is backed by Database  
### CREATING TABLES

The equivalent to doing this in SQL
```ruby
CREATE TABLE dogs (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name VARCHAR(50) NOT NULL,
  license VARCHAR NOT NULL,
  age INTEGER,
  weight INTEGER,
  owner_id INTEGER
  created_at DATETIME,
  updated_at DATETIME
);
```

Is this in Ruby by using ActiveRecord
```ruby
class CreateDogs < ActiveRecord::Migration[5.0] 
  def change 
    create_table :dogs do |t|
      t.string   :name, { null: false, limit: 50 }
      t.string   :license, { null: false }
      t.integer  :age
      t.integer  :weight
      t.integer  :owner_id

      t.timestamps
    end
  end
end

#It inherits from the Migration class in the ActiveRecord module
#method_name :tbl_name do |table_object|
#string = VARCHAR(255) unlesss limit
#timestamp = 2 datetime column created_at and updated_at
# {options} are good to protect the database / save space
```
The ***Migration file*** begins with a timestamp in the format YYYYMMDDHHMMSS. Thas is how it keeps track of the migrations and is able to go back, since each migration will only run once.
The filename 
### INTRODUCTION
Class names singular, CamelCase
Table namees plural, snake_case


| Class Name    | Table Name    | Foreign Key  |
| ------------- |:-------------:| ------------:|
| User          | users         | user_id      |
| LineItem      |line_items     | line_item_id |
| Deer          | deer          | deer_id      |
| Person        | people        | person_id    |

```ruby 
module ActiveRecord
  class Migration
    #...
   end
   class Base
   #...
   end
   #...
 end
```
```ruby 
  class CreateOrange < ActiveRecord::Migration
     def change
       create_table :oranges do |table| #Create table on the Orange class
        table.integer :diameter
       end 
     end
   end 
 end
 ```
### Convention
### 


### BUNDLE COMMANDS
Check all the rake commands  
`$ bundle exec rake -T`  

to install bundler  
`$ gem install bundler` 

to install bundle gems from Gemfile.lock  
`$ bundle install`  

create a database in the db/ directory  
`$ bundle exec rake db:create`  

check current database version  
`$ bundle exec rake db:version`  

run the test suite  
`$ bundle exec rake spec`  

migrating  
`$ bundle exec rake db:migrate`  

populate database with Seed Data  
`$ bundle exec rake db:seed`  

opening the console  
`$ bundle exec rake console`  

whithin the console:  
- `ActiveRecord::Base.connection.tables` Names of tables  
- `ActiveRecord::Base.connection.columns(:table_name)` Objects representing columns in the table  
- `ClassName` See the class and atributes  
- `ClassName.all` or `ClassName::all` Return records from table as instances of the class  

rollback the database(undo a migration)  
`$ bundle exec rake db:rollback`  

drop the database  
`$ bundle exec rake db:drop`  
