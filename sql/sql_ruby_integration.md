[PREP: Object Relational Mapping](https://github.com/sf-sea-lions-2017/phase-1-guide/blob/sf/readings/object-relational-mapping/README.md)

### ON RUBY
```ruby
require 'sqlite3'

$db = SQLite3::Database.new("database.db")   
$db.results_as_hash = true   # $ -> Global Variable

```
