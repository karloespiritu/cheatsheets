---
layout: page
title: Gulp
permalink: /gulp/
---

## Install Gulp plugins

```bash
npm install --save-dev gulp-jshint \
                      gulp-sass \
                      gulp-concat \
                      gulp-uglify \
                      gulp-rename \
                      gulp-clean \
                      gulp-imagemin \
                      gulp-minify-css \
                      gulp-sourcemaps \
                      gulp-cache

```

## Gulpfile.js

```js
// Include gulp
var gulp = require('gulp');

// Include plugins
var jshint = require('gulp-jshint');
var sass = require('gulp-sass');
var concat = require('gulp-concat');
var uglify = require('gulp-uglify');
var rename = require('gulp-rename');
var clean = require('gulp-clean');
var imagemin = require('gulp-imagemin');
var minifyCss = require('gulp-minify-css');
var sourceMaps = require('gulp-sourcemaps');
var cache = require('gulp-cache');


var paths = {
  scripts: ['assets/js/**/*.js'],
  images: 'assets/images/**/*',
  sass: 'assets/sass/**/*'
};

// Lint Task
gulp.task('lint', function() {
    return gulp.src(paths.scripts)
        .pipe(jshint())
        .pipe(jshint.reporter('default'));
});

// Compile Our Sass
gulp.task('sass', function() {
    return gulp.src(paths.sass)
        .pipe(sass({ style: 'expanded' }))
        .pipe(gulp.dest('dist/css'))
        .pipe(rename({ suffix: '.min' }))
        .pipe(minifyCss())
        .pipe(sourceMaps.write())
        .pipe(gulp.dest('dist/css'));
});

// Concatenate & Minify JS
gulp.task('scripts', function() {
    return gulp.src(paths.scripts)
        .pipe(concat('scripts.js'))
        .pipe(gulp.dest('dist/js'))
        .pipe(rename({ suffix: '.min' }))
        .pipe(uglify())
        .pipe(gulp.dest('dist/js'));
});

// Images
gulp.task('imagemin', function() {
  return gulp.src(paths.images)
    .pipe(cache(imagemin({ optimizationLevel: 3, progressive: true, interlaced: true })))
    .pipe(gulp.dest('dist/images'));
});

// Clean
gulp.task('clean', function() {
  return gulp.src(['dist/css', 'dist/js', 'dist/images'], {read: false})
    .pipe(clean());
});

// Watch Files For Changes
gulp.task('watch', function() {
    gulp.watch(paths.scripts, ['scripts']);
    gulp.watch(paths.sass, ['sass']);
    gulp.watch(paths.images, ['imagemin']);
});

// Default Task
gulp.task('default', ['watch', 'sass', 'imagemin', 'scripts']);
```