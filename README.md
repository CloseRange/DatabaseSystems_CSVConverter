# Olympic Countries SQL

## Changes made from assignment 1
* I removed the `City` table fully and just added the `city` column to OlympicGame.
    Redundant to have a whole table for city when its only ever used in the one table and has one row.
* The `Event` table became `SportEvent` due to Event being a reserved keyword
* Tables are now CamelCase instead of Snake_Case
* Had to add `is_winter` as a primary key for OlympicGame's and a foreign key for the `Competitor` table.
    I didn't realize it was possible for a summer and winter olympic to happen the same year.

## Importing From CVS File
Due to the fact that this is a database class and not a programming class
I wrote a very bare bones converter in JavaScript. Nothing fancy and no comments.

To use or see the program visit the [Github Page](https://github.com/CloseRange/DatabaseSystems_CSVConverter) and open the `index.html` file.

### Usage

1. Drag and drop the country.csv file into the first box
2. Then the main_data_set_csv file into the second box.
3. This will auto download 5 .sql files (one for each table)
4. Compress these files by hand (maintaining the .sql.zip extension)
    * Ensure the `Competitor` database is last
5. Import them to the database

NOTE: I ended up splitting the `Competitor` file into 2 zip files because it didn't want to add every row in one go. Using a single INSERT statement over thousands of small ones might have fixed it, but this just was easier for me to work with.


## Basics on how code works
I used chatgpt to get a basic html layout then In JavaScript I wrote the converter.

1. The program iterates over each row adding to a finalized string full of 'INSERT' statements
2. For each row split on the comma delimiter.
3. For each row, add a `INSERT` statement for each event/person/game/country/competitor
    * NOTE: The program keeps an bare bones internal map of each table, if the column already exists (for example a person is mentioned more than once) then we can skip that particular insert
4. Translate each inserted `INSERT` into one big string.
5. Prgram seperates all the relavant INSERT statements into their respective files (such as `Person` data into its own file)
    * NOTE: whiel I could have had them all in one big file, this helped me to debug where my code was not working properly. I also had issues importing big files where most of the data would be imported but not the rest, this helped with that issue.
6. Download the text files
