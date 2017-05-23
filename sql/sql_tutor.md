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
