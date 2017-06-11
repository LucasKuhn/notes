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
$(document).ready(function () {


  $('#roll-form').on('submit', function(event){
    event.preventDefault();

    var method = $(this).attr('method');
    var url = $(this).attr('action');
    var data = $(this).serialize()

    // ajax will set  request = (...)
    $.ajax({
      url: url,
      type: method,
      data: data
    })
    .done(function(response){
      // console.log(response)
      $('.roll').html(response)
    });
  });
});
```


