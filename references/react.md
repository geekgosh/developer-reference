Project Structure
-----------------
1. Create public folder
2. Create index.html inside public folder
3. Create js folder inside public
4. Create main.js inside js folder
5. Create src folder
6. Create components folder inside src folder
7. Create main.jsx inside src folder
8. Create your own componnent inside components folders
9. Inside package.json "scripts" section, enter following code:
"start": "watchify src/main.jsx -v -t [ babelify --presets [ react ] ] -o public/js/main.js",

NPM cmd
-------
1. npm init
2. npm install -g browserify
3. npm install --save babelify
4. npm install --save
5. npm install --save babel-preset-react
6. npm install --save react
7. npm install --save react-dom
8. npm install --save create-react-class / react-create-class
9. npm start

Router
------
npm install history@1.13.1 react-router@latest --save / npm install --save react-router-dom

Local Server
------------
npm install -g http-server
http-server -p 7070

Fetch/Get Data from Server
--------------------------
npm install whatwg-fetch --save

Lodash
------
npm install lodash --save

Redux
-----
npm install redux --save

React-Redux
-----------
npm install react-redux --save

Redux-Promise
-------------
npm install redux-promise --save

------ Webpack (Skipped)
------ Redux-Saga (Skipped)

Tips
====
1. import React, { PureComponent } form 'react';
PureComponent same as the Component, but it will execute the shouldComponentUpdate() by default with looking whether any props or state is changed, if yes, then update, vice versa.

2. Correctly setState
this.setState(prevState, props) => {
	return {
		toggleClicked prevState.toggleClicked + 1;
	}
}

3. Check type of props
- npm install --save prop-types

import PropTypes from 'prop-types';

[ClassName].propTypes = {
	click: PropTypes.func,
	name: PropTypes.string,
	age: PropTypes.number,
	changed:  PropTypes.func	
};

4. Tiny combination
componentDidMount() {
	if(this.props.position === 0) {
		this.inputElement.focus();
	}
}

<input position={index} ref={(inp) => { this.inputElement = inp }}

5. Load route lazily, which mean load the page/component only when needed in Single Page Application
- Create a higher order component
e.g. asyncComponent.js

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

In other file
import asyncComponent from '[the path to asyncComponent.js]';

const AsyncNewPost = asyncComponent(() => {
	return import('./NewPost/NewPost');
});

<Route to="/newpost" component={AsyncNewPost} />

Done :)

Router
======
Tips
====
1.) To use as relative path
pathname: this.props.match.url + '/[next path]';

2.) Determine and style the current active link
import { NavLink } from 'react-router-dom';

Use <NavLink to='/'>Go</NavLink> instead of <Link to='/'>Go</Link>

Then, the active link will have the class "active" and aria-current="true"

You can also customized the added className by
<NavLink to='/' activeClassName='my-active'>Go</NavLink>

activeStyle={{ style }} can set inline style

3.) Pass it and extracting
Passing parameters:
<Route path="/:id" exact component={FullPost} />
<NavLink to={`/${post.id}`}>Go<NavLink>

Accessing parameters:
this.props.match.params.id

4.) Access to Single Route
import { Switch } from 'react-router-rom';

<Switch>
	<Route path="/" exact component={a} />
	<Route path="/new-post" component={b} />
	<Route path="/:id" exact component={c} />
</Switch>

This work by display only 1st match route

5.) Route can be put at anywhere, just need its parent element wrapped by BrowserRouter

6.) Nested Route use relative path
<Route path={this.props.match.url + '/:id'} exact component={abc} />

7.) When use nested route, you api might not refresh when you fecth the api inside componentDidMount() since it is update stage, therefore, you can also load the fetch api inside componentDidUpdate()

Note: history.push('/') allow click back to back, but Redirect are not able to do so.

8.) Redirecting Requests. Note: this.props.history.push('/') is preferred. If don't want allow to back, then use this.props.history.replace('/')
import { Redirect } from 'react-router-dom';

<Switch>
	<Route path="/new-post" component={b} />
	<Route path="/posts" component={b} />
	<Redirect from="/" to="/posts" />
</Switch>

Make achieve conditional redirect


render() {
	let redirect = null;

	if (this.state.submitted) {
		redirect = <Redirect to="/posts"  />;
	}	

	return (
		<div>
			...
			{ redirect }
			...
		</div>
	)
}

9.) To use this.props.history.push('/') by not importing { withRouter } from 'react-router-dom', just simple given the current element this.props property by
<Book {...props} ></Book>

8.) Handle 404 Error
<Route render={() => <h1>Not found</h1>} /> 
Remember, always come last

9.) To match with certain server when deployment, route needed to be modified to match correctly
<BrowserRouter basename="/my-app">
	
</BrowserRouter>

React Animation
===============
React Transition Group - Check out by yourself
React Motion
React Move
React Router Transition

CSS
===
Packages
========
1. npm install --save radium <<< allow pseudo selector and media queries in react

import Radium from 'radium';
export default Radium(App);

-------

To apply hover:

import Radium from 'radium'
const style = {
	backgroundColor: 'green',
	':hover': {
		backgroundColor: 'lightGreen'
	}
}
or 
style[':hover'] = {
	
}

<p className={style}></p>


To apply media queries:
import Radium, { StyleRoot } from 'radium'
const style = {
	'@media (min-width: 500px)': {
		width: '450px';
	}
}

<StyleRoot>
	<p className={style}></p>
</StyleRoot>


Tips
====
1. Access parent content (can be html markup)
Parent
import MyPhoto from './MyPhoto';
<MyPhoto>This is my photo</MyPhoto>
<MyPhoto><div className="lol">Haha</div></MyPhoto>

Child:
{this.props.children}

2. Preferred way to clone data in state
const persons = this.state.persons.slice();
or
const persons = [...this.state.persons];
or
const persons = Object.assign({}, this.state.persons); <<< traditional method

3. Dynamically assign class
const classes = [];

if() {
	classes.push('red');
}

if() {
	classes.push('bold');
}

<p className={classes.join('')}></p>

4. To achieve css modules(each css file bind to specify js only)
- npm run eject
go to config > webpack.config.development and prod, line around 162, saw test: /\.css, under options {}, add these lines

modules: true,
localIdentName: '[name]__[local]__[hash:base64:5]'

To use it
import classes from './App.css';
<div className={classes.myDiv}>Haha</div>

It can even figure out the style of selected class, e.g.
.App button.Red:hover {
	
}

const class_button = classes.Red;

Axios
=====
1. Axios interceptoprs to execute code globally
- Go to index.js

import axios from 'axios'

axios.interceptors.request.use(request => {
	console.log(request);

	// Edit request config
	return request;
}, error => {
	console.log(error);
	return Promise.reject(error);
});

2. Axios set default global configuration

- In the component files
axios.get('./posts'); <<< relatvie path

- In the index.js
axios.defaults.baseUrl = 'https://xxx.com'; <<< set base url for the request

others use case could be like
> axios.defaults.headers.common['Authorization'] = 'AUTH TOKEN';
axios.defaults.headers.post['Content-Type'] = 'application/json';

3. Creating and using axios instances
- Create seperate file for axios. e.g. axios.js

import axios from 'axios';

const instance = axios.create({
	baseURL: 'https://xxx.com'
});

instance.defaults.headers.common['Authorization'] = 'AUTH TOKEN FROM INSTANCE';

export default instance


- In the components file
import axios from 'the separate axios file';

3. Base practical if you create higher order components with axios, to remove it when not use

componentWillMount() {
	this.[yourVariable] = axios.interceptors.....
}

componentWillUnmount() {
	axios.interceptors.request.eject(this.[yourVariable]);
}

wes bos
=======
1. Fragment
===========
import React, { Fragment } from 'react';

<Fragment>

</Fragment

or event latest supports

<>

</>

2. Ref
======
username = React.createRef();

const user = {
  username: this.username.value.value
}

<input ref="username" type="text />

3. Form easy reset
==================
On the submit event of the form/button

event.currentTarget.reset();

4. Form easy get name
=====================
function xxx(event) {
  name = event.currentTarget.name;
}

<input name="username" type="text" />

component lifecycle
===================
Life Cycle
==========
1. Mounting - Run during first time rendering

In Order
--------

  i.) componentWillMount() <<< execute only once
 ii.) render() <<< ReactDOM.render() will execute this
iii.) componentDidMount() <<< take place(preferred) to make AJAX call, Web API, Javascript Framework, setInterval, setTimeout

2. Updating - A component updates every time that it renders, starting with the second render

In Order
--------

  i.) componentWillReceiveProps <<< get called only if receive props

  componentWillReceiveProps: function(nextProps) {
    if (nextProps.number > this.state.highest) {
      this.setState({
        highest: nextProps.number
      })
    }   
  }

 ii.) shouldComponentUpdate <<< after componentWillReceiveProps & rendering
       
        return true || false;
	True = proceed as usual
	False = component will not update, methods after would not execute(incl rendering)
	Argument(nextProps, nextState)

iii.) componentWillUpdate

      Argument(nextProps, nextState)
      Possible usage: checking window size, interacting with an API
 
iv.) render

  v.) componentDidUpdate
      
      Argument(prevProps, prevState)
      Possible usage: browser, API

	if (this.state.latestClick < prevState.latestClick) {
  		this.endGame();
	}

3. Unmounting
i.) componentWillUnmount

Argument(prevProps, prevState)
This could happen if the DOM is rerendered without the component, 
or if the user navigates to a different website or closes their web browser.