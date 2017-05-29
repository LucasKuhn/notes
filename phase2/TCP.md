# TCP
## BASICS
Ftp stands for File Transfer Protocol.
The IP address is used to reach the server, and the PORT tells which path on the system I want to access.
IP is like the street address and the PORT is like the Apartment Number.
The DNS (Domain Name Servers) is the one responsible for translating "google.com" into an IP address to one
of the google machines.

## TCP
The TCP (Transmission Control Protocol) is how two machines connect with each other, sending and recieving data.  
The Server
```ruby 
require 'socket'
server = TCPServer.new(2000)

#keep the server running
loop do   
  client = server.accept #connect to a client
  
  message = client.gets.chomp #recieve a message
  
  client.puts("This is my answer!") #sent a message to a client
  
  client.close #close the client connection
end 
```
The Client
```ruby 
require 'socket'

# Connect to a server
server_connection = TCPSocket.new('127.0.0.1',2000)

message = ARGV.join(" ") # Get a message from console for testing

server_connection.puts(message) #send message to server

response = server_connection.gets # Get response from server
```
