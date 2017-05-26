## WORKFLOW  
1. Install bundle gems from Gemfile.lock  
`bundle install` or `bundle`  
2. Create the DataBase in the db/ directory  
`bundle exec rake db:create`  
3. Generate the the next migration (With proper naming)  
`bundle exec rake generate:migration NAME=create_class`  
4. Migrate!  
`bundle exec rake db:migrate`  
5. Check if it is all good  
`bundle exec spec`  

- INSTALL BUNDLER  
`$ gem install bundler`   
- CHECK ALL RAKE COMMANDS    
`$ bundle exec rake -T`  

### WHITHIN THE CONSOLE 
- `ActiveRecord::Base.connection.tables` Names of tables  
- `ActiveRecord::Base.connection.columns(:table_name)` Objects representing columns in the table  
- `ClassName` See the class and atributes  
- `ClassName.all` or `ClassName::all` Return records from table as instances of the class  
