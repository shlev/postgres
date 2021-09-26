# postgres

start postgres
- sudo -u postgres -i
- psql


## Database commands
- CREATE DATABASE <db_name>
- DROP DATABASE <db_name>
- SELECT * FROM <table_name>
- SELECT <field_1> <field_2> FROM <table> __ORDER BY__ <column> __DESC|ASC__
- SELECT * FROM <table_name> __LIMIT__
- SELECT * FROM <table_name> __OFFSET__
- SELECT * FROM <table_name> WHERE <field_1> IN (<value-1>, <value-2>, <value-3>,)
- SELECT * FROM <table_name> WHERE <field_1> __BETWEEN__ <value_1> __AND__ <value_2>
- SELECT * FROM <table_name> WHERE <field_1> __LIKE__ <pattern_1>   (case sensitive)
- SELECT * FROM <table_name> WHERE <field_1> __ILIKE__ <pattern_1>  (case insensitive)
  - pattern % any number of character
  - pattern _ exact number of characters

- SELECT __DISTINCT__ <field_1> FROM <table_name>
- SELECT <field_1> FROM <table_name> __GROUP BY__ <field_name>
- SELECT <field_1>, Count(*) FROM <table_name> GROUP BY <field_1> ORDER BY count DESC
- SELECT <field_1>, Count(*) FROM <table_name> GROUP BY <field_1> __HAVING__ <condition_func> ORDER BY count DESC
  - condition func example COUNT(*) > 5
- SELECT __COALESCE(<field_1>, <default_value>)__ from <table_name>
- SELECT 10 / NULLIF(<value_1>, 0)
  - NULLIF return NULL if arg1 = arg2
  - Division by Null equals NULL
  - optional  to use COALESCE for default value in case of NULL result
  
  
 ### Dates
- SELECT NOW()
- SELECT NOW()::DATE   => casting to date
- SELECT NOW()::TIME   => casting to time
- SELECT NOW() + __INTERVAL__ '10 DAYS' 
  - add or substract time units(DAY, MONTH, YEAR) 
- __EXTRACT__
- AGE()
  
- ALTER TABLE <table_name> __ADD CONSTRAINT__ <constraint_name> __UNIQUE__ (fields)
- ALTER TABLE <table_name> __ADD UNIQUE__ (fields)  => constraint name created by server.
  
- ... __ADD CONSTRAINT__ <constraint_name> __CHECK__ (condition)
  - condition example (gender = 'FEMALE' OR gender = 'MALE')
  
- __DELETE__ FROM <table_name>   => delete ALL records.
- DELETE FROM <table_name> WHERE <conditions>
  
- __UPDATE__ <table_name> __SET__ <field_1> = <new_value> => more fields seperate with comma(,)
  optionnl to use WHERE for selection.
- __ON CONFLICT__ (<field_or_fields>) __DO NOTHING__.   => handing constraint error for specific filed(s)
- ON CONFLICT (<field_or_fields) __DO__ UPDATE SET <field_name> = __EXCLUDED__.<field_name> =>perform         action on selected fields in case of constraint conflict.
  
### Relations
  1 to 1
  
```
  CREATE TABLE person (
      id BIGSERIAL NOT NULL PRIMARY KEY,
      first_name VARCHAR(50) NOT NULL,
      gender VARCHAR(7) 
      car_id BIGINT REFERENCES car (id)
  );
  
  CREATE TABLE car (
      id BIGSERIAL NOT NULL PRIMARY KEY,
      make VARCHAR(100) NOT NULL,
      model VARCHAR(100) NOT NULL, 
      price NUMERIC(19,2) NOT NULL
  );
```
- __JOIN__ select all fields on both tables <br> 
``` JOIN car ON person.car_id = car.id ```
- select columns
``` 
  SELECT person.first_name, car.model 
  FROM person
  JOIN car ON person.car_id = car.id 
``` 
  

  

<br><br><br>

## Server Commands.
| command | action| comment|
|---|---|---|
|\?|help| |
|\l| list databases||
|\c <db_name>|connect to database|
|\conninfo|connection info| connection from app details|
|\d | show table | |
|\dt| show tables without herlper tables|
|\df| show installed functions| adding function by EXTENTIONS|
|\i <file>| execute from file| 
|\x| toggle expand mode | rows presented vertically |
|\copy| export to CSV| |


## Links
 - [mockaroo.com](https://www.mockaroo.com/) Optional import table from content generator
 - [aggregate functions](https://www.postgresql.org/docs/9.5/functions-aggregate.html)
