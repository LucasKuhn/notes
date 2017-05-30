# TO - DO
Code along this prep work!
[Snitching on Sinatra](https://github.com/sf-sea-lions-2017/snitching-on-sinatra-challenge)

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
