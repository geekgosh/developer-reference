# Table of Content
- [References Tools](#references--tools)
- [CSS](#css)
- [React](#react)
- [NodeJs](#nodejs)
- [NPM Packages](#npm-packages)
- [Yarn](#yarn)
- [SQL](#sql)

## References & Tools
1. coverr.co <<< Great animation video for background
2. sizzy <<< Test website in various devices

## CSS
### Guidelines
1. CSS Naming BEM
2. SASS 7 - 1 Pattern

### Four Steps of CSS Building
- Compilation
- Concatenation
- Prefixing
- Compressing

## React


## NodeJs

## NPM Packages

|    Package    |     Usage     |
|:--------------|:-------------:|
|webpack||
|webpack-cli||
|babel-loader|teach babel how to work with webpack|
|babel-core|take input, parse it, generate output|
|babel-preset-env|ruleset for ES6&7 - ES5|
|css-loader||
|style-loader||
|file-loader||
|image-webpack-loader||
|url-loader||
|webpack-dev-server||
|concat||
|autoprefixer||
|postcss-cli||
|node-sass|compile sass code|
|pm2|multiple cluster for process|
|live-server|allow auto-reload|
|npm-run-all|run multiple npm script at once|

## Yarn
1. `yarn init` === `npm init`
2. `yarn add <package>` === `npm install <package> --save`
3. `yarn add <package> --dev` === `npm install <package> --save-dev`
4. `yarn remove <package>` === `npm remove <package> --save`
5. `yarn outdated` <<< check dependencies version
6. `yarn upgrade <package>` || `yarn upgrad <package>@<version>`
7. `yarn cache clean` <<< clean local cache
8. `yarn install` === `npm install`
9. `yarn run` === `npm run`
10. `yarn global add <package>` === `npm install <package> -g`

## SQL
### Cheatsheet
- `show database;`
- `create database <name>;`
- `drop database <name>;` 
- `use <database_name>;` use the database
- `select database();` show current using database
- `show warnings;`
- `show tables;`
- `drop table <table_name>;`
- `show triggers;`
- `drop trigger <trigger_name>;`
- `source <sql_file_name>;` < execute the sql file
- `select concat (<column>, <column>) ...;` < check out more by sql server functions - w3schools
- DISTINCT, ORDER BY, LIMIT, GROUP BY, SUM
- LIKE '%string%', '%\%%' escape string, '____' < amount of underscore refer to number of char or digit
- COUNT(*), COUNT(DISTINCT <column>), MIN, MAX, AVG
- `select title, pages from books where pages = (select max(pages) from books);` << To be more effective (this is 2 queries), can use below
- `select titile, pages from books order by pages asc limit 1;`
- Take care use of float and double, prefer using decimal where you can set the precision eg (10, 2)
- CURDATE(), CURTIME(), NOW(); eg. select NOW(),
- change_at TIMESTAMP DEFAULT NOW() ON UPDATE CURRENT_TIMESTAMP < auto update the time when update query is executed
- NOT LIKE '%abc%', !=, =, >, >= , <, <=, &&, ||, BETWEEN 1 AND 100, IN('King', 'Queen'), NOT IN('a', 'b'), %
- FOREIGN KEY(customer_id) REFERENCES customers(id)

### Column Modifier
- NOT NULL
- default <default_value>
- autoincrement
- , primary key (<column>)

### Others
- `select a as 'a haha'`
- `select * from table where haha = 'hoho'`

```sql
CREATE TABLE <table_name>
(
    <column_name> <data_type>
)
```
```sql 
- show columns from <database_name> || desc <database_name>;
```

### INSERT SINGLE RECORD
```sql 
- insert into <table_name>(<column>, <column if any>) values (<value> <value>);
e.g. insert into person(name, age) values ('Kitty', 6);
```

### INSERT MULTIPLE RECORD
```sql 
insert into <table_name>(<column>, <column if any>) values (<value> <value>), (<value> <value>), (<value> <value>);
```
  
### UPDATE RECORD
```sql 
update person set name = 'haha' where name = 'kiki';
```

### DELETE RECORD
```sql 
delete from person where name = 'king kong;
```

### DELETE ALL RECRODS IN PARTICULAR TABLE
```sql 
delete from <table_name>;
```

### CASE STATEMENTS
```sql
select title, released_year,
    case
        when released_year >= 2000 then 'Modern Lit'
        else '20th century lit'
    end as genre
from books;
```

### CREATE TRIGGER
```sql
CREATE TRIGGER <trigger_name>
    <trigger_time> <trigger_event> ON <table_name> FOR EACH ROW
    BEGIN
    ...
    END;
```
