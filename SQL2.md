#  List of SQL commands

<!-- toc orderedList:0 depthFrom:1 depthTo:6 -->

* [List of SQL commands](#list-of-sql-commands)
* [Manipulation](#manipulation)
  * [sql](#sql)
  * [statements](#statements)
  * [create](#create)
  * [insert](#insert)
  * [select](#select)
  * [update](#update)
  * [alter](#alter)
  * [delete](#delete)
* [Queries](#queries)
  * [query](#query)
  * [select](#select-1)
  * [distinct](#distinct)
  * [where](#where)
  * [like-i](#like-i)
  * [like-ii](#like-ii)
  * [between](#between)
  * [and](#and)
  * [or](#or)
  * [order-by](#order-by)
  * [limit](#limit)
* [Aggregate Functions](#aggregate-functions)
  * [count](#count)
  * [sum](#sum)
  * [max](#max)
  * [min](#min)
  * [avg](#avg)
  * [round](#round)
  * [round](#round-1)
* [Multiple Tables](#multiple-tables)
  * [multi-table](#multi-table)
  * [primary-key](#primary-key)
  * [foreign-key](#foreign-key)
  * [cross-join](#cross-join)
  * [inner-join](#inner-join)
  * [left-outer-join](#left-outer-join)
  * [aliases](#aliases)

<!-- tocstop -->

# Manipulation
## sql
```sql
SELECT * FROM celebs;
```
## statements
```sql
CREATE TABLE celebs (id INTEGER, name TEXT, age INTEGER);
```
## create
```sql
INSERT INTO celebs (id, name, age) VALUES (1, 'Justin Bieber', 21);
SELECT * FROM celebs;
```

## insert
```sql
INSERT INTO celebs (id, name, age) VALUES (2, 'Beyonce Knowles', 33);

INSERT INTO celebs (id, name, age) VALUES (3, 'Jeremy Lin', 26);

INSERT INTO celebs (id, name, age) VALUES (4, 'Taylor Swift', 26);

SELECT name FROM celebs;
```
## select
```sql
UPDATE celebs
SET age = 22
WHERE id = 1;

SELECT * FROM celebs;
```

## update
```sql
ALTER TABLE celebs ADD COLUMN twitter_handle TEXT;

SELECT * FROM celebs;
```
## alter
```sql
UPDATE celebs
SET twitter_handle = '@taylorswift13'
WHERE id = 4;


DELETE FROM celebs
WHERE twitter_handle IS NULL;

SELECT * FROM celebs;

```

## delete
```sql
DELETE FROM celebs WHERE twitter_handle IS NULL;
```

# Queries
## query
```sql
SELECT name, imdb_rating FROM movies;
```
## select
```sql
SELECT DISTINCT genre FROM movies;
```

## distinct
```sql
SELECT * FROM movies WHERE imdb_rating > 8;
```
## where
```sql
SELECT * FROM movies
WHERE name LIKE 'Se_en';
```
## like-i
```sql
SELECT * FROM movies
WHERE name LIKE '%man%';
```

## like-ii
```sql
SELECT * FROM movies
WHERE year BETWEEN 1990 AND 2000;
```
## between
```sql
SELECT * FROM movies
WHERE year BETWEEN 1990 AND 2000
AND genre = 'comedy';
```

## and
```sql
SELECT * FROM movies
WHERE genre = 'comedy'
OR year < 1980;
```

## or
```sql
SELECT * FROM movies
ORDER BY imdb_rating DESC;
```

## order-by
```sql
SELECT * FROM movies
ORDER BY imdb_rating ASC
LIMIT 3;
```

## limit
```sql
SELECT * FROM movies
ORDER BY imdb_rating DESC
LIMIT 3;
```

# Aggregate Functions
## count
```sql
SELECT COUNT(*) FROM fake_apps;
```
## sum
```sql
SELECT price, COUNT(*) FROM fake_apps
GROUP BY price;
```
## max
```sql
SELECT MAX(downloads) FROM fake_apps;
```

## min
```sql
SELECT MIN(downloads) FROM fake_apps;
```
## avg
```sql
SELECT AVG(downloads) FROM fake_apps;
```

## round
```sql
SELECT price, ROUND(AVG(downloads), 2) FROM fake_apps
GROUP BY price;
```

## round
```sql
SELECT price, ROUND(AVG(downloads)) FROM fake_apps
GROUP BY price;
```

# Multiple Tables
## multi-table
```sql
CREATE TABLE artists(id INTEGER PRIMARY KEY, name TEXT);
```
## primary-key
```sql
SELECT * FROM artists WHERE id = 3;
SELECT * FROM albums WHERE artist_id = 3;
```
## foreign-key
```sql
SELECT albums.name, albums.year, artists.name FROM albums, artists;
```

## cross-join
```sql
SELECT
  *
FROM
  albums
JOIN artists ON
  albums.artist_id = artists.id;
```

## inner-join
```sql
SELECT
  *
FROM
  albums
LEFT JOIN artists ON
  albums.artist_id = artists.id;
```

## left-outer-join
```sql
SELECT
  albums.name AS 'Album',
  albums.year,
  artists.name AS 'Artist'
FROM
  albums
JOIN artists ON
  albums.artist_id = artists.id
WHERE
  albums.year > 1980;
```

## aliases
```sql
SELECT
  albums.name AS 'Album',
  albums.year,
  artists.name AS 'Artist'
FROM
  albums
JOIN artists ON
  albums.artist_id = artists.id
WHERE
  albums.year > 1980;
```
