
To open File: 
`$ sqlite3 database.db` 
### USEFUL COMMANDS
```sql
.tables #Show Tables
.schema #Show Schema
```

### CREATING TABLE 
```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  first_name VARCHAR(64) NOT NULL,
  last_name  VARCHAR(64) NOT NULL,
  email VARCHAR(128) UNIQUE NOT NULL,
  created_at DATETIME NOT NULL,
  updated_at DATETIME NOT NULL
);  /* Don't forget the semicolon */
```
### POPULATING TABLE
```sql
INSERT INTO users
(first_name, last_name, email, created_at, updated_at)
VALUES
('Kevin', 'Solorio', 'kevin@devbootcamp.com', DATETIME('now'), DATETIME('now')),
('Alyssa', 'Diaz', 'alyssa@devbootcamp.com', DATETIME('now'), DATETIME('now'));
```

### EDITING TABLES
#### SELECT / ORDER BY
```sql
# SELECT ALL
SELECT * FROM tblname;

# SELECT ESPECIFIC 
SELECT first_name FROM tblname;

# SELECT IN ORDER 
SELECT * FROM tblname 
ORDER BY firs_name DESC; #ASC by default
```
#### ALTER / UPDATE
```sql
# ALTER TABLE NAME
ALTER TABLE tblname 
RENAME TO newtblname;

# ADD ROW TO EXISTING TABLE
ALTER TABLE Persons 
ADD NickName varchar(255);

# UPDATA DATA IN EXISTING TABLE
UPDATE tblname 
SET Name = 'Alfred' 
WHERE id = 1;
```
#### WHERE / LIKE
```sql
# SELECTING WHEN CONDITIONS ARE MET (ANDs ARE OPTIONAL)
SELECT * FROM invoices 
WHERE billing_state = 'NV' 
AND billing_city = 'Reno'
AND total > 5.00

# WHEN A CONDITION IS LIKE A CERTAIN PATTERN
SELECT * FROM employees 
WHERE first_name LIKE 'A%' 
# 'A%' => Starts with A 
# '%A' => Ends with A
# '%A%' => Has A somewhere in the string 
```
#### COUNT / AVG / SUM
```sql
# COUNT CREATED A ROW AND COUNT THINGS THAT MATCHES THE CRITERIA
SELECT COUNT(column_name)
FROM table_name
WHERE condition;

# SUM ADDS ALL NUMERIC VALUES THAT MATCHES CRITERIA
SELECT SUM(column_name)
FROM table_name
WHERE condition;

# AVG SUMS AND GIVE THE AVERAGE OF THE ELEMENTS MATCHED
SELECT AVG(column_name)
FROM table_name
WHERE condition;

# DISPLAY CITY AND HOW MANY PEOPLE LIVE IN THAT CITY 
SELECT city, COUNT (id) 
FROM people
GROUP BY city
```
#### JOIN / GROUP BY 
```sql
# JOIN 
SELECT artists.name, albums.title
FROM artists JOIN albums
ON artists.id = albums.artist_id

# ALIAS FOR JOIN
SELECT artists.name, albums.title
FROM artists, albums
WHERE artists.id = albums.artist_id

# MULTIPLE JOIN
SELECT *
FROM albums, tracks, artists
WHERE artists.id = albums.artist_id
AND tracks.album_id = albums.id 
AND tracks.name = 'Midnight'


```

### ADD-ONS
Paste this to make tables more readable:  
```
cat << EOF > ~/.sqliterc
.headers on
.mode column
EOF
```
A prettier way to display schema than .schema
```sql
$ sqlite3 db/database.sqlite3

sqlite> PRAGMA table_info(dogs);
```

### FROM SQL TUTOR - NOT EDITED YET
43 - 
SELECT COUNT (albums.id)
FROM albums, artists
WHERE artists.id = albums.artist_id
AND artists.name = 'Iron Maiden'

44 -
SELECT artists.name, COUNT (albums.id)
FROM albums, artists
WHERE artists.id = albums.artist_id
GROUP BY artists.name 
ORDER BY artists.name ASC

45 -   
SELECT albums.title, COUNT (tracks.id)  
FROM albums, tracks  
WHERE tracks.album_id = albums.id  
GROUP BY albums.title   
ORDER BY COUNT DESC, albums.title ASC  

47 - 
SELECT albums.*,
COUNT (tracks.id)
FROM tracks JOIN albums
ON albums.id = tracks.album_id
GROUP BY albums.id
ORDER BY COUNT DESC

48 - 
SELECT customers.first_name, 
customers.last_name, 
SUM(invoices.total)
FROM customers, invoices
WHERE customers.id = invoices.customer_id
GROUP BY customers.id
ORDER BY SUM DESC
LIMIT 5

50 -
SELECT albums.*, COUNT(tracks.id)
FROM albums, tracks
WHERE albums.id = tracks.album_id
GROUP BY albums.id
ORDER BY COUNT DESC

51 - 
SELECT artists.*, COUNT(albums.id)
FROM albums, artists
WHERE albums.artist_id = artists.id
GROUP BY artists.id
ORDER BY COUNT DESC, artists.name
