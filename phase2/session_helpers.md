```ruby
helpers do
  def current_user
    @current_user ||= User.find(session[:id]) if session[:id]
  end

  def login(user)
    session[:id] = @user.id
    redirect :'/'
  end

  def logout
    session[:id] = nil
    redirect :'/'
  end

  def logged_in?
    !!current_user
  end
end
```
