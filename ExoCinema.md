# Exercise: Designing a Movie Database

## Conceptual Modeling

1. **Identify Entities:**
   - Movie
   - Actor
   - Director
   - Genre
   - Studio
   - Review

2. **Define Attributes:**
   - Movie: Title, Release Date, Duration
   - Actor: Name, Birthdate, Nationality
   - Director: Name, Birthdate, Nationality
   - Genre: Label
   - Studio: Name, Location
   - Review: Title, Content, Date, Rating

3. **Establish Relationships:**
   - Actors can be in multiple movies; movies can have multiple actors.
   - Each movie has one director; directors can direct multiple movies.
   - A movie can belong to multiple genres; a genre can have multiple movies.
   - Each movie is produced by one studio; a studio can produce multiple movies.
   - Each movie is reviewed once at most

4. **Specify Cardinality and Participation:**
   - (0..n) - (0..n), many to many, both side optional
   - (1) - (0..n), one to many, mandatory on one side
   - (1) - (0..1), one to one, optional on one side
   - (1) - (1), one to one, mandatory

## Logical Modeling

1. **Refine Entities:**
   - Identify primary keys for each entity

2. **Resolve Many-to-Many Relationships:**
   - Introduce associative tables for Movie-Actor and Movie-Genre relationships.

3. **Specify Foreign Keys:**
   - Movie-Actor: MovieID (foreign key referencing Movie), ActorID (foreign key referencing Actor)
   - Movie-Genre: MovieID (foreign key referencing Movie), GenreID (foreign key referencing Genre)

4. **Specify Attributes:**
   - Add necessary attributes like MovieBudget, ActorRole, and StudioRevenue.

## Implementation Modeling

1. **Choose Data Types:**
   - MovieID, ActorID, DirectorID, GenreID, StudioID: INTEGER
   - Title, Name, Type: VARCHAR
   - ReleaseDate, Birthdate: DATE
   - Duration: TIME
   - Rating, Budget, Revenue: DECIMAL

2. **Apply Constraints:**
   - Set constraints for NOT NULL, UNIQUE, and DEFAULT values where appropriate.

3. **Create Tables:**
   
4. **Establish Relationships with Foreign Keys:**
   - Set up foreign key relationships based on the previously defined logical model.

