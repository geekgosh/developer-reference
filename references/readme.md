Performance
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

Security
7. Free HTTPS - Let's Encrypt
8. CDN - Cloudflare
9. NPM package named "nsp" and "snyk" - good for checking npm package security
10. Logging package named "morgan" and "winston"
11. Https everywhere - sanitize input, no eval(), no document.write(), content security policy, secure + HTTPOnly Cookies
12. Code Secret - Environment variable, commit history
13. Secure Headers - npm package "helmet"
14. Access Control (Give least privilege) - npm package "cors"
15. Data Management - bcrypt, scrypt, Aragon2 & pgcrypto

IT news
1. OWASP - IT Security

Others
1. Prettier - can use in precommit

Web Hosting List
================
1. Now
2. Heroku
3. Digital Ocean

Nodejs Template
===============
1. Pug (previosly known as Jade)
2. Mustache
3. EJS

Nodejs Https Package
====================
1. Node-fetch
2. isomorphic-fetch
3. Axios

Good NPM Package
================
1. body-parser

Node.js
=======
1. Node.js Thread - Recommended (Used only when there are good reasons)
- Some methods using Thread Pool (default 4 threads) - e.g. fs module and crypto
- Some methods using OS process - e.g. https
- So they are not stop any of each type. But thread will need to wait as always
- Tricks: SET UV_THREADPOOL_SIZE=1 can set the number of threads in thread pool, use it wisely

2. Nodejs Create thread
const cluster = require('cluster');
npm install -g pm2 - multiple cluster for process

3. Node.js Worker Threads - Experimental stage for current IT trends
npm install --save webworker-threads

4. For any function which using callback, can change to async await
E.g. with redis

const util = require('util');
client.get = util.promisify(client.get);

const cahced = await client.get(id);

Node.js Package
===============
axios
body-parser
concurrently
dotenv
express
faker
multer
webpack
nodemon
bcrypt-nodejs
passport
jest
redis
jsonwebtoken
express-http-proxy
npm-run-all
serialize-javascript

React Package
=============
react
react-dom
enzyme
react-redux
redux
redux-logger
redux-thunk
react-helmet
react-router-config

Others
======
passport-google-oauth20 <<< google+ login
cookie-session <<< cookie session for user logged in information
concurrently <<< concurrently run script
materialize-css <<< great material design css framework
react-stripe-checkout <<< credit card payment (front end)
stripe <<< credit card payment for nodejs (backend)
sendgrid <<< mailer
localtunnel <<< web to localhost
 passport passport-jwt passport-local <<< not sure is what, but is authenticate cookies
jsonwebtoken <<< json web token || jwt-simple
bcryptjs <<< encrypt || bcrypt-nodejs

Javascript Pattern
==================
1. Module Pattern
2. Singleton Pattern
3. Factory Pattern
4. Observer Pattern
5. Mediator Pattern
6. State Pattern
7. SOLID Pattern

Docker CheatSheet
=================
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

Create custom docker image
--------------------------
1. Create file named "Dockerfile", and put configuration inside
2. docker build .
2. docker build -t <your_docker_id>/<container_name>:<version> . - (with custom image tags)
3. docker run <container_id>

# docker run with port mapping incoming port:port inside container
- docker run -p 8080:8080 <image_id>
- docker run -it <image_id> sh - (go into shell)

Docker readme
-------------
1. docker wil remember the order in docker file and cache if it is the same, so don't move the order if can

docker compose
--------------
- docker-compose ps >>> list all docker compose
- docker-compose up >>> docker run <image>
- docker-compose up -d >>> run in background
- docker-compose up --build >> docker build. && docker run <image>

For PWA
=======
1. npm install -g serve <-- allow simulator launch project
2. serve -s build <-- give you the address to launch the project in simulator

Things to explore
=================
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