To make sqlite more readable, paste this to terminal:  
```
cat << EOF > ~/.sqliterc
.headers on
.mode column
EOF
```
`$ sqlite3 database.db` - Open file  
