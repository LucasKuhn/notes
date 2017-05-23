
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
#### JOIN / GROUP BY / COUNT
```sql
# DISPLAY CITY AND HOW MANY PEOPLE LIVE IN THAT CITY 
SELECT city, COUNT (id) 
FROM people
GROUP BY city

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

Writing to DB files examples : [Phase 0 Puppy Maker](https://github.com/LucasKuhn/phase-0-tracks/blob/master/databases/puppy_maker/puppy_maker.rb)

