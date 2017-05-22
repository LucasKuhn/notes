### In The Terminal 
Paste this to make tables more readable:  
```
cat << EOF > ~/.sqliterc
.headers on
.mode column
EOF
```
To open File: 
`$ sqlite3 database.db` 
### In SQLITE3 

#### Useful Commands
`.tables` - Show Tables  
`.schema` - Show table schemas  

#### Creating Table 
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
#### Populating Table
```sql
INSERT INTO users
(first_name, last_name, email, created_at, updated_at)
VALUES
('Kevin', 'Solorio', 'kevin@devbootcamp.com', DATETIME('now'), DATETIME('now')),
('Alyssa', 'Diaz', 'alyssa@devbootcamp.com', DATETIME('now'), DATETIME('now'));
```

#### Editing Tables
**Renaming Table**: `ALTER TABLE tblname RENAME TO newtblname;`     
**Add column to existing table:** `ALTER TABLE Persons ADD NickName varchar(255);`  
**Update data in exisiting table:**  `UPDATE tblname SET Name = 'Alfred' WHERE id = 1;`  
