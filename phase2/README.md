# [PHASE 2 GUIDE](https://github.com/sf-sea-lions-2017/phase-2-guide)
- [FINISH THE DAMN PREP WORK](https://github.com/sf-sea-lions-2017/phase-2-guide/blob/sf/week-4/pre-work.md)

# [REST](https://github.com/sf-sea-lions-2017/phase-2-guide/blob/sf/resources/case-eee_72715407554996828e0c.md)

## POST FORMS
### POST
This form
```ruby 
  <form method="post" action="/words">

    Which word's anagrams would you like to see? <br>
    <input type='text' name='word'>
    <input type='submit' value='Get Anagrams'>
  </form>
```
Will redirect to a post /words  
And the params[:word] recieved will be the whatever the person typed
```ruby 
post '/words' do
 redirect "/words/#{params[:word]}"
end
# In this case it does nothing but redirect to the page
```
### PUT
Sinatra only recieves GET or POST from forms, so you can use a work-around to do PUT:  
YOu add a hidden method _method_ with a hidden content and the value put

```ruby 
<form method="post" action="dogs/<%= @dog.id %>">
  <input type="hidden" name="_method" value="put">

  <!-- continue form ... -->
</form>
```
Will redirect you to
```ruby 
  post '/dogs/:id' do 
    #Something here
  end 
```
Where :id is set as a params[:id] being sent from the post

## ACTIVE RECORD QUERY
```ruby
# Seach with a range
User.where(id:14000..14500)
```
```ruby
# Using greater than 
Event.where("starts_at > ?",Time.current).order(:starts_at)
```
