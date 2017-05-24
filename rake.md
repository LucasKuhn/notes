```ruby 
desc "Say hello to the world."
task :greet do
  puts "Hello world!"
end

#This inquire test depends on greet, it will run greet first
task :inquire => :greet do
  puts "How are you?"
end

task :converse, [:name] => [:greet, :introduce, :inquire, :farewell]
```

https://github.com/sf-sea-lions-2017/phase-1-guide/blob/sf/readings/rake/README.md
