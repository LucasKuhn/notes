[Text Source](https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)  
[Video Source](https://talks.devbootcamp.com/intro-to-http)  

# HTTP
- **HTTP** HyperText Transfer Protocol  
- It is a stateless protocol   

## REQUESTS
A **REQUEST** contains a *Method* and a *URL*  
You can check a request by opening the console > network , let filter be All and add the tag 'Method'. Once you click a GET request it will display the Request Header with all the info send, and Responde Header with all the server returned.
### REQUEST HEADER
On Accept is displays what the request wants the server to return.
On User-Agent it displays info about what the user is using.




## VERBS / METHODS
These describe the action that should be performed on the host. They are fomalized and universally applicable:  

- **GET:** fetch an existing resource. The URL contains all the necessary information the server needs to locate and return the resource.  
- **POST:** create a new resource. POST requests usually carry a payload that specifies the data for the new resource.  
- **PUT:** update an existing resource. The payload may contain the updated data for the resource. (Also, PATCH)  
- **DELETE:** delete an existing resource.  

## URL
![xomething jhere](https://github.com/LucasKuhn/notes/blob/master/phase2/images/http1-url-structure.png)  
<p align="center">Uniform Resource Locator</p>
 - The default port is 80  
 
### URI gem  
```ruby 
require 'uri'
url = URI('http://devbootcamp.com/')
url.scheme
url.hostname
url.port
url.path
url.query
```
## HEADER

## BODY

## STATUS CODES
- **1xx:** Informational Messages
- **2xx:** Successful
- **3xx:** Redirection
- **4xx:** Client Error
- **5xx:** Server Error
