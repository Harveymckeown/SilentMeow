CREATE TABLE Planets (Id CHAR(36), Name VARCHAR(10), Position INT, PRIMARY KEY(Id))# Pets Database
Develop SQL statements required to manipulate a database of pets<br>

[data types](https://www.w3schools.com/sql/sql_datatypes.asp),
[hsqldb](http://hsqldb.org/),
[sql](https://www.w3schools.com/sql/),
[uuid](https://www.uuidgenerator.net/)

## Pre-requirements
* Ensure the Eclipse IDE has Maven by looking for M2E from Help About ([details](https://www.vogella.com/tutorials/EclipseMaven/article.html))
* Install `DBViewer Plugin 1.2.2.v20101009` by ZIGEN from the Eclipse IDE marketplace
* Import into Eclipse as Git with smart import (accepting all defaults in wizard)
* Let the IDE finish building dependencies before proceeding (see bottom right of Eclipse)

## Steps
* Run the PetsDB app to start the database
* Develop Pets-based SQL statements
* Switch to DBViewer perspective to test
* Stop the PetsDB app to shutdown database
* Ensure SQL documented within this README
* Push update README back to forked GitHub

## Bonus
* Create another related table with SQL

## Database Schema

**Animal table**
 - Hunger INT
 - Id CHAR(36)
 - Name VARCHAR(100)
 - OwnerId CHAR(36)
 - Species CHAR(1)

**Owner table**
 - Id CHAR(36)
 - Name VARCHAR(100)
 - Town VARCHAR(100)
 
**To create the Owner table**<br>
CREATE TABLE Owner (Id CHAR(36), Name VARCHAR(100), Town VARCHAR(100), PRIMARY KEY(id))

**To create the Animal table**<br>
CREATE TABLE Animal (Id CHAR(36), Name VARCHAR(36), OwnerId CHAR(36), Hunger INT, Species CHAR(1), PRIMARY KEY (Id), FOREIGN KEY (OwnerId) REFERENCES Owner(Id))

**To insert a new Owner row**<br>
INSERT INTO Owner (Id, Name, Town) VALUES ('cb03a7e6-e01d-4545-8329-fd0bf696abad', 'Moe Lester', 'Rochdale')

**To insert a new Cat row**<br>
INSERT INTO Animal (Id, Name, OwnerId, hunger, species) VALUES ('b9cb4400-5a0b-43bf-bcb7-5332b6b4bf12', 'patches' , 'cb03a7e6-e01d-4545-8329-fd0bf696abad', 60,  'C')

**To insert a new Dog row**<br>
INSERT INTO Animal (Id, Name, OwnerId, hunger, species) VALUES ('b7e68db5-17c7-464e-b230-a9d6260433e5', 'mike' , 'cb03a7e6-e01d-4545-8329-fd0bf696abad', 40,  'D')

**To query an animal**<br>
SELECT Animal.Name FROM Animal animal WHERE animal.Name = 'mike'

**To query all pets for an owner**<br>
SELECT Animal.Name FROM Owner owner, Animal animal WHERE owner.Name = 'Moe Lester' AND animal.OwnerId = Owner.Id