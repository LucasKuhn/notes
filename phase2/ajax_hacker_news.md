```javascript
$(document).ready(function() {

  upVoteButton();
  deleteButton();
  postButton();
  deleteButtonListener();

});

var upVoteButton = function() {
  $('.button-form').on('submit', function(){
    event.preventDefault();
    var current_button = $(this).find('button');
    var current_points = current_button.parent().parent().find('.points');
    var url = $(this).attr('action');
    var method = $(this).attr('method');
    var ajaxRequest = $.ajax({
      url: url,
      type: method,
    })
    ajaxRequest.done(function(response){
      current_button.css('color','green');
      current_points.html(response.points);
    });
    ajaxRequest.fail(function(response){
      console.warn(response);
    });
  });
};


var postButton = function() {
  $('#posts').on('submit', function(event){
    event.preventDefault();

    var url = $(this).attr('action');
    var method = $(this).attr('method');
    var data = $(this).serialize();
    var ajaxRequest = $.ajax({
      url: url,
      type: method,
      data: data,
    });
    ajaxRequest.done(function(response){
      $('.post-container').append(response)
    });
  });
};

var deleteButton = function() {
  $('.delete').on('click',function(event){
    event.preventDefault();
    var url = $(this).attr('href');
    var ajaxRequest = $.ajax({
      url: url,
      type: "delete",
    });
    ajaxRequest.done(function(response){
      location.reload();
     });
  });
};

var deleteButtonListener = function () {
    $('.post-container').on('click','.delete',function(){
    event.preventDefault();
    var url = $(this).attr('href');
    var ajaxRequest = $.ajax({
      url: url,
      type: "delete",
    });
    ajaxRequest.done(function(response){
      location.reload();
     });
  });
};
```
