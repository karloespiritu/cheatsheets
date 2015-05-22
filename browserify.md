---
layout: page
title: Browserify
permalink: /browserify/
---

## Browserify with Gulp

Browserify is a tool that lets you write client-side scripts like Node, letting you to use Node's package management system. It looks at a single JavaScript file, follows the `require` dependency tree, and bundles them into a single `js` file. Browserify can be used in the command line, or through its API using Node (with Gulp).

**Command Line**

Plain JavaScript

```bash
browserify app.js > bundle.js
```
Coffeescript

```bash
browserify -t coffeeify app.coffee > bundle.js
```
**gulpfile.js**

```js
var browserify = require('browserify');
var gulp = require('gulp');
var source = require('vinyl-source-stream');

gulp.task('browserify', function() {
    return browserify({ entries: ['assets/js/app.js'] })
        .bundle()
        .pipe(source('app.bundled.js'))
        .pipe(gulp.dest('dist'));
});
```