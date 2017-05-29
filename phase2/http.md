Read-Time : 2 minutes

# HTTP
**HTTP**  stands for HyperText Transfer Protocol. It is a stateless application protocol, used to exchange or transfer hypertext. It is called a stateless protocol because each command is executed independently, without any knowledge of the commands that came before it.

# REQUEST
A **REQUEST** contains a **Method** and a **URL**  
You can check a request on your browser by opening the console > network (let filter be All and add the tag 'Method').
Once you click a GET request it will display 3 tabs: `General`, `Response Headers` and
`Request Headers`. 
Open the `Request Header`:  

There are a few things we can check there:

- On Accept it displays what the request wants the server to return.
- On User-Agent it displays info about what the user is using.

Now toggle the button `view source`. Using Google as an example, the first lines look like this:  
```
GET / HTTP/1.1
Host: google.com
```
This is our **REQUEST HEADER**.  

## REQUEST HEADER
HTTP_METHOD /route 

## VERBS / METHODS
These describe the action that should be performed on the host. They are fomalized and universally applicable:  

- **GET:** fetch an existing resource. The URL contains all the necessary information the server needs to locate and return the resource.  
- **POST:** create a new resource. POST requests usually carry a payload that specifies the data for the new resource.  
- **PUT:** update an existing resource. The payload may contain the updated data for the resource. (Also, PATCH)  
- **DELETE:** delete an existing resource.  

## URL
![URL Layout](https://github.com/LucasKuhn/notes/blob/master/phase2/images/http1-url-structure.png)  
<p align="center">Uniform Resource Locator</p>
 - The default port is 80  
 
### URI gem  
Try it on pry/irb ^^  
```ruby 
require 'uri'
url = URI('http://devbootcamp.com/')
url.scheme
url.hostname
url.port
url.path
url.query
```

# RESPONSE

## STATUS CODES
- **1xx:** Informational Messages
- **2xx:** Successful
- **3xx:** Redirection
- **4xx:** Client Error
- **5xx:** Server Error  
[HTTP Statuses](https://httpstatuses.com/)  

# RESOURCES 
[Text Source](https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)  
[Video Source](https://talks.devbootcamp.com/intro-to-http)  

