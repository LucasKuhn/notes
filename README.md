# Week 2
Notes for what I learned
## RSPEC
```ruby
describe Class/Method do
  let(:object) { Class.new("Amazing Name") }

  it 'can do this exact thing' do
    expect(object.name).to eq('Amazing Name')
  end

  it 'can use a method to change a variable' do
   expect { object.change_name_method('Another Name') }.to change { object.name }.to 'Lame'
  end

  it 'has a readable and writable first name' do
    expect { object.name = 'Lame' }.to change { onject.name }.from('Amazing Name').to('Lame')
  end
end
```

## CLASSES
### Initialize recieving a hash argument
```ruby
class ClassName
  def initialize(args)
    @name = args[:name] || "Default Name"
    @married = args.fetch(:married, false)
  end
end
#args[:key] - set nil by default if no matching key is found and no default is given  
#args.fetch(:key) - gives an error if no matching key is found and no default is given  
```
### Inheritance
```ruby
class Class < SuperClass
  def initialize
   super #=>Copy all initialize from SuperClass
   @classvar = "Another Value"
  end 
end
```
### Comments
`@@`- Class Variable  
`@`- Instance Variable  

## GENERAL RUBY
### Recursion
```ruby
def countdown(n)
  return if n.zero? # base case
  puts n
  countdown(n-1)    # getting closer to base case
end

countdown(5) # => 5,4,3,2,1
```
### Reduce
```ruby 
  #collection.reduce(initial_value, :name_of_method)
  [2,2,3].reduce(0, :+) => 7
  [2,2,3].reduce(1, :*) => 12
  #Also take blocks
  [2,2,3].reduce(1) {|sum,element| sum*element}
```
## SQL SCHEMAS
[Images and details here](sql/README.md)

## SHORTCUTS
### Mac
` cmd + shift + 4 ` -> Screenshot
` cmd + option + arrows ` => Resize window size
### Sublime
` cmd + option + 2 ` -> Split screen in two files  
### GIT  
Delete untracked files:  
` git clean -n ` => Check what will be deleted  
` git clean -d ` => Delete Files  

<p><a href="https://github.com/LucasKuhn/notes">Link Example</a></p>

## GitHub Markdown Resources
- [Highlight Code Blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/)
- [Writing on GitHub](https://help.github.com/categories/writing-on-github/)
