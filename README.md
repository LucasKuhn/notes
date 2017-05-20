# WEEK 2
Notes for what I learned
## RSPEC
```ruby
describe Class/Method do
  let(:object) { Class.new("Amazing Name") }

  it "can do this exact thing" do
    expect(object.name).to eq("Amazing Name")
  end

  it "can do something elsewhere" do
   expect { object.change_name_method = "Lame" }.to change { object.name }.to "Lame"
  end

end
````

## Class
```ruby
class ClassName

  def initialize(args)
    @name = args[:name] || "Default Name"
    @married = args.fetch(:married, false)
  end

end
#@@ => Class Variable
#@ => Instance Variable
# => args[:key] set's nil by default if no matching key is found
# => args.fetch(:key) gives an error if no matching key is found
````


<p><a href="https://github.com/LucasKuhn/notes">Link Example</a></p>

## GitHub Markdown Resources
- [Highlight Code Blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/)
- [Writing on GitHub](https://help.github.com/categories/writing-on-github/)
