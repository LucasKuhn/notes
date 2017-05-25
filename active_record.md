# Active Record
Active Recaord is a Gem for ORM (Object Relational Mapping)  
It is the M on the MVC, a Model that is backed by Database  

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
- `'ClassName.all` or `ClassName::all` Return records from table as instances of the class  

rollback the database(undo a migration)  
`$ bundle exec rake db:rollback`  

drop the database  
`$ bundle exec rake db:drop`  
