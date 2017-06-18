If it was sinatra
```ruby
# in sinatra app
get '/' do
  @sign_text = params[:sign_text]
  # Look in app/views/index.erb
  erb :index
end
```
Create the server
```
rails server
```
Check if working, then
```ruby
# in config/routes.rb
LearningRails::Application.routes.draw do
  get '/' => 'pages#index'
end
```
Check error, then
```ruby
# in app/controllers/pages_controller.rb
class PagesController < ApplicationController
end
```
Check error, then
```ruby
# in app/controllers/pages_controller.rb
class PagesController < ApplicationController
  def index
  end
end
```
