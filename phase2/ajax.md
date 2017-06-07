# AJAX
Asyncronous JavaScript And XML.
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

Nice trick to show what you clicked:
```javascript
$('body').on('click', function(event){
console.log(event.target) });
```
