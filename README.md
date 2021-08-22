# Movie-theatres
![img](https://upload.wikimedia.org/wikipedia/commons/f/ff/Sql_movie_theaters.png)

## Table creation code
```SQL CREATE TABLE Movies (
   Code INTEGER PRIMARY KEY NOT NULL,
   Title TEXT NOT NULL,
   Rating TEXT 
 );
  
 CREATE TABLE MovieTheaters (
   Code INTEGER PRIMARY KEY NOT NULL,
   Name TEXT NOT NULL,
   Movie INTEGER  
     CONSTRAINT fk_Movies_Code REFERENCES Movies(Code)
 );
```

 ## Exercises
 1. Select the title of all movies.
 
  ```SQL SELECT Title FROM Movies;```
 2. Show all the distinct ratings in the database.
 
 ```SQL SELECT DISTINCT Rating FROM Movies; ```
 3. Show all unrated movies.
 
 ```SQL SELECT * FROM Movies WHERE Rating IS NULL; ```
 4. Select all movie theaters that are not currently showing a movie.
 
 ```SQL SELECT * FROM MovieTheaters WHERE Movie IS NULL; ```
 5. Select all data from all movie theaters and, additionally, the data from the movie that is being shown in the theater (if one is being shown).
 
 ```SQL SELECT * FROM MovieTheaters LEFT OUTER JOIN Movies M on MovieTheaters.Movie = M.Code;```
 6. Select all data from all movies and, if that movie is being shown in a theater, show the data from the theater.
 ```SQL SELECT * FROM MovieTheaters RIGHT OUTER JOIN Movies M on MovieTheaters.Movie = M.Code;```
 7. Show the titles of movies not currently being shown in any theaters.
 ```SQL SELECT Title FROM MovieTheaters RIGHT OUTER JOIN Movies M on M.Code = MovieTheaters.Movie WHERE Movie IS NULL;```
 8. Add the unrated movie "One, Two, Three"
 ```SQL INSERT INTO Movies(Code, Title, Rating) VALUES (10 , 'One Two Three', NULL);```
 9. Set the rating of all unrated movies to "G"
 ```SQL UPDATE Movies SET Rating='G' WHERE Rating IS NULL;```
 10. Remove movie theaters projecting movies rated "NC-17".
 ```SQL DELETE FROM MovieTheaters WHERE Movie IN (SELECT Code FROM Movies WHERE Rating = 'NC-17');```
