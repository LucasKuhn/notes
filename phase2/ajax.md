# AJAX
Asyncronous JavaScript And XML.

Nice trick to show what you clicked:
```javascript
$('body').on('click', function(event){
console.log(event.target) });
```
### Workflow
```javascript
  //   1- Select the thing! 
  //   2- Check if you have the right thing! (alert / console.log)
  //   3- Break the thing! (preventDefault)
  //   4- Make an AJAX call on the thing ($.ajax - URL, TYPE, DATA)
  //   5- Check if you got the right route and passing the right things! (params, requests)
  //   6- Create a .done to do things on the page!
  //   7- Check if your .done has the right things! (response, json)
  //   8- Display the things on the page! (.append, .html)
  //   9- Add a .fail cuz its fancy
```
### Skeleton
```javascript
// Wait for the page to load
$(document).ready(function () {
  thingThatHappens();
  especialCaseListener();
});

var thingThatHappens = function() {
  // $('tag') || $('.class') || $('#id') 
  $('.class').on('submit', function(event){
    event.preventDefault();
    // ajax will set request = (...)
    var method = $(this).attr('method');
    var url = $(this).attr('action');
    var data = $(this).serialize();
    
    var ajaxRequest = $.ajax({
      url: url,
      type: method,
      data: data
    });
    
    // .done gets the last line of the route as 'response'
    var thingYouWant = $(this).find('button');
    ajaxRequest.done(function(response){
      thingYouWant.css('color','green');
      thingYouWant.html("Replace with this!");
      thingYouWant.append("Add this!");
      // If you want to reload the page
      location.reload();
    });
    
    // Add a fail
    ajaxRequest.fail(function(response){
      alert("This bad thing happened!");
      console.error(response); // or console.warn
    });
  })
};

var especialCaseListener = function () {
    $('.parent-class').on('click','.thing-you-want',function(){
    event.preventDefault();
    // (...)
  });
};
```
#### On the route:
```ruby
  post '/posts/:id/vote' do
    post = Post.find(params[:id])
    post.votes.create(value: 1)

    if request.xhr?
      // Jason makes the things be available on the .done response (responde.post and response.points)
      content_type :json
      {post: post, points:post.points}.to_json
    else
      redirect "/posts"
    end

  end
```

