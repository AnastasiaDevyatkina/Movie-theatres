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
 3. Show all the distinct ratings in the database.
 ```SQL SELECT DISTINCT Rating FROM Movies; ```
