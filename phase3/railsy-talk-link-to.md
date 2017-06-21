# Basics
[routes](http://guides.rubyonrails.org/routing.html)
```ruby
<%= link_to "Home", root_path %>
# => <a href="/">Home</a>
```
# Routes 
```ruby
<%= link_to 'New article(with link_to)', new_article_path %>
<a href="/articles/new">New article(normal a tag)</a>
```
# Delete
```ruby
<%= link_to 'Destroy', article_path(@article), method: :delete, data: { confirm: 'Are you sure?' } %>
# => <a rel="nofollow" data-method="delete" href="/articles/<%= @article.id %>">Destroy</a>
```
# Link_to_if
```ruby
<%= link_to_if(@current_user.nil?, "Login", { controller: "sessions", action: "new" }) %>
# If the user isn't logged in...
# => <a href="/sessions/new/">Login</a>

<%=
   link_to_if(@current_user.nil?, "Login", { controller: "sessions", action: "new" }) do
     link_to(@current_user.login, { controller: "accounts", action: "show", id: @current_user })
   end
%>
# If the user isn't logged in...
# => <a href="/sessions/new/">Login</a>
# If they are logged in...
# => <a href="/accounts/show/3">my_username</a>
```

# Link_to_unless
```ruby
<%= link_to_unless(@current_user.nil?, "Reply", { action: "reply" }) %>
# If the user is logged in...
# => <a href="/controller/reply/">Reply</a>

<%=
   link_to_unless(@current_user.nil?, "Reply", { action: "reply" }) do |name|
     link_to(name, { controller: "accounts", action: "signup" })
   end
%>
# If the user is logged in...
# => <a href="/controller/reply/">Reply</a>
# If not...
# => <a href="/accounts/signup">Reply</a>
```
# Button to 
```ruby
<%= button_to "New", action: "new" %>
# => "<form method="post" action="/controller/new" class="button_to">
#      <input value="New" type="submit" />
#    </form>"

<%= button_to "New", new_articles_path %>
# => "<form method="post" action="/articles/new" class="button_to">
#      <input value="New" type="submit" />
#    </form>"
```
# Form for
```
<%= form_for :person do |f| %>
  First name: <%= f.text_field :first_name %><br />
  Last name : <%= f.text_field :last_name %><br />
  Biography : <%= f.text_area :biography %><br />
  Admin?    : <%= f.check_box :admin %><br />
  <%= f.submit %>
<% end %>

=>
<form method="post" action="/people">
 <input type='text' name='person[first_name]'>
 <input type='text' name='person[last_name]'>
 <input type='textarea' name='person[biography]'>
 <input type='submit'>
</form>
```
