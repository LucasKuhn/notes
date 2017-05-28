# RAKE
Rake is a Ruby gem that helps automate repetitive tasks. It is sometimes referenced as a build tool, since it helps build a file based on another (a Markdown to HTML, for example.) [More Info](https://github.com/ruby/rake#presentations-and-articles-about-rake)  
Like RSpec, it is a Domain Specific Language(DSL) so the syntax may be a little bit weird, but it is ruby!

### RAKE TASKS
They are run in the Rakefile:  
```ruby 
# normal 'method' called 'greet'
desc "Say hello to the world."
task :greet do
  puts "Hello world!"
end

# the inquire is dependent on greet, it will run greet first
task :inquire => :greet do
  puts "How are you?"
end

# Similar to running ARGV, you can pass arguments in [:name], ex: ["Bob"] 
task :introduce, [:name] do |task, args|
  puts "I'm #{args[:name]}."
end

task :converse, [:name] => [:greet, :introduce, :inquire]
```
On the terminal, you can run `rake converse["Bob"]` and the following will run:  
Greet, then Introduce(with the name:"Bob"), and then the Inquire.

### DEFAULT TASK
You can have a default task that will run if you call only `rake` on the terminal
```ruby 
task :default => :greet
```
*On this case, calling rake would call the default that calls :greet first*  

### NAMESPACES
You can encapsulate many tasks the same way a module incapsulates methods
```ruby
namespace :interactions do
  task :greet do
    puts "Hello world!"
  end

  task :farewell do
    puts "Bye."
  end
end
```
With modules, you call them by running `ModuleName.method`  
With a rake task, you run on the console `rake namespace:task`, for example: `rake interactions:greet`   
Do you see what `rake db:create` means now? (;  
