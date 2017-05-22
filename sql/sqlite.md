To make sqlite more readable, paste this to terminal:  
```
cat << EOF > ~/.sqliterc
.headers on
.mode column
EOF
```
`$ sqlite3 database.db` - Open file 
#### In SQLite3
`.tables` - Show Tables  
`.schema` - Show table schemas  
#### Editing Tables
Rename table:  
`ALTER TABLE name RENAME TO newname;`     
Add column to existing table:  
`ALTER TABLE Persons ADD NickName varchar(255);`  
Update data in exisiting table:  
`
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
WHERE CustomerID = 1;
`  
