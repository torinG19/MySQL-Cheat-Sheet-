# MySQL Cheat Sheet
## How to login into mysql from terminal
```
mysql -u root -p
```
## How to CREATE user
```
CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
```
## How to GRANT PRIVILEGES, Show granted privileges and remove.
```
GRANT ALL PRIVILEGES ON * . * TO 'user'@'localhost';
FLUSH PRIVILEGES;
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'user'@'localhost';
```
## How to SHOW, DELETE & CREATE DATABASES & SELECT DATABASES
```
CREATE DATABASE mydatabase;
DROP DATABASE mydatabase;
```
## How to CREATE a TABLE with Columns and their data types
```
CREATE TABLE table_name(
id INT AUTO_INCREMENT,
   first_name VARCHAR(100),
   last_name VARCHAR(100),
   email VARCHAR(100),
   password VARCHAR(100),
   PRIMARY KEY(id)
);
```
## How to SHOW, DELETE & DROP Tables
```
DROP TABLE tablename;
```
## How to Insert ROWS & RECORDS (single and multiple)
```
INSERT INTO table_name (first_name, last_name, email, password) values ('Matt', 'Tooty', 'brad@gmail.com', '12345');
```
```
INSERT INTO table_name (first_name, last_name, email, password) values ('Zack', 'Jackson', 'zack123@gmail.com', '123456'), ('bob', 'Watson', 'bob123@gmail.com', '1234567');
```
## How to SELECT with the WHERE Clause
```
SELECT * FROM table_name WHERE first_name = zack;

```
## How to SELECT with the WHERE Clause using a range
```
SELECT * FROM table_name WHERE age BETWEEN 10 AND 30;
```
## How to DELETE an individual ROW
```
DELETE FROM table_name WHERE id = 8;
```
## How to UPDATE a ROW
```
UPDATE table_name SET email = 'toringraham19@gmail.com' WHERE id = 3;
```
## How to add a new column and modify it
```
ALTER TABLE table_name ADD age VARCHAR(4);
```
```
ALTER TABLE table_name MODIFY COLUMN age INT(4);
```
## How to Order by and use Distinct
```
SELECT * FROM table_name ORDER BY column_name ASC;
SELECT * FROM table_name ORDER BY column_name DESC;
```
```
SELECT DISTINCT location FROM table_name;
```
## How to Concatenate Columns
```
SELECT CONCAT(first_name, ' ', last_name) AS 'Name', dept FROM table_name;
```
## How to Select Distinct Rows
```
SELECT DISTINCT column_name FROM table_name;
```
## How to use LIKE to Search
```
SELECT * FROM table_name WHERE first_name LIKE 'th%';
SELECT * FROM table_name WHERE first_name LIKE '%k';
SELECT * FROM table_name WHERE first_name LIKE '%er%';
```
## How Select using IN
```
SELECT * FROM table_name WHERE column_name IN ('value1', 'value2');
```
## How to Create & Remove Index
```
CREATE INDEX LIndex On table_name(location);
DROP INDEX LIndex ON table_name;
```
## Create Two Tables demonstrating a one to many relationship that shows a PK & FK
```
CREATE TABLE posts(
id INT AUTO_INCREMENT,
   user_id INT,
   title VARCHAR(100),
   body TEXT,
   publish_date DATETIME DEFAULT CURRENT_TIMESTAMP,
   PRIMARY KEY(id),
   FOREIGN KEY (user_id) REFERENCES table_name(id)
);
```
## How to use Inner Join
```
SELECT
  table_name.first_name,
  table_name.last_name,
  posts.title,
  posts.publish_date
FROM table_name
INNER JOIN posts
ON table_name.id = posts.user_id
ORDER BY posts.title;
```
## How to JOIN Multiple Tables
```
SELECT
comments.body,
posts.title,
table_name.first_name,
table_name.last_name
FROM comments
INNER JOIN posts on posts.id = comments.post_id
INNER JOIN table_name on table_name.id = comments.user_id
ORDER BY posts.title;
```