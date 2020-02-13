# qparse

[![Build Status](https://travis-ci.org/sungwoncho/qparse.svg?branch=master)](https://travis-ci.org/sungwoncho/qparse)

A top-down parser to turn advanced search query strings into JavaScript objects.

It has *no dependency* and provides *a simple interface* with *readable implementation*.

## Installation

```bash
# Using npm
npm install --save qparse

# Using yarn
yarn add qparse
```

## Usage

### parse(str, keywords)

Parse the given `str` while matching the `keywords`.

```js
const q = require('qparse');

q.parse('tag:foo tag:bar sort:baz quz qux', ['tag', 'sort']);
// => { text: 'quz qux', filters: { tag: [ 'foo', 'bar' ], sort: 'baz' } }

q.parse('tag:foo tag:bar sort:baz quz qux', ['tag']);
// => { text: 'sort:baz quz qux', filters: { tag: [ 'foo', 'bar' ] } }

q.parse('tag:foo sort:baz quz qux', ['tag']);
// => { text: 'sort:baz quz qux', filters: { tag: 'foo' } }

q.parse('tag:foo sort:baz quz qux', []);
// => { text: 'tag:foo sort:baz quz qux', filters: {} }
```

## Real World Example

Used by [Dnote](https://github.com/dnote/dnote).

## LICENSE

Apache 2.0
