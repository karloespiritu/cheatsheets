---
layout: page
title: Webpack
permalink: /webpack/
---

## Quick Install

```bash
npm install -g webpack
```

## Running Webpack

Using a command line (equivalent to `browserify app.js > bundle.js`)

```bash
webpack app.js > bundle.js
```

Using a config file `webpack.config.js` in project root directory

```js
module.exports = {
    entry: "./entry.js",
    output: {
        path: __dirname,
        filename: "bundle.js"
    },
    module: {
        loaders: [
            { test: /\.css$/, loader: "style!css" }
        ]
    }
};
```

## Invoking Webpack

* `webpack` to make a build for development
* `webpack -p` to make a build for production (minified)
* `webpack --watch` for continuous incremental build in development
* `webpack -d` to include source maps

## Stylesheets & Images

```js
require('./bootstrap.css');
require('./app.less');

var img = document.createElement('img');
img.src = require('./logo.png');
```
When CSS (or less, etc) are required, webpack inlines the CSS as a string inside the JS bundle and require() will insert a `<style>` tag into the page.

For images, webpack inlines a URL to the image into the bundle and returns it from require().

```js
// webpack.config.js
module.exports = {
  entry: './main.js',
  output: {
    path: './build', // This is where images AND js will go
    publicPath: 'http://mycdn.com/', // This is used to generate URLs to e.g. images
    filename: 'bundle.js'
  },
  module: {
    loaders: [
      { test: /\.less$/, loader: 'style-loader!css-loader!less-loader' }, // use ! to chain loaders
      { test: /\.css$/, loader: 'style-loader!css-loader' },
      {test: /\.(png|jpg)$/, loader: 'url-loader?limit=8192'} // inline base64 URLs for <=8k images, direct URLs for the rest
    ]
  }
};
```

## Feature Flags

```js
// webpack.config.js
// definePlugin takes raw strings and inserts them, so you can put strings of JS if you want.
var definePlugin = new webpack.DefinePlugin({
  __DEV__: JSON.stringify(JSON.parse(process.env.BUILD_DEV || 'true')),
  __PRERELEASE__: JSON.stringify(JSON.parse(process.env.BUILD_PRERELEASE || 'false'))
});

module.exports = {
  entry: './app.js',
  output: {
    filename: 'bundle.js'
  },
  plugins: [definePlugin]
};
```

Then run build with `BUILD_DEV=1 BUILD_PRERELEASE=1 webpack` from the terminal.

## Multiple Entrypoints

Let's say you have a profile page and a feed page. You don't want to make the user download the code for the feed if they just want the profile. So make multiple bundles: create one "main module" (called an entrypoint) per page:

```
// webpack.config.js
module.exports = {
  entry: {
    Profile: './profile.js',
    Feed: './feed.js'
  },
  output: {
    path: 'build',
    filename: '[name].js' // Template based on keys in entry above
  }
};
```

For profile, insert <script src="build/Profile.js"></script> into your page. Do a similar thing for feed.

## Optimising Common Code

Webpack can figure out what two pages have in common and make a shared bundle that can be cached between pages:

```js
// webpack.config.js

var webpack = require('webpack');

var commonsPlugin =
  new webpack.optimize.CommonsChunkPlugin('common.js');

module.exports = {
  entry: {
    Profile: './profile.js',
    Feed: './feed.js'
  },
  output: {
    path: 'build',
    filename: '[name].js' // Template based on keys in entry above
  },
  plugins: [commonsPlugin]
};
```

Add `<script src="build/common.js"></script>` before the script tag you added in the previous step and enjoy the free caching.

## Async Loading

CommonJS is synchronous but webpack provides a way to asynchronously specify dependencies. This is useful for client-side routers, where you want the router on every page, but you don't want to have to download features until you actually need them.

Specify the split point where you want to load asynchronously. For example:

```js
if (window.location.pathname === '/feed') {
  showLoadingState();
  require.ensure([], function() { // this syntax is weird but it works
    hideLoadingState();
    require('./feed').show(); // when this function is called, the module is guaranteed to be synchronously available.
  });
} else if (window.location.pathname === '/profile') {
  showLoadingState();
  require.ensure([], function() {
    hideLoadingState();
    require('./profile').show();
  });
}
```

Webpack will do the rest and generate extra chunk files and load them for you.

Webpack will assume that those files are in your root directory when you load then into a html script tag for example. You can use `output.publicPath` to configure that.

```js
// webpack.config.js
output: {
    path: "/var/www/public/assets", //path to where webpack will build your stuff
    publicPath: "/assets/" //path that will be considered when requiring your files
}
```

## Development Server

```js
npm install webpack-dev-server -g
```

This will install a small express server on `localhost:8080` which serves your static assets as well as the bundle (compiled automatically). It automatically updates the browser page when a bundle is recompiled (socket.io). Open `http://localhost:8080/webpack-dev-server/bundle` in your browser.

> The dev server uses webpack’s watch mode. It also prevents webpack from emitting the resulting
> files to disk. Instead it keeps and serves the resulting files from memory.

References:

* [Webpack Howto](https://github.com/petehunt/webpack-howto)
* [Webpack Official Site](http://webpack.github.io)
