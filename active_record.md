# ACTIVE RECORD
Active Record is a Gem for ORM (Object Relational Mapping).  
It is the M on the MVC, a Model responsible for representing business dataand logic, that is backed by Database. It facilitates the creation and use of business objects whose data requires persistent storage to a database

<details>
  <summary>CONSOLE WORKFLOW (Click to Expand) </summary><p>  
  
1. Install bundle gems from Gemfile.lock  
`bundle install` or `bundle`  
2. Create the DataBase in the db/ directory  
`bundle exec rake db:create`  
3. Generate the the next migration (With proper naming)  
The file will be in db/migrate  
`bundle exec rake generate:migration NAME=create_class`  
4. Migrate!  
`bundle exec rake db:migrate`  
5. Check if it is all good  
`bundle exec spec`  

-To create a model (Class)(Ex. Student)  
The file will be in app/models    
`bundle exec rake generate:model NAME=Student`

- INSTALL BUNDLER  
`$ gem install bundler`   
- CHECK ALL RAKE COMMANDS    
`$ bundle exec rake -T`  
</p></details>  

## CREATING TABLES

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
#method_name :tbl_name do |TableDefinitionObject|
#string = VARCHAR(255) unlesss limit
#timestamp = 2 datetime column created_at and updated_at
# {options} are good to protect the database / save space
```

This second file is created when you run `bundle exec rake generate:migration NAME=create_dogs`
and the method `change` is empty by default. Create table is only one thing you can do,
more commands can be found here:  
[Active Record Migrations](http://edgeguides.rubyonrails.org/active_record_migrations.html)  

The ***Migration file*** name begins with a timestamp in the format YYYYMMDDHHMMSS. Thas is how it keeps track of the migrations and is able to go back, since each migration will only run once.

## CLASSES
```ruby
class Dog < ActiveRecord::Base
end
```
All the Class needs is inherited from `ActiveRecord::Base`. Neat!  
  
### BUNDLE EXEC RAKE CONSOLE
When you open the console using `bundle exec rake console` you can do a few calls from the Dog class
that inherited from ActiveRecord::Base.  
```sql
Dog.all
Dog.where(age: 1)
Dog.where("age = ? and name like ?", 1, '%Te%')
Dog.order(age: :desc)
Dog.limit(2)
Dog.count
Dog.pluck(:name, :age)
Dog.first
Dog.find(3) /* the id 3 */
Dog.find_by(name: "Jayda")
Dog.order(name: :asc).where(age: 1).limit(1)
```
 [Active Record Calculations](http://api.rubyonrails.org/classes/ActiveRecord/Calculations.html#method-i-pluck)  
 [Active Record Querying](http://guides.rubyonrails.org/active_record_querying.html)  

### INSTANTIATING A NEW OBJECT
```sql
new_dog = Dog.new(name: "Bear")
Dog.new(color: "brown")
Dog.count # -> 3
new_dog.persisted?
new_dog.save
Dog.count # -> 4!
```
```sql
Dog.create(name: "Max")
Dog.create [{name: "Toot"}, {name: "Cosmo"}]
Dog.find_by(license: "OH-9384764")
Dog.find_or_initialize_by(license: "OH-9384764") #-> Only Local, not persited
Dog.find_or_create_by(name: "Taj", license: "OH-9084736") #-> creates on the DB
```
### OBJECTS
Every class object has their attributes as accessor methods by default, **but** the changes we
make to them in the console are **not persistent** by default. To make them persistent, you have to
call `.save` on the object you edited on console, or you can call `.destroy` and remove it completely.
```sql
tenley = Dog.find_by(name: "Tenley")
tenley.age = 2
tenley.assign_attributes(age: 3, license: "OH-1234567")
tenley.save
tenley.
```

## VALIDATIONS
The same way you can create a table with a restriction in SQL
```sql
CREATE TABLE dogs (
  name VARCHAR(50) NOT NULL,
);
```
You can create add option to validade the input before trying to run the INSERT INTO statement in Active Record:
```ruby 
class Dog < ActiveRecord::Base
  include USGeography

  has_many :ratings
  belongs_to :owner, { class_name: "Person" }

  # owner must point to a record that actually exists (Person object)
  validates :owner, { :presence => true }

  # name and license are required
  validates :name, :license, { :presence => true }

  # license must be unique for every dog
  validates :license, { :uniqueness => true }

  # license must start with two capital letters, a dash, then any characters
  validates :license, format: { with: /\A[A-Z]{2}\-/ }

  # age is not required, but if it's present, can't be less than 0
  validates :age, { :numericality => { greater_than_or_equal_to: 0 },
                    :allow_blank  => true }

  validate :license_from_valid_state

  def license_from_valid_state
    unless self.license.instance_of? String
      errors.add :license, "must be a string"
      return
    end

    abbreviation = self.license[0..1]
    unless valid_state_abbreviation? abbreviation
      errors.add :license, "must be from a valid US state"
    end
  end
end
```
[Validation Checkers](http://guides.rubyonrails.org/active_record_validations.html#validation-helpers)  
[Rails Guide on Validation](http://guides.rubyonrails.org/active_record_validations.html)  
```ruby 
  validates :coolness, { :presence => true }
  validates :coolness, numericality: { greater_than: 1, less_than_or_equal_to: 10 }

  validates :cuteness, { :presence => true }
  validates :cuteness, numericality: { greater_than: 1, less_than_or_equal_to: 10 }

  validates :judge, :dog, { :presence => true }

  #A dog can be rated by different judges,
  #But a judge can't rate the same dog twice
  validates :judge, uniqueness: { scope: :dog}
  # -- This also works (how?)
  # validates :dog, uniqueness: { scope: :judge}
```
## INTRODUCTION (Torey Video) - Not Complete
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
