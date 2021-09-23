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


<br><br><br>

## Server Commands.
| command | action| comment|
|---|---|---|
|\c <db_name>|connect to database|
|\conninfo|connection info| connection from app details|
|\d | show table | |
|\dt| show tables without herlper tables|



## Links
 - [mockaroo.com](https://www.mockaroo.com/) Optional import table from content generator
 - [aggregate functions](https://www.postgresql.org/docs/9.5/functions-aggregate.html)
