

### Inheritance:
When something IS A other thing, it would be a good idea to make one inherit the other.
Thing on the left IS A thing on the right

Ex: 
A Human is a Mammal, so it could inherit from Mammal things he have as a default
EX: Breathing, sleeping, blablabla

Inheritance is NOT for sharing code, but to moddel some kind of system.

Module is a "bag of behavior"
They don't usually include 'initialize' 
module Bookable
  def book_appointment(person,time)
  @calendar.book
end

require_relative 'bookable'
Class Therapist 
  include Bookable
end

Class HealthProfessional
  include Bookable
  
  def initialize
    @calendar = Calendar.new
  end
end

Class Therapist
  def listen
    puts "Tell me more..."
  end 
end 

Class Dentist
  def perform_root_canal
    puts "Don't move..."
  end 
end 

Premature Optimization is the root of ***ALL EVIL!***   
You don't know what it coming in the future XD
