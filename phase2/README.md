# [PHASE 2 GUIDE](https://github.com/sf-sea-lions-2017/phase-2-guide)
- [FINISH THE DAMN PREP WORK](https://github.com/sf-sea-lions-2017/phase-2-guide/blob/sf/week-4/pre-work.md)

# [REST](https://github.com/sf-sea-lions-2017/phase-2-guide/blob/sf/resources/case-eee_72715407554996828e0c.md)

## POST FORMS
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
