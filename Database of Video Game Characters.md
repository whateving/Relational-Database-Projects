```sql
ALTER DATABASE first_database RENAME TO mario_database;
ALTER DATABASE
second_database=> \l
second_database=>                                     List of databases
+-----------------+--------------+----------+---------+---------+-----------------------+
|      Name       |    Owner     | Encoding | Collate |  Ctype  |   Access privileges   |
+-----------------+--------------+----------+---------+---------+-----------------------+
| mario_database  | freecodecamp | UTF8     | C.UTF-8 | C.UTF-8 |                       |
| postgres        | postgres     | UTF8     | C.UTF-8 | C.UTF-8 |                       |
| second_database | freecodecamp | UTF8     | C.UTF-8 | C.UTF-8 |                       |
| template0       | postgres     | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +|
|                 |              |          |         |         | postgres=CTc/postgres |
| template1       | postgres     | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +|
|                 |              |          |         |         | postgres=CTc/postgres |
+-----------------+--------------+----------+---------+---------+-----------------------+
(5 rows)

\c mario_database
You are now connected to database "mario_database" as user "freecodecamp".
mario_database=> DROP DATABASE second_database;
DROP DATABASE
mario_database=> \l
mario_database=>                                    List of databases
+----------------+--------------+----------+---------+---------+-----------------------+
|      Name      |    Owner     | Encoding | Collate |  Ctype  |   Access privileges   |
+----------------+--------------+----------+---------+---------+-----------------------+
| mario_database | freecodecamp | UTF8     | C.UTF-8 | C.UTF-8 |                       |
| postgres       | postgres     | UTF8     | C.UTF-8 | C.UTF-8 |                       |
| template0      | postgres     | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +|
|                |              |          |         |         | postgres=CTc/postgres |
| template1      | postgres     | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +|
|                |              |          |         |         | postgres=CTc/postgres |
+----------------+--------------+----------+---------+---------+-----------------------+
(4 rows)

\d
Did not find any relations.
mario_database=> CREATE TABLE characters();
mario_database=> CREATE TABLE
ALTER TABLE characters ADD COLUMN character_id SERIAL;
mario_database=> ALTER TABLE
select * from characters;
mario_database=>         
+--------------+
| character_id |
+--------------+
+--------------+
(0 rows)

\d characters
mario_database=>                                      Table "public.characters"
+--------------+---------+-----------+----------+--------------------------------------------------+
|    Column    |  Type   | Collation | Nullable |                     Default                      |
+--------------+---------+-----------+----------+--------------------------------------------------+
| character_id | integer |           | not null | nextval('characters_character_id_seq'::regclass) |
+--------------+---------+-----------+----------+--------------------------------------------------+

ALTER TABLE characters ADD COLUMN name VARCHAR(30);
ALTER TABLE
mario_database=> ALTER TABLE characters ADD COLUMN name VARCHAR(30) and NOT NULL;
ERROR:  syntax error at or near "and"
LINE 1: ...LTER TABLE characters ADD COLUMN name VARCHAR(30) and NOT NU...
                                                             ^
mario_database=> \d characters
mario_database=>                                             Table "public.characters"
+--------------+-----------------------+-----------+----------+--------------------------------------------------+
|    Column    |         Type          | Collation | Nullable |                     Default                      |
+--------------+-----------------------+-----------+----------+--------------------------------------------------+
| character_id | integer               |           | not null | nextval('characters_character_id_seq'::regclass) |
| name         | character varying(30) |           |          |                                                  |
+--------------+-----------------------+-----------+----------+--------------------------------------------------+

ALTER TABLE characters DROP COLUMN name;
ALTER TABLE
mario_database=> ALTER TABLE characters ADD COLUMN name VARCHAR(30) NOT NULL;
mario_database=> ALTER TABLE
ALTER TABLE characters ADD COLUMN homeland VARCHAR(60);
ALTER TABLE
mario_database=> ALTER TABLE characters ADD COLUMN favorite_color VARCHAR(30);
mario_database=> ALTER TABLE
\d characters
mario_database=>                                              Table "public.characters"
+----------------+-----------------------+-----------+----------+--------------------------------------------------+
|     Column     |         Type          | Collation | Nullable |                     Default                      |
+----------------+-----------------------+-----------+----------+--------------------------------------------------+
| character_id   | integer               |           | not null | nextval('characters_character_id_seq'::regclass) |
| name           | character varying(30) |           | not null |                                                  |
| homeland       | character varying(60) |           |          |                                                  |
| favorite_color | character varying(30) |           |          |                                                  |
+----------------+-----------------------+-----------+----------+--------------------------------------------------+

INSERT INTO characters(name, homeland, favorite_color) VALUES('Mario', 'Mushroom Kingdom', 'Red');
INSERT 0 1
mario_database=> SELECT * FROM characters;
                              
+--------------+-------+------------------+----------------+
| character_id | name  |     homeland     | favorite_color |
+--------------+-------+------------------+----------------+
|            1 | Mario | Mushroom Kingdom | Red            |
+--------------+-------+------------------+----------------+
(1 row)

mario_database=> INSERT INTO characters(name, homeland, favorite_color) VALUES('Luigi', 'Mushroom Kingdom', 'Green');
INSERT 0 1
mario_database=> SELECT * FROM characters;
mario_database=>                               
+--------------+-------+------------------+----------------+
| character_id | name  |     homeland     | favorite_color |
+--------------+-------+------------------+----------------+
|            1 | Mario | Mushroom Kingdom | Red            |
|            2 | Luigi | Mushroom Kingdom | Green          |
+--------------+-------+------------------+----------------+
(2 rows)

SELECT * FROM chaINSERT INTO characters(name, homeland, favorite_color) VALUES('Peach', 'Mushroom Kingdom', 'Pink');
INSERT 0 1
mario_database=> 
mario_database=> INSERT INTO characters(name, homeland, favorite_color) VALUES('Toadstool', 'Mushroom Kingdom', 'Red'), ('Bowser
', 'Mushroom Kingdom', 'Green');
mario_database=> INSERT 0 2
INSERT           INSERT INTO characters(name, homeland, favorite_color) VALUES('Daisy', 'Sarasaland', 'Yellow'), ('Yoshi', 'Dino
saur Land', 'Green');
INSERT 0 2
mario_database=> SELECT * FROM characters;
mario_database=>                                 
+--------------+-----------+------------------+----------------+
| character_id |   name    |     homeland     | favorite_color |
+--------------+-----------+------------------+----------------+
|            1 | Mario     | Mushroom Kingdom | Red            |
|            2 | Luigi     | Mushroom Kingdom | Green          |
|            3 | Peach     | Mushroom Kingdom | Pink           |
|            4 | Toadstool | Mushroom Kingdom | Red            |
|            5 | Bowser    | Mushroom Kingdom | Green          |
|            6 | Daisy     | Sarasaland       | Yellow         |
|            7 | Yoshi     | Dinosaur Land    | Green          |
+--------------+-----------+------------------+----------------+
(7 rows)

UPDATE characters SET favorite_color='Orange' WHERE name='Daisy';
UPDATE 1
mario_database=> SELECT * FROM characters;
mario_database=>                                 
+--------------+-----------+------------------+----------------+
| character_id |   name    |     homeland     | favorite_color |
+--------------+-----------+------------------+----------------+
|            1 | Mario     | Mushroom Kingdom | Red            |
|            2 | Luigi     | Mushroom Kingdom | Green          |
|            3 | Peach     | Mushroom Kingdom | Pink           |
|            4 | Toadstool | Mushroom Kingdom | Red            |
|            5 | Bowser    | Mushroom Kingdom | Green          |
|            7 | Yoshi     | Dinosaur Land    | Green          |
|            6 | Daisy     | Sarasaland       | Orange         |
+--------------+-----------+------------------+----------------+
(7 rows)

UPDATE characters SET name='Toad' WHERE favority_color='Red';
ERROR:  column "favority_color" does not exist
LINE 1: UPDATE characters SET name='Toad' WHERE favority_color='Red'...
                                                ^
HINT:  Perhaps you meant to reference the column "characters.favorite_color".
mario_database=> UPDATE characters SET name='Toad' WHERE favorite_color='Red';
mario_database=> UPDATE 2
UPDATE charactersSELECT * FROM characters;
mario_database=>                                
+--------------+--------+------------------+----------------+
| character_id |  name  |     homeland     | favorite_color |
+--------------+--------+------------------+----------------+
|            2 | Luigi  | Mushroom Kingdom | Green          |
|            3 | Peach  | Mushroom Kingdom | Pink           |
|            5 | Bowser | Mushroom Kingdom | Green          |
|            7 | Yoshi  | Dinosaur Land    | Green          |
|            6 | Daisy  | Sarasaland       | Orange         |
|            1 | Toad   | Mushroom Kingdom | Red            |
|            4 | Toad   | Mushroom Kingdom | Red            |
+--------------+--------+------------------+----------------+
(7 rows)

UPDATE characters SET name='Mario' where character_id=1;
UPDATE 1
mario_database=> SELECT * FROM characters;
mario_database=>                                
+--------------+--------+------------------+----------------+
| character_id |  name  |     homeland     | favorite_color |
+--------------+--------+------------------+----------------+
|            2 | Luigi  | Mushroom Kingdom | Green          |
|            3 | Peach  | Mushroom Kingdom | Pink           |
|            5 | Bowser | Mushroom Kingdom | Green          |
|            7 | Yoshi  | Dinosaur Land    | Green          |
|            6 | Daisy  | Sarasaland       | Orange         |
|            4 | Toad   | Mushroom Kingdom | Red            |
|            1 | Mario  | Mushroom Kingdom | Red            |
+--------------+--------+------------------+----------------+
(7 rows)

UPDATE characters SET favority_color='Blue' WHERE character_id=4;
ERROR:  column "favority_color" of relation "characters" does not exist
LINE 1: UPDATE characters SET favority_color='Blue' WHERE character_...
                              ^
mario_database=> UPDATE characters SET favorite_color='Blue' WHERE character_id=4;
mario_database=> UPDATE 1
UPDATE characters SET favorite_color='Yellow' WHERE character_id=5;
mario_database=> UPDATE 1

mario_database=> UPDATE characters SET homeland='Koopa Kingdom' WHERE character_id=5;
UPDATE 1
mario_database=> SELECT * FROM characters;
mario_database=>                                
+--------------+--------+------------------+----------------+
| character_id |  name  |     homeland     | favorite_color |
+--------------+--------+------------------+----------------+
|            2 | Luigi  | Mushroom Kingdom | Green          |
|            3 | Peach  | Mushroom Kingdom | Pink           |
|            7 | Yoshi  | Dinosaur Land    | Green          |
|            6 | Daisy  | Sarasaland       | Orange         |
|            1 | Mario  | Mushroom Kingdom | Red            |
|            4 | Toad   | Mushroom Kingdom | Blue           |
|            5 | Bowser | Koopa Kingdom    | Yellow         |
+--------------+--------+------------------+----------------+
(7 rows)

SELECT * FROM characters ORDER BY character_id;
mario_database=>                                
+--------------+--------+------------------+----------------+
| character_id |  name  |     homeland     | favorite_color |
+--------------+--------+------------------+----------------+
|            1 | Mario  | Mushroom Kingdom | Red            |
|            2 | Luigi  | Mushroom Kingdom | Green          |
|            3 | Peach  | Mushroom Kingdom | Pink           |
|            4 | Toad   | Mushroom Kingdom | Blue           |
|            5 | Bowser | Koopa Kingdom    | Yellow         |
|            6 | Daisy  | Sarasaland       | Orange         |
|            7 | Yoshi  | Dinosaur Land    | Green          |
+--------------+--------+------------------+----------------+
(7 rows)

ALTER TABLE characters ADD PRIMARY KEY(name);
ALTER TABLE
mario_database=> \d characters
mario_database=>                                              Table "public.characters"
+----------------+-----------------------+-----------+----------+--------------------------------------------------+
|     Column     |         Type          | Collation | Nullable |                     Default                      |
+----------------+-----------------------+-----------+----------+--------------------------------------------------+
| character_id   | integer               |           | not null | nextval('characters_character_id_seq'::regclass) |
| name           | character varying(30) |           | not null |                                                  |
| homeland       | character varying(60) |           |          |                                                  |
| favorite_color | character varying(30) |           |          |                                                  |
+----------------+-----------------------+-----------+----------+--------------------------------------------------+
Indexes:
    "characters_pkey" PRIMARY KEY, btree (name)

ALTER TABLE characters DROP CONSTRAINT name;
ERROR:  constraint "name" of relation "characters" does not exist
mario_database=> ALTER TABLE characters DROP CONSTRAINT characters_pkey;
ALTER TABLE
mario_database=> \d characters
mario_database=>                                              Table "public.characters"
+----------------+-----------------------+-----------+----------+--------------------------------------------------+
|     Column     |         Type          | Collation | Nullable |                     Default                      |
+----------------+-----------------------+-----------+----------+--------------------------------------------------+
| character_id   | integer               |           | not null | nextval('characters_character_id_seq'::regclass) |
| name           | character varying(30) |           | not null |                                                  |
| homeland       | character varying(60) |           |          |                                                  |
| favorite_color | character varying(30) |           |          |                                                  |
+----------------+-----------------------+-----------+----------+--------------------------------------------------+

ALTER TABLE characters ADD PRIMARY KEY(character_id); 
ALTER TABLE
```
