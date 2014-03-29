gulp-expand-url
========================

Expands a url inside a file using the file relative path.

## Usage

    var gulp = require('gulp');
    var expandUrl = require('gulp-expand-url');

    gulp.task('templates', function () {
      gulp.src('src/my-module/input.tpl.html')
        .pipe(expandUrl({ type: 'imgSrc', root: 'images' }))
        .pipe(gulp.dest('dist'));
    });

**input:** `src/my-module/input.tpl.html`

    <img alt="Hello World" src="hello-world.gif" />

**ouput:** `dist/my-module/input.tpl.html`

    <img alt="Hello World" src="images/my-module/hello-world.gif" />

## Options

### option.regexp

Type: `RegExp`  
Default: `null`  
_**required**_

The regular expression to use to match the path, the replacement character should
be the first subexpression.

### option.type

Type: `string`  
Default: `''`  
Available: `['templateUrl', 'imgSrc']`  
_optional_

Predefined regular expressions.

### option.root

Type: `string`  
Default: `''`  
_optional_

The root or prefix for the path.

### option.sep

Type: `string`  
Default: `'/'`  
_optional_

The url segment separator

## Examples

If you wanted to add a full http url to a list of images.

    gulp.task('templates', function () {
      gulp.src('src/**/*.tpl.html')
        .pipe(expandUrl({ type: 'imgSrc', root: 'http://my-domain.com/images' }))
        .pipe(gulp.dest('dist'));
    });

**input:** `src/my-module/input.tpl.html`

    <img alt="Hello World" src="hello-world.gif" />

**ouput:** `dist/my-module/input.tpl.html`

    <img alt="Hello World" src="http://my-domain.com/images/my-module/hello-world.gif" />

