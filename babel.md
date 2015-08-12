---
layout: page
title: Babel
permalink: /babel/
---

Babel.js is a command line tool that lets you transpile ES6 code into ES5 code that runs in current JavaScript environments, including Node.js and browsers.


## Quick Install

```bash
# To install globally
$ npm install -g babel

# to install locally per package
$ npm install --save-dev babel
```

Use `babel-node` for Node.js:

```bash
# Using Nod
$ babel-node
 Object.assign({}, {message: 'hell yeah\'});  // => { message: 'hell yeah!' }
```

You need `babel` and `browserify` if you want to run ES6 on browsers

```bash
$ npm install --save-dev babelify browserify
```

To use `Object.assign()` and `Object.is()`, etc. in browsers:

```bash
$ npm install --save core-js
```

At the top of your js file:

```js
require('core-js');
```

## Linting

Use ESLint to lint your code in ES6:

```bash
$ npm install --save-dev eslint
```

## Compiling

Compile ES6 code to ES5:

```bash
$ babel script.js --out-file script-compiled.js
```

To compile from a directory, use `-d` option:

```bash
$ babel -d build-dir source-dir
```

To setup debugger work properly:

```bash
$ babel -d build-dir source-dir -s
```

To compile for the browser, install `browserify` and `browser-run`.

```bash
npm install -g browserify browser-run
browserify -t babelify script.js | browser-run -p 8080
```

Compile a bundle:

```bash
$ browserify script.js -t babelify --outfile bundle.js
```

## Using Existing Modules

Import modules using ES6 syntax:

```js
import 'core-js'; // Node module
import harness from './harness'; // ES6 module
```

## Automation

Add to `package.json`:

```json

"scripts": {
  "lint": "eslint source",
  "clean": "rm -rf build/* && mkdir build/public && mkdir build/server && mkdir build/client",
  "build-server": "babel -d build/server source/server -s",
  "build-client": "browserify source/client/index.js -t babelify --outfile build/client/bundle.js",
  "build": "npm run clean && npm run build-server && npm build-client"
}
```

Reference:

* [How to Use ES6 for Universal JavaScript Apps](https://medium.com/javascript-scene/how-to-use-es6-for-isomorphic-javascript-apps-2a9c3abe5ea2)
