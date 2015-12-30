# johnnycache

> Cache file operations

[![Build Status][travis-image]][travis-url]
[![Code Quality][codeclimate-image]][codeclimate-url]
[![Code Coverage][coveralls-image]][coveralls-url]
[![NPM Version][npm-image]][npm-url]

## Install

```
$ npm install --save johnnycache
```


## Usage

```js
const Cache = require('johnnycache');
const exec = require('child-process-promise');

let cache = new Cache();

// this will be hella faster the second time around
cache.doCached(function () {
    return exec('npm install');
}, {
    input: 'package.json',
    output: ['node_modules/**/*']
});

```


## API

### johnnycache([options])

Constructor

#### options

##### workspace

Type: `type`  
Default: `path.join(process.cwd(), '.johnny')`

### johnnycache.doCached(run, options)

#### run

Type: `function`

A function that returns a promise for the file operation's completion

#### options

##### input

Type: `string|string[]`

A glob or an array of globs that indicate the files of which the hash should be calculated to check whether there is a cached version of the operation

##### output

Type: `string|string[]`

A glob or an array of globs that indicate the files that are produced as a result of the operation

##### action

Type: `string`

Default: Automatically generated string based on `input` and `output` arguments

Identifier for the operation

##### compress

Type: `boolean`

Default: `false`

Whether to gzip cached files

## License

MIT © [JM Versteeg](http://github.com/jmversteeg)

[![Build Status (Windows)][appveyor-image]][appveyor-url]
[![dependency Status][david-image]][david-url]
[![devDependency Status][david-dev-image]][david-dev-url]

[travis-image]: https://img.shields.io/travis/jmversteeg/johnnycache.svg?style=flat-square
[travis-url]: https://travis-ci.org/jmversteeg/johnnycache

[appveyor-image]: https://img.shields.io/appveyor/ci/jmversteeg/johnnycache.svg?style=flat-square&label=build+(Windows)
[appveyor-url]: https://ci.appveyor.com/project/jmversteeg/johnnycache

[codeclimate-image]: https://img.shields.io/codeclimate/github/jmversteeg/johnnycache.svg?style=flat-square
[codeclimate-url]: https://codeclimate.com/github/jmversteeg/johnnycache

[david-image]: https://img.shields.io/david/jmversteeg/johnnycache.svg?style=flat-square
[david-url]: https://david-dm.org/jmversteeg/johnnycache

[david-dev-image]: https://img.shields.io/david/dev/jmversteeg/johnnycache.svg?style=flat-square
[david-dev-url]: https://david-dm.org/jmversteeg/johnnycache#info=devDependencies

[coveralls-image]: https://img.shields.io/coveralls/jmversteeg/johnnycache.svg?style=flat-square
[coveralls-url]: https://coveralls.io/r/jmversteeg/johnnycache

[npm-image]: https://img.shields.io/npm/v/johnnycache.svg?style=flat-square
[npm-url]: https://www.npmjs.com/package/johnnycache
