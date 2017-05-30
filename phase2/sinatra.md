## COMMENTS
Cinnamon Sticks `<%= %>` display the result of the code inside  
Icecream Cones `<% %>` don't display the result to the page

# SINATRA
It is a DSL (Domain Specific Language) for quickly creating web applications.
It acts as the SERVER, recieves and handles requests.
OBS: It will route from the top-down  

## HOW IT ALL WORKS
The HTTP Client send the request to server and the server sends a response back.  

## CONFIGURATIONS
Sinatra has a `config.ru` file that requires the file `environment.rb` and then runs Sinatra.  

In `environment`:  
- Sets up bundler
- Require gems, 
- Require erb, 
- Sets where the views files are

## REQUESTS
HTTP REQUEST HEADER:
```
GET / HTTP/1.1
POST /form-examples HTTP/1.1
```
THE SINATRA ROUTING:
```ruby
require 'sinatra'
get '/' do
  "Hello World"
end

post '/form-examples' do
  ...code-here...
end
```
## VIEW PARAMS IN SHOTGUN TERMINAL
``` ruby
puts "==============\n"
puts params.inspect
puts "==============\n"
```
## VIEWS DIRECTORY
Is where the templates (erb) are stored.

# RESOURCES
[Intro Video](https://talks.devbootcamp.com/intro-to-sinatra-1)

# Prep Work!
[Snitching on Sinatra](https://github.com/sf-sea-lions-2017/snitching-on-sinatra-challenge)
```
$ gem list sinatra
$ gem install sinatra  
```
```ruby
#filename: sinatra.rb
require 'sinatra'
```
```
$ ruby sinatra.rb
```
```ruby
get '/' do
  "Hello world!"
end

get '/about' do
  "A little about me."
end
```
```ruby
get '/about' do
  "A little about <b>me</b>."
  "<h1>I'm really excited you're here!</h1>"
end
```
```ruby
get '/about' do
  erb :about # => same as erb(:about)
end
```
```
$ mkdir views
$ touch views/about.erb
```
```ruby
# about.erb
<h1>I'm really excited you're here!</h1>
```
```
$ gem install shotgun
```
``` ruby
# sinatra.rb
set :views, File.join(File.dirname(__FILE__), "views")
```
```ruby
get '/about' do
  @ice_cream_cones = rand(30) + 1
  erb :about
end
```
```ruby
# about.erb
<h1>I once ate <%= @ice_cream_cones %> ice cream cones in one sitting!</h1>
```
```ruby 
get '/greetings/:name' do
  params[:name]
end
```
```ruby
get '/greetings/:name' do
  "Hey #{params[:name]}!"
end
```
```ruby 
get '/cities/:city/greetings/:name' do
  "Hey #{params[:name]}! Welcome to the #{params[:city]} greeting page!"
end
```
```ruby
get '/greetings' do
  erb :greetings
end
```
```ruby
# greetings.erb
<h1><%= @greeting %>, friend!</h1>

<form action="/custom_greetings" method="post">
  <input type="text" name="greeting">
  <input type="submit">
</form>
```
```ruby 
post '/custom_greetings' do
  "Hello World"
end
```
```ruby
<% if @greeting %>
  <h1><%= @greeting %>, friend!</h1>
<% else %>
  <h1>Hello, friend!</h1>
<% end %>
```
