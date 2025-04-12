# Olympic Countries SQL
## Changes made from assignment 1
I removed the 'City' table fully and just added the 'city' column to OlympicGame.

I know this is a big change but it was very reductive to add a whole table for city names when it wasn't needed.
Collating into 1 table is a much better choice

## Importing From CVS File
Due to the fact that this is a database class and not a programming class
I wrote a very bare bones converter in JavaScript. Nothing fancy.

To use or see the program visit the [Github](https://github.com/CloseRange/DatabaseSystems_CSVConverter) and open the html file

1. Drag and drop the country.csv file into the first box
2. Then the main_data_set_csv file into the second box.
3. This will auto download the .sql file
4. Compress this files by hand (maintaining the .sql.zip extension)
5. Import to the database


## Basics on how code works
I used chatgpt to get a basic html layout then In java I wrote the converter.

1. The program iterates over each row adding to a finalized string full of 'INSERT' statements
2. For each row split on the comma delimiter.
3. For each row, add a `INSERT` statement for each event/person/game/country/competitor
3. * NOTE: The program keeps an bare bones internal map of each table,
if the column already exists (for example a person is mentioned more than once) then we can skip that particular insert
4. Translate each inserted 'INSERT' into one big string.
5. Download the text file