# databasePractice1

bench@bench-Surface-Book:~$ psql -d postgres -U db_user
Mot de passe pour l'utilisateur db_user : 
psql (12.4 (Ubuntu 12.4-1.pgdg20.04+1))
Saisissez « help » pour l'aide.

postgres=> CREATE DATABASE db_1;
CREATE DATABASE
postgres=> \list
postgres=> \c db_1;
Vous êtes maintenant connecté à la base de données « db_1 » en tant qu'utilisateur « db_user ».
db_1=> CREATE TABLE USERS (id SERIAL PRIMARY KEY, name VARCHAR(30), password VARCHAR(30));
CREATE TABLE

psql -d db_1 -U db_user
Mot de passe pour l'utilisateur db_user : 
psql (12.4 (Ubuntu 12.4-1.pgdg20.04+1))
Saisissez « help » pour l'aide.

db_1=> SELECT * FROM users;
 id | name | password 
----+------+----------
(0 ligne)

db_1=> INSERT INTO users (name, password) VALUES ('alice','123'), ('bob','456'), ('charlie','789');
INSERT 0 3
db_1=> SELECT * FROM users;
 id |  name   | password 
----+---------+----------
  1 | alice   | 123
  2 | bob     | 456
  3 | charlie | 789
(3 lignes)


db_1=> INSERT INTO users (name, password) VALUES ('dan','101112'), ('eve','131415'), ('faythe','161718');
INSERT 0 3
db_1=> SELECT * FROM users;
 id |  name   | password 
----+---------+----------
  1 | alice   | 123
  2 | bob     | 456
  3 | charlie | 789
  4 | dan     | 101112
  5 | eve     | 131415
  6 | faythe  | 161718
(6 lignes)

db_1=> SELECT password  FROM  users WHERE LENGTH(password) > 3;
 password 
----------
 101112
 131415
 161718
(3 lignes)

db_1=> ALTER TABLE users ADD COLUMN bio VARCHAR DEFAULT 'hello, world';
ALTER TABLE

db_1=> SELECT * FROM users;
 id |  name   | password |     bio      
----+---------+----------+--------------
  1 | alice   | 123      | hello, world
  2 | bob     | 456      | hello, world
  3 | charlie | 789      | hello, world
  4 | dan     | 101112   | hello, world
  5 | eve     | 131415   | hello, world
  6 | faythe  | 161718   | hello, world
(6 lignes)

db_1=> UPDATE users SET bio = 'hello, i am user.name' WHERE bio = 'hello, world';
UPDATE 6
db_1=> SELECT * FROM users;
 id |  name   | password |          bio          
----+---------+----------+-----------------------
  1 | alice   | 123      | hello, i am user.name
  2 | bob     | 456      | hello, i am user.name
  3 | charlie | 789      | hello, i am user.name
  4 | dan     | 101112   | hello, i am user.name
  5 | eve     | 131415   | hello, i am user.name
  6 | faythe  | 161718   | hello, i am user.name
(6 lignes)


