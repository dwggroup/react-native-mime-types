# mime-types

> forked from https://github.com/Liroo/react-native-mime-types
> 
> Changed typings + GH Package deployment

[![NPM Version][npm-image]][npm-url]
[![NPM Downloads][downloads-image]][downloads-url]
[![Node.js Version][node-version-image]][node-version-url]
[![Build Status][travis-image]][travis-url]
[![Test Coverage][coveralls-image]][coveralls-url]

The ultimate javascript content-type utility.

Similar to [node-mime](https://github.com/broofa/node-mime), except:

- __No fallbacks.__ Instead of naively returning the first available type, `mime-types` simply returns `false`,
  so do `var type = mime.lookup('unrecognized') || 'application/octet-stream'`.
- No `new Mime()` business, so you could do `var lookup = require('mime-types').lookup`.
- Additional mime types are added such as jade and stylus via [mime-db](https://github.com/jshttp/mime-db)
- No `.define()` functionality

Otherwise, the API is compatible.

## Install

`.npmrc`

```
@dwggroup:registry=https://npm.pkg.github.com/
```

```sh
$ yarn add @dwggroup/react-native-mime-types
```

## Adding Types

All mime types are based on [mime-db](https://github.com/jshttp/mime-db),
so open a PR there if you'd like to add mime types.

## API

```js
import * as mime from '@dwggroup/react-native-mime-types';
```

All functions return `false` if input is invalid or not found.

### mime.lookup(path)

Lookup the content-type associated with a file.

```js
mime.lookup('json')             // 'application/json'
mime.lookup('.md')              // 'text/x-markdown'
mime.lookup('file.html')        // 'text/html'
mime.lookup('folder/file.js')   // 'application/javascript'
mime.lookup('folder/.htaccess') // false

mime.lookup('cats') // false
```

### mime.contentType(type)

Create a full content-type header given a content-type or extension.

```js
mime.contentType('markdown')  // 'text/x-markdown; charset=utf-8'
mime.contentType('file.json') // 'application/json; charset=utf-8'

// from a full path
mime.contentType(path.extname('/path/to/file.json')) // 'application/json; charset=utf-8'
```

### mime.extension(type)

Get the default extension for a content-type.

```js
mime.extension('application/octet-stream') // 'bin'
```

### mime.charset(type)

Lookup the implied default charset of a content-type.

```js
mime.charset('text/x-markdown') // 'UTF-8'
```

### var type = mime.types[extension]

A map of content-types by extension.

### [extensions...] = mime.extensions[type]

A map of extensions by content-type.

## License

[MIT](LICENSE)

[npm-image]: https://img.shields.io/npm/v/react-native-mime-types.svg
[npm-url]: https://npmjs.org/package/react-native-mime-types
[node-version-image]: https://img.shields.io/node/v/react-native-mime-types.svg
[node-version-url]: https://nodejs.org/en/download/
[travis-image]: https://img.shields.io/travis/jshttp/mime-types/master.svg
[travis-url]: https://travis-ci.org/jshttp/mime-types
[coveralls-image]: https://img.shields.io/coveralls/jshttp/mime-types/master.svg
[coveralls-url]: https://coveralls.io/r/jshttp/mime-types
[downloads-image]: https://img.shields.io/npm/dm/react-native-mime-types.svg
[downloads-url]: https://npmjs.org/package/react-native-mime-types
