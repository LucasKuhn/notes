1. Create Controller
```
$ rails generate controller posts
Running via Spring preloader in process 28086
      create  app/controllers/posts_controller.rb
      invoke  erb
      create    app/views/posts
      invoke  helper
      create    app/helpers/posts_helper.rb
      invoke  assets
      invoke    coffee
      create      app/assets/javascripts/posts.coffee
      invoke    scss
      create      app/assets/stylesheets/posts.scss
```
```ruby
# controllers/posts_controller.rb
class PostsController < ApplicationController
end
```
```ruby
# app/helpers/post_helper.rb
class PostsController < ApplicationController
end
```
2. Add index routes
```ruby
# config/routes.rb
Rails.application.routes.draw do
  resources :posts
  root "posts#indes"
end
```
3. Add index on controller
```ruby
class PostsController < ApplicationController
  def index
  end
end 
```
4. Add index view (template) 
```ruby
# view/posts/index.html.erb
<h1>Index here!</h1>
```
5. Create new on controller
```ruby
  # test 3000/posts/new
  def new
  end
```
6. Add template for new route
```ruby
# views/posts/new.html.erb
<h1>New Post</h1>
<%= form_for :post, url: posts_path do |f| %>
  <p>
    <%= f.label :title %><br>
    <%= f.text_field :title %>
  </p>
  <p>
    <%= f.label :body %><br>
    <%= f.text_field :body %>
  </p>
  <p>
    <%= f.submit %>
  </p>
<% end %>
```
7. Create model for submiting the data
```
$ rails generate model Post title:string body:text
=>
      invoke  active_record
      create    db/migrate/20170620034503_create_posts.rb
      create    app/models/post.rb
```
```
$ rails db:create
$ rails db:migrate
=> Same as rake 
```
8. add create route
```ruby
  # post_controller.rb
  def create
    @post = Post.new(post_params)
    @post.save

    redirect_to @post
  end

  private
  def post_params
    params.require(:post).permit(:title, :body)
  end
```
9. Try to create post, get error

10. Add show action in the controller
```ruby
def show
  @post = Post.find(params[:id])
end
```

11. Add show action
```ruby
# posts/show.html.erb
<h1 class="title">
  <%= @post.title %>
</h1>

<p class="date">
  Submitted <%= time_ago_in_words(@post.created_at) %> Ago
</p>

<p class="body">
  <%= @post.body %>
</p>
```
12. To see all posts
```
# posts controller
  def index
    @posts = Post.all.order('created_at DESC')
  end
```
```
# posts/index.html.erb
<h1>Index here!</h1>
<% @posts.each do |post| %>
  <div class="post_wrapper">
    <h2 class="title"><%= link_to post.title, post %></h2>
    <p class="date"><%= post.created_at.strftime("%B, %d, %Y") %></p>
  </div>
<% end %>
```
13. add structure, navigation and styling
```
# views/layouts/application.html.erb
  <body>
    <div id="sidebar">
      <div id="logout">
        <%= link_to root_path do  %>
          <%= image_tag "download.svg" %>
        <% end %>
      </div>
      <ul>
        <li class="category">Website</li>
        <li><%= link_to "Blog", root_path %></li>
        <li>About</li>
      </ul>

      <ul>
        <li class="category">Social</li>
        <li>Github</li>
        <li>Email</li>
      </ul>
    </div>

    <div></div>
    <%= yield %>
  </body>
```
14. Rename application.css to .css.scss
