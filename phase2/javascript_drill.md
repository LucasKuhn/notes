## RECTANGLE FUNCTION
```javascript
var rectOne   = {width: 10, height: 20};
var rectTwo   = {width: 32, height: 13};
var rectThree = {width: 20, height: 10};

function equal(rect1, rect2) {
  return ( (rect1.width  == rect2.width && rect1.height == rect2.height ) ||
           (rect1.height == rect2.width && rect1.width  == rect2.height ) );
};

function area(rect1) {
  return ( rect1.width * rect1.height );
};

function perimeter(rect1) {
  var sides1 = rect1.width * 2;
  var sides2 = rect1.height * 2;
  return sides1 + sides2
};

function diagonal(rect1) {
  var width_squared = rect1.width * rect1.width;
  var height_squared = rect1.height * rect1.height;
  var diagonal = Math.sqrt(width_squared + height_squared)
  return diagonal
};

function isSquare(rect1) {
  if (rect1.width == rect1.height)
    return true
  else
    return false;
};

```
## VALID TRIANGLE
```javascript
function validTriangle(a, b, c) {
  if (a == 0 || b == 0 || c == 0) {
    return false;
  }
  if (a + b < c || a + c < b || c + b < c) {
    return false;
  }
  return true;
}
```
