# BUNDLE
Bundle is a gem that provides a simple way to install gems for an application.

## `bundle install` 
It  Will read the `Gemfile` and try to install missing gems and dependencies.  
It will then create a `Gemfile.lock`, that will list all gems after installing them.
It represents the environment where our code works!

## `bundle exec`
It will make the next code run with access to the gems previously installed.  
ex:  
`$ bundle exec ruby file.rb`  
`$ bundle exec rake task`
