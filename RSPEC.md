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
