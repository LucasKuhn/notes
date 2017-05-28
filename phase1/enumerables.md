# Enumerables
Enumerable is the name of a module. This module is included in Array and Hashes. You can check this by opening IRB and typing `Array.included_modules` and check the modules contained in the Array class. You can also check which methods are in the Enumerable module by typing `Enumerable.instance_methods.sort`
### What are they for?
We use them iterate,search,sort and manipulate collection. More specifically:  
  
**Iteration** - EACH  
**Manipulation** - MAP   
**Filtering** - SELECT / REJECT  
**Aggregation** - REDUCE  
**Sorting** - SORT / SORT_BY  
There are many more methods, but these are the most common ones.

#### SELECT - FILTER
Array.select{|item| item.something } 
Returns a new array containing all elements of ary 
for which the given block returns a true value.

#### MAP
  def teacher_names(teachers)
  array.map{|teachers| "#{teachers.first_name} #{teacher.last_name}"}
  end
  
#### REJECT
  teachers = array.reject{|teacher| teacher.kitten_love == :hatred }
  teacher_names(teachers)

#### SORT BY 
  
  -Accepts one argument in the block  
  -Translate to number(usually using index)
  Array.sort_by{|teacher| teacher.age }
  -----------------------
  teachers.sort_by{|teacher| [teacher.last_name, teacher.first_name] }
  ["A","B"]
  ["A","C"]
  
#### SELECT
  teacher.select{|teacher| teacher.location == "San Diego"}.sort_by(&:last_name)
  when calling one thing only - standart
  
#### SORT
  teachers.sort{|a.b| a <=> b }
  
### .REVERS - Reverse Things

# CLASS
create a .to_s method to display what a string representation of the method is 
puts call turns objects into string by calling .to_s
by default object of classes show the object class and id
self. is implied

any?

CLASS_VARIABLE -> always in class
Class::CLASS_VARIABLE  

[Enumerables DBC Talk](https://talks.devbootcamp.com/playing-with-enumerable-methods-and-objects)
[Enumerables Concept](https://www.sitepoint.com/guide-ruby-collections-iii-enumerable-enumerator/)

