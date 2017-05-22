SELECT * FROM employees ORDER BY hire_date DESC;
SELECT hire_date, first_name, last_name  FROM employees WHERE hire_date < '2011-02-15'
SELECT * FROM employees WHERE first_name LIKE 'A%'


SELECT * FROM invoices 
WHERE billing_state = 'NV' 
AND billing_city = 'Reno'
AND total > 5.00

SELECT * FROM tracks 
WHERE composer IS NULL

SELECT * FROM invoices
WHERE billing_country = 'Germany'
ORDER BY total DESC LIMIT 10

SELECT COUNT (*) FROM invoices
WHERE billing_city = 'Santiago'

SELECT country, COUNT (id) FROM customers GROUP BY country

SELECT name FROM artists WHERE name LIKE '%smith%'

31 - 
SELECT city, COUNT (id) 
FROM employees
GROUP BY city

32 - 
SELECT country, COUNT (id) 
FROM customers
GROUP BY country
ORDER BY COUNT DESC
LIMIT 3

34 - 
SELECT artists.name, albums.title
FROM artists JOIN albums
ON artists.id = albums.artist_id

36 - 
SELECT  artists.name, albums.title
FROM albums JOIN artists
ON albums.artist_id = artists.id
ORDER BY artists.name ASC

37 - 
SELECT customers.first_name, 
customers.last_name, 
invoices.total
FROM customers, invoices
WHERE customers.id = invoices.customer_id
ORDER BY total DESC

38 - 
SELECT *
FROM customers, invoices
WHERE customers.id = invoices.customer_id
ORDER BY total DESC
LIMIT 1

41 - 
SELECT *
FROM albums, tracks
WHERE tracks.album_id = albums.id 
AND tracks.name = 'Midnight'

42 - 
SELECT artists.name
FROM albums, tracks, artists
WHERE artists.id = albums.artist_id
AND tracks.album_id = albums.id 
AND tracks.name = 'Midnight'

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
