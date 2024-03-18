# SQL-database

SQL, which stands for Structured Query Language, is a powerful tool for managing and manipulating databases. It's used to interact with relational databases, which store data in tables that can relate to each other through common fields. 
First step is Creating a Table
Example: 
-- Create locations table
CREATE TABLE locations (
    city_id INT PRIMARY KEY,
    city VARCHAR(50),
    country VARCHAR(50)   
);

Explanation: 
CREATE TABLE locations: This tells the database to create a new table with the name locations.
Inside the parentheses, you define the columns of the table and their data types:
city_id INT PRIMARY KEY: This defines a column named city_id that stores integer values. It's designated as the PRIMARY KEY, meaning each value in this column must be unique and not null. This uniqueness ensures that each row (each location) can be uniquely identified by its city_id.
city VARCHAR(50): This defines a column named city that stores string values (text), with a maximum length of 50 characters.
country VARCHAR(50): Similarly, this defines a country column for storing the country name, also with a maximum length of 50 characters.

Second step is to define Foreign Keys and Altering Tables
Why Foreign Keys: A foreign key is a column or a set of columns used to establish a link between the data in two tables. 
Example: -- Add foreign key to shops table
ALTER TABLE shops
ADD FOREIGN KEY (city_id)
REFERENCES locations(city_id)
ON DELETE SET NULL;
Explanation: ALTER TABLE shops: This command is used to make changes to the structure of an existing table, in this case, shops.
ADD FOREIGN KEY (city_id): This adds a new foreign key to the shops table. The foreign key is based on the city_id column, implying that shops also has a column named city_id that will link to the city_id in the locations table.
REFERENCES locations(city_id): This specifies that the foreign key in the shops table references the city_id column in the locations table. It establishes the relationship between the two tables.
ON DELETE SET NULL: This part of the command specifies what should happen to the foreign key value in shops if the corresponding city_id in locations is deleted. In this case, it sets the city_id in shops to NULL, effectively breaking the link but not deleting the record.
