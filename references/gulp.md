Gulp <<< Automation
====
> npm install gulp-cli -g
> gulp -v
> npm install gulp --save-dev
- create gulpfile.js
gulp.src()
gulp.dest()
pipe()
plugins
> npm install gulp-watch --save-dev <<< watch files changes
> npm install gulp-postcss --save-dev
> npm install autoprefixer --save-dev
> npm install postcss-simple-vars --save-dev
> npm install postcss-nested --saved-dev
> npm install postcss-import --save-dev
> npm install browser-sync --save-dev

var watch = require('gulp-watch');
var postcss = require('gulp-postcss');
var autoprefixer = require('autoprefixer');
var cssvars = require('postcss-simple-vars');
var nested = require('postcss-nested');
var cssImport = require('postcss-import');
var browserSync = require('browser-sync').create();

gulp.task('watch', function() {
  watch('./app/index.css', function() {
    gulp.start('cssInject');
  });

  watch('./app/index.html', function() {
    browserSync.reload();
  });

  browserSync.inti({
    notify: false,
    server: {
      baseDir: 'app'
    }
  });
});

gulp.task('cssInject', ['style'], function() {
  return gulp.src('[css file]')
  .pipe(browserSync.stream());
});

gulp.task('style', function() {
  return gulp.src([source file])
	.pipe(postcss([cssImport, cssvars, nested, autoprefixer]))
        .on('error', function(errorInfo) {
	  console.log(errorInfo.toString());
	  this.emit('end');
	})
	.pipe(gulp.dest([dest file]));
});

> gulp watch

cssImport is to combine the @import [filename] into one file only. Noted that @import [filename] is native css module