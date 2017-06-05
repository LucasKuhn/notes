```javascript
/* flower */
var Flower = function(name, color) {
  this.name = name;
  this.color = color;
}

/*

Use object literal syntax to create a garden object with
the attributes and behaviors described in spec/garden_spec.js.

*/

var garden = {
  name: "Kula Botanical Garden",
  location: "Makawao",
  flowers: [],

  addFlower: function(flower) {
    this.flowers.push(flower)
  },

  plant: function(flowers) {
    flowers.forEach(function(flower){garden.addFlower(flower); });
  },

  remove: function(flower){
    var flower_index = garden.flowers.indexOf(flower)
    garden.flowers.splice(flower_index,1)
  },

  flowersByColor: function(color) {
    var found_flowers = this.flowers.filter(
      function(flower)
      { return flower.color === color }
      );
    return found_flowers
    },

  flowersByName: function(name) {
    var found_flowers = this.flowers.filter(
      function(flower)
      { return flower.name == name }
      );
    return found_flowers
    }
}


```
