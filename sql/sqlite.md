
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
#### BASICS  
```sql
# RENAME TABLE
ALTER TABLE tblname 
RENAME TO newtblname;

# ADD TO EXISTING TABLE
ALTER TABLE Persons 
ADD NickName varchar(255);

# UPDATA DATA IN EXISTING TABLE
UPDATE tblname 
SET Name = 'Alfred' 
WHERE id = 1;
```

### Add-Ons
Paste this to make tables more readable:  
```
cat << EOF > ~/.sqliterc
.headers on
.mode column
EOF
```

Writing to DB files examples : [Phase 0 Puppy Maker](https://github.com/LucasKuhn/phase-0-tracks/blob/master/databases/puppy_maker/puppy_maker.rb)

