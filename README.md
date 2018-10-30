# Table of Content
- [References & Tools](#references--tools)
- [Performance](#performance)
- [Security](#security)
- [CSS](#css)
- [React](#react)
- [NodeJs](#nodejs)
- [NPM Packages](#npm-packages)
- [Yarn](#yarn)
- [SQL](#sql)
- [MongoDB](#mongodb)
- [#Docker](#docker)
- [#Git & GitHub](#git--github)
- [Things To Expore](#things-to-explore)

## References & Tools
1. [Animation video for background](https://coverr.co/)
2. [Test website in various devices](https://sizzy.co/)
3. [IT Security Information](https://www.owasp.org/)
4. PageSpeed Insights & WebPageTest <<< Test page speed
5. [Free High Resolution Wallpaper](https://unsplash.com/)
6. [HTML5 & CSS3 Compatibility Checker](http://caniuse.com/)
7. [CSS Selectors](https://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048)
8. [CSS Tricks](https://css-tricks.com/)
9. [<hr /> style](https://css-tricks.com/examples/hrs/)
10. [jQUery in Javascript](http://youmightnotneedjquery.com/)
11. [Color Gradients Sample](https://uigradients.com/)
12. [CSS autoprefixer](https://autoprefixer.github.io/)
13. ColorZilla - Google Chrome Plugin
14. Postman <<< API Tester

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
### Lifecycle in Order
In Order
--------
1. Mounting - Run during first time rendering


  i.) `componentWillMount()` <<< execute only once
 ii.) `render()` <<< ReactDOM.render() will execute this
iii.) `componentDidMount()` <<< take place(preferred) to make AJAX call, Web API, Javascript Framework, setInterval, setTimeout

2. Updating - A component updates every time that it renders, starting with the second render

  i.) componentWillReceiveProps <<< get called only if receive props
 ```js
  componentWillReceiveProps: function(nextProps) {
    if (nextProps.number > this.state.highest) {
      this.setState({
        highest: nextProps.number
      })
    }   
  }
```

 ii.) shouldComponentUpdate <<< after componentWillReceiveProps & rendering
       
    ```js
    return true || false;
	True = proceed as usual
	False = component will not update, methods after would not execute(incl rendering)
	Argument(nextProps, nextState)
    ```

iii.) componentWillUpdate

      ```js
      Argument(nextProps, nextState)
      Possible usage: checking window size, interacting with an API
      ```
 
iv.) render

  v.) componentDidUpdate
      
    ```js  
    Argument(prevProps, prevState)
    Possible usage: browser, API

	if (this.state.latestClick < prevState.latestClick) {
  		this.endGame();
	}
    ```

3. Unmounting
i.) componentWillUnmount

```js
Argument(prevProps, prevState)
This could happen if the DOM is rerendered without the component, 
or if the user navigates to a different website or closes their web browser.
```

### Tips
Tips
====
1. import React, { PureComponent } form 'react';
PureComponent same as the Component, but it will execute the shouldComponentUpdate() by default with looking whether any props or state is changed, if yes, then update, vice versa.

2. Correctly setState
```js
this.setState(prevState, props) => {
	return {
		toggleClicked prevState.toggleClicked + 1;
	}
}
```

3. Check type of props
- `npm install --save prop-types`

```js
import PropTypes from 'prop-types';

[ClassName].propTypes = {
	click: PropTypes.func,
	name: PropTypes.string,
	age: PropTypes.number,
	changed:  PropTypes.func	
};
```

4. Tiny combination
```js
componentDidMount() {
	if(this.props.position === 0) {
		this.inputElement.focus();
	}
}

<input position={index} ref={(inp) => { this.inputElement = inp }}
```

5. Load route lazily, which mean load the page/component only when needed in Single Page Application
- Create a higher order component
e.g. asyncComponent.js

```js
import React, { Component } from 'react';

const asyncComponent = (importComponent) => {
	return class extends Component {
		state = {
			component: null
		}

		componentDidMount() {
			importComponent()
				.then(cmp => {
					this.setState({ component: cmp.default });
				});
		}

		render() {
			const c = this.state.component;

			return C ? <C {...this.props} /> : null;
		}
	}
}

export default asyncComponent;
```

In other file
```js
import asyncComponent from '[the path to asyncComponent.js]';

const AsyncNewPost = asyncComponent(() => {
	return import('./NewPost/NewPost');
});

<Route to="/newpost" component={AsyncNewPost} />
```

Done :)

## NodeJs
### View Engine
1. Pug <<< previously known as Jade
2. Mustache
3. EJS
4. hbs

## NPM Packages

|    Package    |     Usage     |
|:--------------|:-------------:|
|react||
|react-dom||
|lodash|utility library|
|eslint|Javascript and JSX syntax checker|
|enzyme|testing framework|
|redux|State management|
|react-redux|State management for react|
|redux-logger||
|redux-thunk||
|redux-promise||
|redux-sage||
|react-router-config||
|materialize-css|material design css library|
|react-stripe-checkout|credit card payment|
|prettier|make code prettier in precommit|
|react-helmet|add HTML tag|
|node-fetch|Http Client|
|isomorphic-fetch|Http Client|
|axios|Http Client|
|whatwg-fetch|Http Client|
|request|Http Client|
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
|mongodb|document type database|
|mongoose|object relational mapping for mongo|
|faker|generate dummy data|
|validator|validator|
|multer||
|pm2|multiple cluster for process|
|body-parser||
|expect|assertions library|
|supertest|testing for express|
|rewire|variable swap for testing|
|jest|testing framework|
|passport|authenticate user|
|passport-local||
|moment|deal with time|
|morgan|logging package|
|winston|logging package|
|serialize-javascript|serialize javascript to prevent injection|
|express-http-proxy||
|redis|cache server|
|jsonwebtoken|token based authentication|
|cookie-session|cookie based authentication|
|stripe|credit card payment|
|sendgrid|mailer|
|http-server|local server|
|localtunnel|web to localhost|
|helmet|secure HTTP headers|
|yarns|encode & decode text on url|
|cors|access-control|
|bcrypt|data management|
|bcrypt-nodejs|data management|
|crypto-js|data management|
|scrypt|data management|
|aragon2|data management|
|pgcrypto|data management|
|socket.io|web socket|
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

## MongoDB
### Script
- `db.getUsers();`
- `db.createUser({user: <username>, pwd: <password>, roles: [{ role: 'userAdmin', db: <database_name> }]});`
- `mongod --auth --dbpath <db_directory_path>` // open mongodb with authentication 
- `db.auth(<user>, <password>);`
- `show dbs;`
- `use <database>;`
- `db.dropDatabase();`
- `show collections;`
- `db.createCollection(<string - collection_name>);`
- `db.<collection>.drop();`
- `db.<collection>.insert(<document>);`
- `db.<collection>.find();`
- `db.<collection>.find()[0];`
- `db.<collection>.find({ _id: ObjectId('idxxx') });`
- `db.<collection>.find().explain();`
- `db.<collection>.find().pretty();`
- `db.<collection>.save(<document>);`
- `load(<path_to_js_file_with_script>);` // load file as script
- `db.<collection>.createIndex({ age: 1 });` // 1 = ASC, -1 = DESC
- `db.<collection>.getIndexes();` // return all indexes createdv
- `db.<collection>.dropIndex({ age: 1 }); `
- `db.<collection>.insert({ _id: 1, "name" : "king" });` // own object id - discourage
pros: easy for use (eg product/1);
cons: object id can get timestamps (db.<collection>.find()[0]._id.getTimestamp())
- `db.<collection>.aggregate();` 
- `db.<collection>.distinct();`
- `db.<collection>.count();`
- `db.<collection>.sort();`



Example
=======
- `db.<collection>.find({"name.firstname": "Sunil"});`
- `db.<collection>.find({"age": {$eq: 21}});`
- `db.<collection>.find({"age": {$lt: 21}});`
- `db.<collection>.find({"age": {$gt: 21}});`
- `db.<collection>.find({"age": {$gte: 21}});`
- `db.<collection>.find({"age": {$lte: 21}});`
- `db.<collection>.find({"age": {$ne: 21}});`
- `db.<collection>.find({"age": {$in: [21, 31]}});`
- `db.<collection>.find({"age": {$exists: true, $nin: [21, 31]}});`

- `db.<collection>.uodate({"name.firstName": "Sunil", { $set: { "age": 20 } }});`
- `db.<collection>.uodate({"name.firstName": "Sunil", { $set: { "age": 20 } }, { upsert:true } });` // auto insert if the record not found

- `db.<collection>.remove({"name.firstName": "Alun"});`
- `db.<collection>.remove({"name.firstName": "Alun"}, 1);` // 1 mean delete only first record that matching the criteria
- `db.<collection>.remove(); // remove all

- `db.<collection>.aggregate([{$group: { _id: "$author", total_posts: {$sum:1} }}]);`
- `db.<collection>.distinct("subjects");`
- `db.<collection>.count();`
- `db.<collection>.find({"subjects": "Maths"}).count();`
- `db.<collection>.sort({ age: 1 });` // 1 for ascending order, -1 for descending order
- `db.<collection>.find().sort({ $natural: 1 });`

- `db.<collection>.find({empName:{$regex:"sunil"}});`
- `db.<collection>.find({empName:/Sunil/});`

Doubt
=====
1. The way how mongodb sort data in natural, first based on insertion, second based on update, latest update put into last

Real Example
============
Assume below data, to get their total for both a and b for each name
{ Name: 'X', Prod: { 'a': 25, b: '75' } }
{ Name: 'Y', Prod: { 'a': 33, b: '66' } }
To solve this, we need both group by and reduce function
Answer:
db.<collection>.group({key:{'Name':1},reduce:function(curr,result){result.total+=curr.Prod.a+curr.Prod.b;},initial:{total:0}});

Others
======
1. Map-Reduce
```js
db.<collection>.mapReduce(
    function() { emit(this.emp_id, this.loanAmount) },
    function(key, values) { return Array.sum(values); },
    {
        query: { loanStatus: "Active" },
        out: "TotaLoan"
    }.find();
);
```
2. .toArray()
3. Namespace in mongodb = Database + Collection e.g. Udemy.course
4. ObjectId in Mongodb is a 12-byte JSON which generated by: timestamp, process id, counter, machine identifier
5. Mongodb does not use big amount of memory in order to run, where it can dynamicly change based on needs
6. It is recommended to run on 64bit machine rather than 32bit is because 32bit maximum support 2gb storage only, 64bit no limit
7. Why are mongoDB data files so large in size?
Because it pre-allocates the data files to avoid the file system fragmentation
8. When should we embed documents?
- For relationships between entities
- To achieve one-to-many relationship
- To improve the performance
10. Maximum 50 replica set (7 voting member, 34 non voting)
members[n].priority = 1;

Key Feature
===========
1. NoSQL
2. Faster than RDBMS
3. Agile
4. Highly Scalable
5. Flexible data model
6. Dynamic schema

Replica Set
===========
- `mongod --replSet <replicat_set_name> --dbpath <database_directory_path>`
> `rs.status();` - show replicate set status
> `rs.initiate();` - initiate the replica set

1 PRIMARY NODE and 2 REPLICA NODE
=================================
- Set port for each mongodb, use `--port <port>` when start the instance
- `mongod --replSet <replicat_set_name> --dbpath <database_directory_path` <<< different path for each>
- `db.hostInfo();` < to get the hostName

In primary node
---------------
- `rs.initiate();`
- `rs.add(<host_name>)` - add other node to the replica set

## Docker
### CheatSheet
- `docker run <image_name>` - (create and start the image into container)
- `docker ps` - (list all the current container)
- `docker ps --all` - (list all created container)
- `docker system prune` - (delete all container)
- `docker logs <container_id>` - (retrieve logs of the container)
- `docker stop <container_id>` - (stop the container)
- `docker kill <container_id>` - (direct stop the container)
- `docker exec -it <container_id> <new_image_name>` - (add new functionality into particular container)
- `docker exec -it <container_id> sh` - (enter the shell command)
- `docker build -f <custom_docker_filename> .` >>> build docker with custom filename
- `docker run -p 3000:3000 -v $(pwd):/app <image_id>` >>> reference file (pwd only work in git bash)
- `docker run -p 3000:3000 -v /app/node_modules -v $(pwd):/app <image_id>` >>> reference file but exclude node_modules (pwd only work in git bash)
- `docker run <image_id> <command>` - e.g. docker run xxxx npm run test

### Create custom docker image
1. Create file named "Dockerfile", and put configuration inside
2. `docker build .`
2. `docker build -t <your_docker_id>/<container_name>:<version> .` - (with custom image tags)
3. `docker run <container_id>`

#### docker run with port mapping incoming port:port inside container
- `docker run -p 8080:8080 <image_id>`
- `docker run -it <image_id> sh` - (go into shell)

### Docker readme
1. docker wil remember the order in docker file and cache if it is the same, so don't move the order if can

### Docker compose
- `docker-compose ps` >>> list all docker compose
- `docker-compose up` >>> docker run <image>
- `docker-compose up -d` >>> run in background
- `docker-compose up --build` >> docker build. && docker run <image>

## Git & Github
### Git
1.) `git init`
2.) `git status`
3.) `git add -A | git add .`
4.) `git commit -m "Commit Message"`
5.) `git push`
6.) `git checkout -- .` <<< back to previous commit
7.) `git pull origin master` <<< get the latest commit version of the repo
8.) `git clone [repo .git]`
9.) `git remote -v` <<< check current repo origin 
10.) `git remote set-url origin [repo .git]` <<< set new origin for repo
11.) `git push origin master`
12.) `git log`
13.) `git show <show last comment>`
14.) `git reset <file_name>` <<< discard from latest git add
15.) `git checkout -- <file_name>` <<< change the file content to last commit
16.) `git mv <original_file_name> <new_file_name>`
17.) `git rm <file_name_to_be_removed>`
18.) `git diff `
19.) `git merge <branch_name_that_merge_to_current_branch>` <<< fast-forward merge(when no conflict)
20.) `git brand -d <branch_name>` <<< delete branch
21.) `git mergetool`
22.) `git tag <tag_name>`
23.) `git tag --list`
24.) `git stash`, then `git stash <stash_name>` <<< apply and drop last stash
25.) `git version`
26.) `git fetch || --all` <<< update branch from remove
27.) `git pull` <<< update branch and update local file too

```bash
git config --global user.name "Name"
git config --global user.email "youremail@address.com"
```
^^^ setup git info to let it know who is commit the repo

### Git Branch
> `git branch || -a` <<< list all the branches for the repo, the repo with * is the current working repo
> `git branch [branch name]` <<< create new branch
> `git checkout [branch name]` <<< switch to branch, after git commit, you can freely switch between branch to modify it
> `git checkout [master branch name]` > `git merge [branch to merge with master]` <<< merge branch with master
> `git push origin [branch name]`
> `git branch -d [branch name]` <<< delete repo branch
> `git checkout -b [branch name]` <<< create branch and switch over it

### GitHub Issues
1. Create issue in github
2. Can close by GUI in github, or terminal, where git commit -m "<message>, close <tag_id>" and push, github will auto detect and close the issue

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
