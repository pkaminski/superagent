# SuperAgent (with less suck) [![Build Status](https://travis-ci.org/kmalakoff/superagent-ls.svg?branch=master)](https://travis-ci.org/kmalakoff/superagent-ls)

[![Sauce Test Status](https://saucelabs.com/browser-matrix/kmalakoff.svg?auth=3aae5a49ad38f721960413eb2b0ff6e2)](https://saucelabs.com/u/kmalakoff)

SuperAgent is a small progressive __client-side__ HTTP request library, and __Node.js__ module with the same API, sporting many high-level HTTP client features. View the [docs](http://visionmedia.github.com/superagent/).

**FORK** this fork removes the suck introduced into superagent 1.x by returning the `end` api back to being compliant with node-style callback conventions as in the original superagent 0.x design. This fork will track official releases of superagent so everyone can benefit from improvements in superagent. The goal is merge this fork back into superagent and to retire this fork.

![super agent](http://f.cl.ly/items/3d282n3A0h0Z0K2w0q2a/Screenshot.png)

## Installation

node:

```
$ npm install superagent-ls
```

component:

```
$ component install kmalakoff/superagent-ls
```

Works with [browserify](https://github.com/substack/node-browserify) and should work with [webpack](https://github.com/visionmedia/superagent/wiki/Superagent-for-Webpack)

```js
request
  .post('/api/pet')
  .send({ name: 'Manny', species: 'cat' })
  .set('X-API-Key', 'foobar')
  .set('Accept', 'application/json')
  .end(function(err, res){

  });
```

## Supported browsers

Tested browsers:

- Latest Android
- Latest Firefox
- Latest Chrome
- IE9 through latest
- Latest iPhone
- Latest Safari

Even though IE9 is supported, a polyfill `window.btoa` is needed to use basic auth.

# Plugins

Superagent is easily extended via plugins.

```js
var nocache = require('no-cache');
var request = require('superagent-ls');
var prefix = require('superagent-prefix')('/static');

prefix(request); // Prefixes *all* requests

request
.get('/some-url')
.use(nocache) // Prevents caching of *only* this request
.end(function(res){
    // Do something
});
```

Existing plugins:
 * [superagent-no-cache](https://github.com/johntron/superagent-no-cache) - prevents caching by including Cache-Control header
 * [superagent-prefix](https://github.com/johntron/superagent-prefix) - prefixes absolute URLs (useful in test environment)

Please prefix your plugin with `superagent-*` so that it can easily be found by others.

For superagent extensions such as couchdb and oauth visit the [wiki](https://github.com/visionmedia/superagent/wiki).

## Running node tests

Install dependencies:

```shell
$ npm install
```
Run em!

```shell
$ make test
```

## Running browser tests

Install dependencies:

```shell
$ npm install
```

Start the test runner:

```shell
$ make test-browser-local
```

Visit `http://localhost:4000/__zuul` in your browser.

Edit tests and refresh your browser. You do not have to restart the test runner.

## License

MIT
