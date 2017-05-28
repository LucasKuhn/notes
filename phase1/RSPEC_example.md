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
### Tips
- You can add --fail-fast to the end so the testing will stop after the first fail  
Ex: `rspec --fail-fast`
- You can also add the line you want to run from the RSPEC file so it will run only that  
Ex: `rspec ./spec/contact_spec.rb:18`
