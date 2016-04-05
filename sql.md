
Help full link
--------------

http://www.cheat-sheets.org/sites/sql.su/


CREATE (schema.sql)
---------------------
DROP TABLE IF EXISTS comments;
DROP TABLE IF EXISTS movies;
DROP TABLE IF EXISTS categories;

CREATE TABLE songs(
 id SERIAL PRIMARY KEY,
 track_number INTEGER,
 artist VARCHAR(255),
 album VARCHAR(255),
 title VARCHAR(255) NOT NULL,
 year INTEGER,
 length_in_seconds INTEGER,
 created_at TIMESTAMP,
 updated_at TIMESTAMP
);


SELECT SQL:
SELECT * FROM table_name;

SELECT columns FROM table_name
WHERE conditional;

SELECT title, year FROM movies
WHERE year = 1977;

SELECT title, rating FROM movies
WHERE rating > 90;

SELECT title, rating FROM movies
ORDER BY rating DESC
LIMIT 10;

[8:20]
INSERT SQL:

INSERT INTO categories (name)
VALUES
 ('Action'),
 ('Comedy'),
 ('Drama'),
 ('Horror'),
 ('Sci-Fi'),
 ('Mystery'),
 ('Fantasy'),
 ('Animation’);

INSERT INTO movies (title, year, category_id)
VALUES
 ('Donnie Darko', '2001', (SELECT id FROM categories WHERE name='Mystery')),
 ('Army of Darkness', '1992', (SELECT id FROM categories where name='Fantasy')),
 ('Dumbo', '1941', (SELECT id FROM categories WHERE name = 'Animation')),
 ('Lion King', '1994', (SELECT id FROM categories WHERE name = 'Animation')),
 ('Evolution', '2001', (SELECT id FROM categories WHERE name='Comedy')),
 ('Young Frankenstein', '1974', (SELECT id FROM categories where name='Comedy')),
 ('Fifth Element', '1997', (SELECT id FROM categories WHERE name = 'Sci-Fi')),
 ('Die Hard', '1988', (SELECT id FROM categories WHERE name = 'Action')),
 ('Ex Machina', '2015', (SELECT id FROM categories WHERE name = 'Sci-Fi'));


UPDATE SQL:

UPDATE songs
SET artist = 'Aphex Twin', updated_at = NOW()
WHERE artist = 'aphex twin';
