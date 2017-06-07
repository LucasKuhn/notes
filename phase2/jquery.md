```javascript
// Shorthand for document ready
$(function(){
  styleItListener();
  // your code goes here.
});

var styleItListener = function(){
  var $form = $('#style_editor');
  $form.on('submit', function(){
    grabTheSelector();
    event.preventDefault();

  });
};

var grabTheSelector = function(){
  var $selector = $("input[name = 'selector']").val()
  var $property = $("input[name = 'property']").val()
  var $value = $("input[name = 'value']").val()
  // alert($property);

  $($selector).css($property,$value);
  alert("Did the color change?");
};
```
```javascript
$(document).ready(function () {
  switchTab();
});


var switchTab = function(){

  $(".tabs li").on("click", function(){
  $('li').removeClass("active");
  $(this).addClass("active");
  $('.tab-content').hide();
  var chosen = $(this).find("a").attr("href");
  $(chosen).show();
  })
};
```
