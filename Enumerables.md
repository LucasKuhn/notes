!SINGLE RESPONSABILITY!

Iteration - Each
Manipulation - Map -> Manipulating something into something else
Filtering - Select / Reject
Aggregation - Reduce
Sorting - Sort / Sort_by

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

[Enumerables Talk](https://talks.devbootcamp.com/playing-with-enumerable-methods-and-objects)
