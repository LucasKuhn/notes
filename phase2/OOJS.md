## DECLARING VARIABLES
```javascript
var valueOne = 5;
var valueTwo = 10;
var result = valueOne + valueTwo;
```

## Console I/O
```javascript
console.log("I will now ask you for your name.");
var name = prompt("Enter your name");
console.log("Hello ".concat(name, ". How are you"));
```

## ADDING AND MULTIPLYING 
```javascript
var num = 3;
var result = 0;

num = num * 4;
result = result + 1;
--------------------
num *= 4;
result += 1;
```

## CLASSES
In Ruby:
```ruby
class Band
  def initialize(name, members, albums)
    @name = name
    @members = members
    @albums = albums
  end
  
  # Rest of class omitted ...
end
```
In JavaScript - Constructor Function
```javascript
function Band(name, members, albums) {
  this.name = name;
  this.members = members;
  this.albums = albums;
}

weezerMembers = ["Rivers Cuomo", "Patrick Wilson", "Brian Bell", "Scott Shriner"]
weezerAlbums  = ["Weezer (The Blue Album)", "Weezer (The Green Album)", "Weezer (The Red Album)", "Weezer (The White Album)"]

weezer = new Band("Weezer", weezerMembers, weezerAlbums)
```
## OBJECT WITH FUNCTIONS
```javascript
var person = {
  firstName: "Kweku",
  lastName: "White",
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}

person.firstName;
// => "Kweku"
person.fullName();
// => "Kweku White"
```
### CONSTRUCTOR FUNCTION (Persons)
```javascript
var Person = function(firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
}

Person.prototype.fullName = function() {
  return this.firstName + " " + this.lastName
}

var grayson = new Person("Grayson", "Arthur");
grayson.firstName;
// => "Grayson"

var warner  = new Person("Warner", "Constable");
warner.fullName();
// => "Warner Constable"
```
## JASMINE TESTS
```javascript
describe "a string with my name" do
  let(:my_name) { "Carson Hollands" }
  
  it "is my name" do
  	expect(my_name).to eq "Carson Hollands"
  end
end
Figure 3. Testing the value of a Ruby string object with RSpec.

describe("a string with my name", function() {
  var myName;
  
  beforeEach(function() {
    myName = "Carson Hollands";  
  });
  
  it("is my name", function() {
    expect(myName).toEqual("Carson Hollands");
  });
});
```
## [ORANGE TREES IN JS](https://github.com/sf-sea-lions-2017/oojs-orange-tree-challenge/tree/pair-intell-gent%2Clucaskuhn)
### [Orange-trees.js](https://github.com/sf-sea-lions-2017/oojs-orange-tree-challenge/blob/pair-intell-gent%2Clucaskuhn/src/orange_tree.js)
## [BIKES AND STATIONS](https://github.com/sf-sea-lions-2017/oojs-bikes-and-stations-challenge/tree/solo-lucaskuhn)
### [station.js](https://github.com/sf-sea-lions-2017/oojs-bikes-and-stations-challenge/blob/solo-lucaskuhn/src/station.js)

## [GARDEN.js](https://github.com/sf-sea-lions-2017/oojs-garden-challenge/blob/pair-intell-gent%2Clucaskuhn/src/garden.js)

## [JS RACER](https://github.com/sf-sea-lions-2017/phase-2-guide/blob/sf/week-6/monday.md)
