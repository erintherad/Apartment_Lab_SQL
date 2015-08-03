1.  Show all the psql users. (Hint: Look for a command to show roles)

\dg[+]  [PATTERN]

2.  Show all the tables in your apartmentlab database.

\dt

3.  Show all the data in the owners table.

\d owners

4.  Add three owners: Donald (age 56), Elaine (age 24), and Emma (age 36).

INSERT INTO owners (name, age)
  VALUES ('Donald', 56);

INSERT INTO owners (name, age)
VALUES ('Elaine', 24);

INSERT INTO owners (name, age)
VALUES ('Emma', 36);


5.  Show the names of all owners.

SELECT name FROM owners;


6.  Show the ages of all of the owners in ascending order.

SELECT name FROM owners ORDER BY age ASC;


7.  Show the name of an owner whose name is Donald.

SELECT name FROM owners
	WHERE name = 'Donald';


8.  Show the age of all owners who are older than 30.


SELECT age FROM owners
	WHERE age > 31;


9.  Show the name of all owners whose name starts with an "E".

SELECT name FROM owners
	WHERE name LIKE 'E%';


10.  Add an owner named John who is 33 years old.

INSERT INTO owners (name, age)
	VALUES ('John', 33);


11.  Add an owner named Jane who is 43 years old.

INSERT INTO owners (name, age)
	VALUES ('Jane', 43);


12.  Change Jane's age to 30.

UPDATE owners
	SET age = 30
	WHERE age = 43;


13.  Change Jane's name to Janet.

UPDATE owners
	SET name = 'Janet'
	WHERE name = 'Jane';


14.  Delete the owner named Janet.

DELETE FROM owners
	WHERE name = 'Janet'
	RETURNING *;


15.  Add a property named Archstone that has 20 units.

INSERT INTO properties (name, num_units)
	VALUES ('Archstone', 20);


16.  Add two more properties with names and number of units of your choice.

INSERT INTO properties (name, num_units)
	VALUES ('Generic_Apts', 10);

INSERT INTO properties (name, num_units)
	VALUES ('Hobo Livin', 30);	


17.  Show all of the properties in alphabetical order that are not named Archstone.

SELECT name FROM properties
	WHERE name <> 'Archstone'
	ORDER BY name ASC;



18.  Count the total number of rows in the properties table.

SELECT * FROM properties;
3


19.   Show the highest age of all the owners.

SELECT * FROM owners;
56


20.  Show the names of the first three owners in your owners table.

Donald, Elaine, Emma


21.  Use a FULL OUTER JOIN to show all of the information from the owners table and the properties table.

SELECT * FROM owners
FULL OUTER JOIN properties
ON owners.id = properties.owner_id;



22.  Update at least one of your properties to belong to the owner with id 1.

UPDATE properties
	SET owner_id = 1
	Where name = 'Archstone';


23.  Use an INNER JOIN to show all of the owners with associated properties.

SELECT * FROM owners
INNER JOIN properties
ON owners.id = properties.owner_id;

SELECT owners.name, properties.name from owners
INNER JOIN properties
ON owners.id = properties.owner_id;


24.  Use a CROSS JOIN to show all possible combinations of owners and properties.

SELECT * FROM owners
CROSS JOIN properties
WHERE owners.id = 1;

25.  In the properties table, change the name of the column name to property_name.

ALTER TABLE properties RENAME COLUMN name TO property_name;

26.  Count the total number of properties where the owner_id is between 1 and 3.

SELECT COUNT(*) FROM properties
	WHERE owner_id  BETWEEN 1 AND 3;


