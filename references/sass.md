Tips
====
1. Search for clip path maker
2. To install sass and run it
> npm install node-sass --save-dev
- Under package.json > scripts
 "complie:sass": "node-sass sass/main.scss css/style.css" <<< add -w can watch the file changes and compile directly
 "complie:sass": "node-sass [input sass file] [output css file]"

3. To auto reload browser when file changes
> npm install live-server -g
- Command line Interface go to main directory
> live-server

4. Guidelines for CSS and SASS
> CSS Naming BEM
> SASS 7 - 1 Pattern

5. coverr.co <<< Great animation video for background

6. sizzy <<< to test website in various devices

7. 
min-resolution: 192dpi) and (min-width: 37.5em)
^^^ For Windows

(-webkit-min-deivce-pixel-ratio: 2) and (min-width: 37.5em)
^^^ For OS X

8. Four Steps of CSS Building
- Compilation
- Concatenation
- Prefixing
- Compressing

npm install concat --save-dev
npm install autoprefixer --save-dev
npm install postcss-cli --save-dev
npm install node-sass --save-dev
npm install npm-run-all --save-dev


Under Script
------------

"compile:sass": "node-sass sass/main.scss css/style.comp.css",
"concat:css": "concat -o css/style.concat.css css/icon-font.css css/style.comp.css",
"prefix:css": "postcss --use autoprefixer -b \"last 10 versions\" css/style.concat.css -o css/style.prefix.css",
"compress:css": "node-sass css/style.prefix.css css/style.css --output-style compressed",
"build:css": "npm-run-all compile:sass concat:css prefix:css compress:css"

> npm run build:css

9. Another use case of npm-run-all
"devserver": "live-server",
"start": "npm-run-all --parallel devserver watch:sass",

10.) icomoon.io <<< Free SVG Icon

11.) Best way to use SVG Icon
<svg class="search__icon">
    <use xlink:href="img/sprite.svg#icon-manifying-glass"></use>
</svg>

Syntax
======
1.) Variable
$color-primary: #f9ed9;
background-color: $color-primary;

2.) Style for nested element
For CSS
.navigation {
	xxx
}

.navigation li {
	xxx
}

For SASS
.navigation {
	xxxx

	li {
		xxx
	}
}

However, for pseudo element, need to add & in front
E.g.
.navigation {
	xxxx

	&:last-child {
		xxx
	}
}

3.) Dynamically darken or lighten color
// (color, percentage)
background-color: darken($color-primary, 15%);
background-color: lighten($color-primary, 15%);

4.) Mixin
@mixin clearfix {
	&::after {
		content: '';
		clear: both;
		display: table;
	}
}

To use it
.container {
	@include clearfix;
}

Mixin also allow arguments
@mixin abcstyle($color) {
	background-color: $color;
}

To use it
.container {
	@include abcstyle(#fff);
}

4.) Function
@function divide($a, $b) {
	@return $a / $b;
}

To use it
.container {
	margin: divide(50, 2) * 1px;
}

5.) Extend
%btn-placeholder {
	background-color: 'black';
	padding: 10px;
}

To use it
.btn:link {
	@extend %btn-placeholder;
}

5.) To use media queries efficiently
- Create a mixin
@mixin respond($breakpoint) {
	@if $breakpoint == phone {
		@media only screen and (max-width: 37.5em) { @content }
	}

	@if $breakpoint == tab-port {
		@media only screen and (max-width: 56.25em) { @content }
	}

	@if $breakpoint == tab-land {
		@media only screen and (max-width: 75em) { @content }
	}

	@if $breakpoint == big-desktop {
		@media only screen and (min-width: 112.5em) { @content }
	}
}

- Use it in elements
@include respond(tab-port) {
	width: 100% !important;
}

Tips
====
1.) Comment using // instead of /**/