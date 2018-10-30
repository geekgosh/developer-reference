# Table of Content
- [References Tools](#references--tools)
- [Performance](#performance)
- [Security](#security)
- [CSS](#css)
- [React](#react)
- [NodeJs](#nodejs)
- [NPM Packages](#npm-packages)
- [Yarn](#yarn)
- [SQL](#sql)
- [#Docker](#docker)
- [Things To Expore](#things-to-explore)

## References & Tools
1. coverr.co <<< Great animation video for background
2. sizzy <<< Test website in various devices
3. OWASP <<< IT Security Information
4. PageSpeed Insights & WebPageTest <<< Test page speed

## Performance
1. HTML, CSS and JS minifier
2. Image compresser (resize, and reduce quality)
3. Image remove meta - verexif
4. Web page speed - PageSpeed Insights & WebPageTest
5. Code Splitting - React check example (so cool), got route and component based code splitting
6. Favicon generator
7. Use CDN e.g. Cloudflare, Amazon CloudFront & Azure Content Delivery Network
8. Use gzip compression for files
9. Caching - cache the file by service worker and max age
10. Load balancing - use nginx and test by using "loadtest"

## Security
1. Free HTTPS - Let's Encrypt
2. CDN - Cloudflare
3. NPM package named "nsp" and "snyk" - good for checking npm package security
4. Logging package named "morgan" and "winston"
5. Https everywhere - sanitize input, no eval(), no document.write(), content security policy, secure + HTTPOnly Cookies
6. Code Secret - Environment variable, commit history
7. Secure Headers - npm package "helmet"
8. Access Control (Give least privilege) - npm package "cors"
9. Data Management - bcrypt, scrypt, Aragon2 & pgcrypto

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
### Template
1. Pug <<< previously known as Jade
2. Mustache
3. EJS

## NPM Packages

|    Package    |     Usage     |
|:--------------|:-------------:|
|react||
|react-dom||
|enzyme|testing framework|
|redux|State management|
|react-redux|State management for react|
|redux-logger||
|redux-thunk||
|redux-promise||
|react-router-config||
|materialize-css|material design css library|
|react-stripe-checkout|credit card payment|
|prettier|make code prettier in precommit|
|react-helmet|add HTML tag|
|node-fetch|Http Client|
|isomorphic-fetch|Http Client|
|axios|Http Client|
|concurrently||
|dotenv||
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
|express||
|faker|generate dummy data|
|multer||
|pm2|multiple cluster for process|
|body-parser||
|jest|testing framework|
|passport|authenticate user|
|passport-local||
|morgan|logging package|
|winston|logging package|
|serialize-javascript|serialize javascript to prevent injection|
|express-http-proxy||
|redis|cache server|
|jsonwebtoken|token based authentication|
|cookie-session|cookie based authentication|
|stripe|credit card payment|
|sendgrid|mailer|
|localtunnel|web to localhost|
|helmet|secure HTTP headers|
|cors|access-control|
|bcrypt|data management|
|bcrypt-nodejs|data management|
|scrypt|data management|
|aragon2|data management|
|pgcrypto|data management|
|synk|check npm package security|
|live-server|allow auto-reload|
|npm-run-all|run multiple npm scripts at once|
|nodemon||

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

## Docker
### CheatSheet
- docker run <image_name> - (create and start the image into container)
- docker ps - (list all the current container)
- docker ps --all - (list all created container)
- docker system prune - (delete all container)
- docker logs <container_id> - (retrieve logs of the container)
- docker stop <container_id> - (stop the container)
- docker kill <container_id> - (direct stop the container)
- docker exec -it <container_id> <new_image_name> - (add new functionality into particular container)
- docker exec -it <container_id> sh - (enter the shell command)
- docker build -f <custom_docker_filename> . >>> build docker with custom filename
- docker run -p 3000:3000 -v $(pwd):/app <image_id> >>> reference file (pwd only work in git bash)
- docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <image_id> >>> reference file but exclude node_modules (pwd only work in git bash)
- docker run <image_id> <command> - e.g. docker run xxxx npm run test

### Create custom docker image
1. Create file named "Dockerfile", and put configuration inside
2. docker build .
2. docker build -t <your_docker_id>/<container_name>:<version> . - (with custom image tags)
3. docker run <container_id>

#### docker run with port mapping incoming port:port inside container
- docker run -p 8080:8080 <image_id>
- docker run -it <image_id> sh - (go into shell)

### Docker readme
1. docker wil remember the order in docker file and cache if it is the same, so don't move the order if can

### Docker compose
- docker-compose ps >>> list all docker compose
- docker-compose up >>> docker run <image>
- docker-compose up -d >>> run in background
- docker-compose up --build >> docker build. && docker run <image>

## Things to Explore
1. WebGL
2. Speech API & Speech Synthesis API
3. Web animation - element.animate
4. Web Push Notifications
5. Broadcast Channel API
6. Payment Request API
7. Web Share API
8. Sensor API
9. CSS Typed Object Model
10. Web Authentication API - WebAuthn
11. Payment Handler API
12. AR and VR on the web
13. CSS Scroll Snap
14. Page Lifecycle API
