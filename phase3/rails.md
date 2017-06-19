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
Check error, then
```ruby
# in config/routes.rb
LearningRails::Application.routes.draw do
  get '/' => 'pages#index'
end
```
```ruby
# in app/controllers/pages_controller.rb
class PagesController < ApplicationController
  def index
    @sign_text = params[:sign_text]
    # Look in app/views/pages/index.html.erb
  end
end
```
Note: Now we have to call .html.erb since it can handle other inputs. Also, you don't need to call erb: anymore since Rails assumes it will find a file with the same name as the action in a folder with the same name as the controller.

## Conventions

Don't Repeat Yourself: DRY is a principle of software development which states that "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system." By not writing the same information over and over again, our code is more maintainable, more extensible, and less buggy.
Convention Over Configuration: Rails has opinions about the best way to do many things in a web application, and defaults to this set of conventions, rather than require that you specify minutiae through endless configuration files.
