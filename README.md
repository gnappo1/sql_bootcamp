#### Coding challenge

- use downloaded database: chinook.db

## Challenges

1. Write the SQL to return all of the rows in the artists table?

```SQL
SELECT * FROM artists;
```

2. Write the SQL to select the artist with the name "Black Sabbath"

```SQL
SELECT * FROM artists WHERE name = "Black Sabbath";
```

3. Write the SQL to create a table named 'fans' with an autoincrementing ID that's a primary key and a name field of type text

```sql
CREATE TABLE fans (id INTEGER PRIMARY KEY, name TEXT);
```

4. Write the SQL to alter the fans table to have a artist_id column type integer?

```sql
ALTER TABLE fans ADD column artist_id INTEGER;
```

5. Write the SQL to add yourself as a fan of the Postal Service? ArtistId **174**

```sql
INSERT INTO fans (name, artist_id) VALUES ("Matteo", 174)
```

6. Write the SQL to return fans that are not fans of the black eyed peas.

```sql
SELECT * FROM fans WHERE artist_id != 169;
```

7. Write the SQL to display an artists name next to their album title

```sql
SELECT artists.name, albums.title 
FROM artists 
INNER JOIN albums 
ON artists.id = albums.artist_id;
```

8. Write the SQL to display artist name, album name and number of tracks on that album

```sql
SELECT artists.name, albums.title, count(tracks.album_id)
FROM artists 
INNER JOIN albums ON artists.id = albums.artist_id
INNER JOIN tracks ON tracks.album_id = albums.id
GROUP BY album_id;
```

9. Write the SQL to return the name of all of the artists in the 'Pop' Genre

```sql
SELECT artists.name
FROM artists 
INNER JOIN albums ON artists.id = albums.artist_id
INNER JOIN tracks ON tracks.album_id = albums.id
WHERE tracks.genre_id = 9
GROUP BY tracks.album_id;
```

## BONUS (very hard)

10. I want to return the names of the artists and their number of rock tracks
    who play Rock music
    and have more than 30 tracks
    in order of the number of rock tracks that they have
    from greatest to least

```sql
SELECT artists.name, COUNT(tracks.genre_id)
FROM artists
INNER JOIN albums ON artists.id = albums.artist_id
INNER JOIN tracks ON tracks.album_id = albums.id
WHERE tracks.genre_id = 1
GROUP BY artists.id
HAVING COUNT(tracks.genre_id > 30)
ORDER BY COUNT(tracks.genre_id) DESC;
```