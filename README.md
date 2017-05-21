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

## CLASS
```ruby
class ClassName
  def initialize(args)
    @name = args[:name] || "Default Name"
    @married = args.fetch(:married, false)
  end
end
```
### Comments
`@@`- Class Variable  
`@`- Instance Variable  
`args[:key]`- set nil by default if no matching key is found and no default is given  
`args.fetch(:key)`- gives an error if no matching key is found and no default is given  

## GENERAL RUBY
### Recursion Example
```ruby
def countdown(n)
  return if n.zero? # base case
  puts n
  countdown(n-1)    # getting closer to base case
end

countdown(5)
5
4
3
2
1
```


## GIT
Delete untracked files:
` git clean -n ` => Check what will be deleted
` git clean -d ` => Delete Files

## SQL
[Propet Placement](sql/README.md)
### One-to-many relationship
![one-to-many schema](https://github.com/sf-sea-lions-2017/database-drill-one-to-many-schema-challenge/blob/master/readme-assets/schema-example.png)
*One amazon user can have many orders*
### One-to-one relationship
<img src="https://github.com/sf-sea-lions-2017/database-drill-one-to-one-schema-challenge/blob/master/readme-assets/facebook-account-schema.png" width="40%">.
*One FB user can only have on FB account, and vice-versa*
### Many to many relationship ###
![many-to-many schema](https://github.com/sf-sea-lions-2017/database-drill-many-to-many-schema-challenge/blob/master/readme-assets/many-to-many-schema.png)
*An author can write many books, and a book can have many authors.*

![many-to-many schema](https://github.com/sf-sea-lions-2017/database-drill-many-to-many-schema-challenge/blob/solo-lucaskuhn/many-to-many.png)
*A user can have many reviews and favoritings*
*A favoriting has a user who made it and a review*
*A review has an author, a product, and can have many favoritings*
*A review is about one product, one product can have many reviews*

Writing to DB files example : [Phase 0 Puppy Maker](https://github.com/LucasKuhn/phase-0-tracks/blob/master/databases/puppy_maker/puppy_maker.rb)


## SHORTCUTS
### Mac
` cmd + shift + 4 ` -> Screenshot
` cmd + option + arrows ` => Resize window size
### Sublime
` cmd + option + 2 ` -> Split screen in two files

<p><a href="https://github.com/LucasKuhn/notes">Link Example</a></p>

## GitHub Markdown Resources
- [Highlight Code Blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/)
- [Writing on GitHub](https://help.github.com/categories/writing-on-github/)
