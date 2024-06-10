#@taktikorg/ratione-saepe-ipsum <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

[![browser support][testling-svg]][testling-url]

An ES5 spec-compliant `Array.prototype.some` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://www.ecma-international.org/ecma-262/6.0/).

Because `Array.prototype.some` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var some = require('@taktikorg/ratione-saepe-ipsum');
var assert = require('assert');

assert.equal(true, some([1, 2, 3], function (x) { return x === 2; }));
assert.equal(false, some([1, 2, 3], function (x) { return x === 4; }));
```

```js
var some = require('@taktikorg/ratione-saepe-ipsum');
var assert = require('assert');
/* when Array#some is not present */
delete Array.prototype.some;
var shimmedSome = some.shim();
assert.equal(shimmedSome, some.getPolyfill());
var arr = [1, 2, 3];
var threeOrLarger = function (x) { return x >= 3; };
assert.deepEqual(arr.some(threeOrLarger), some(arr, threeOrLarger));
```

```js
var some = require('@taktikorg/ratione-saepe-ipsum');
var assert = require('assert');
/* when Array#some is present */
var shimmedSome = some.shim();
assert.equal(shimmedSome, Array.prototype.some);
assert.deepEqual(arr.some(threeOrLarger), some(arr, threeOrLarger));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@taktikorg/ratione-saepe-ipsum
[npm-version-svg]: https://versionbadg.es/taktikorg/ratione-saepe-ipsum.svg
[deps-svg]: https://david-dm.org/taktikorg/ratione-saepe-ipsum.svg
[deps-url]: https://david-dm.org/taktikorg/ratione-saepe-ipsum
[dev-deps-svg]: https://david-dm.org/taktikorg/ratione-saepe-ipsum/dev-status.svg
[dev-deps-url]: https://david-dm.org/taktikorg/ratione-saepe-ipsum#info=devDependencies
[testling-svg]: https://ci.testling.com/taktikorg/ratione-saepe-ipsum.png
[testling-url]: https://ci.testling.com/taktikorg/ratione-saepe-ipsum
[npm-badge-png]: https://nodei.co/npm/@taktikorg/ratione-saepe-ipsum.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@taktikorg/ratione-saepe-ipsum.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@taktikorg/ratione-saepe-ipsum.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@taktikorg/ratione-saepe-ipsum
[codecov-image]: https://codecov.io/gh/taktikorg/ratione-saepe-ipsum/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/taktikorg/ratione-saepe-ipsum/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/taktikorg/ratione-saepe-ipsum
[actions-url]: https://github.com/taktikorg/ratione-saepe-ipsum/actions
