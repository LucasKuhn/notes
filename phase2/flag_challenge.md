nc -c hsh.dbcapps.com 80
GET /levels/one HTTP/1.1
Host: hsh.dbcapps.com

GET /levels/2 HTTP/1.1
Host: hsh.dbcapps.com

GET /levels/iii?secret=HellaTameableTransferProtocol HTTP/1.1
Host: hsh.dbcapps.com


GET /levels/quatro HTTP/1.1
Host: hsh.dbcapps.com

GET /levels/onwards HTTP/1.1
Host: hsh.dbcapps.com

GET /levels/00000110 HTTP/1.1
Host: hsh.dbcapps.com

nc -c hsh.dbcapps.com 80
POST /users HTTP/1.1
Host: hsh.dbcapps.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 32

username=Skywalker&password=yoda
-----------
nc -c hsh.dbcapps.com 80
POST /users/login HTTP/1.1
Host: hsh.dbcapps.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 32

username=Skywalker&password=yoda
------------
GET /users/profile HTTP/1.1
Host: hsh.dbcapps.com
Cookie: user_id=292
------------
POST /flags HTTP/1.1
Host: hsh.dbcapps.com
Cookie: user_id=292
------------
GET /flags HTTP/1.1
Host: hsh.dbcapps.com
Cookie: user_id=292

