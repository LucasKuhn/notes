# AJAX
Asyncronous JavaScript And XML.

Nice trick to show what you clicked:
```javascript
$('body').on('click', function(event){
console.log(event.target) });
```
Workflow:
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

```javascript
// Wait for the page to load
$(document).ready(function () {
  thingThatHappens();
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
    ajaxRequest.done(function(response){
      current_button.css('color','green');
      current_points.html(response.points);
    });
  })
};
```


