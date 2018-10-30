Webpack
=======
> npm install webpack --save-dev
> npm install webpack-cli --save-dev
- Create file name "webpack.config.js", customize own settings
- Create scripts "build": "webpack"

Dependency --save-dev
=====================
> babel-loader <<< Teaches babel how to work with webpack
> babel-core <<< Knows how to take in code, parse it, and generate some output files
> babel-preset-env <<< Ruleset for telling babel exactly what pieces of ES2015/6/7 syntax to look for, and how to turn it into ES5 code
- create .babelrc

> css-loader <<< Know how to deal with CSS imports
> style-loader <<< Take CSS imports and adds them to the HTML document

> extract-text-webpack-plugin@4.0.0-alpha.0 <<< Try using latest version at first

> file-loader
> image-webpack-loader
> url-loader

> webpack-dev-server <<< auto build for each file js file changes (Exclude webpack.config.js)
- create script with "webpack-dev-server"

Deployment with Surge
==================================
> surge <<< publish static site to surge instantly
surge -p [directory to publish]
E.g. surge -p dist

Deployment with Github Pages
===================================
1. New repository (Repo name affect url link)
2. > git init
3. > git add .
4. > git commit -m "[message]"
5. > git remote add origin [ssh given]
6. > git checkout -b gh-pages <<< Note: any github branch name 'gh-pages' will auto surf at https:<username>.github.io/<repo name>
7. > git subtree push --prefix dist origin gh-pages

To make it easier for deployment
Package.json > script > "deploy:github": "npm run build && git subtree push --prefix dist origin gh-pages"

Deployment with AWS S3
===================================
1. > npm install -g s3-website
2. Go to AWS > your name > security credentials > access key > create new access key
3. Create .env file
AWS_ACCESS_KEY_ID=xxx
AWS_SECRET_ACCESS_KEY=xxx
4. s3-websie create [bucket name]
5. s3-website deploy dist

Other Course
============
Webpack
=======
> npm install babel-core babel-loader babel-preset-es2015 --save-dev
- createa file name "webpack.config.js"

var path = require('path');

module.exports = {
	entry: "./app/assets/scripts/App.js",
	output: {
		path: path.resolve(__dirname, "./app/temp/scripts");
		filename: "App.js"
	},
	module: {
		loaders: [
			loader: 'babel-loader',
			query: {
				presets: ['es2015']
			},
			test: /\.js$/,
			exclude: /node_modules/
		]
	}
}

> webpack