# WEEK 2
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

## Class
```ruby
class ClassName
  def initialize(args)
    @name = args[:name] || "Default Name"
    @married = args.fetch(:married, false)
  end
end
```
### Comments
```
@@ => Class Variable
@ => Instance Variable
args[:key] set's nil by default if no matching key is found
args.fetch(:key) gives an error if no matching key is found
```
## Git
Delete untracked files:  
` git clean -n ` => Check what will be deleted  
` git clean -d ` => Delete Files  

## Mac and Terminal
` cmd+shift+4 ` -> Screenshot 
<p><a href="https://github.com/LucasKuhn/notes">Link Example</a></p>

## GitHub Markdown Resources
- [Highlight Code Blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/)
- [Writing on GitHub](https://help.github.com/categories/writing-on-github/)
