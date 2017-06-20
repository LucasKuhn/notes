
# Behavior Driven Development
`describe` => `scenario`

### Controller
Takes care of routing, setting variables, and redirecting.

The controller test doesn't care what the template has in it, that's the views concern.

### RSPEC
google `rspec rails` and put the thing in your gemfile then `bundle`
then run the `rails generate` from the rspec rails guide

### Capybara
get the `gem` in the `gemfile`
add `require capybara/rails` to `rails helper`
require `rails_helper` in rspec

### Testing
Outside in! `features` => `controller` => `unit(models)`
Rspec folder `features` file `homepage_spec.rb`
run `be rspec`
`models/spec_helper.rb`
