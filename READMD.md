# qparse

A top-down parser to turn advanced search query strings into JavaScript objects.

## Installation

```
# Using npm
npm install --save qparse

# Using yarn
yarn add qparse
```

## Usage

### parse(str, keywords)

Parse the given search string while matching the keywords.

```
const q = require('qparse');

> q.parse('tag:foo tag:bar sort:baz quz qux', ['tag', 'sort']);
{ text: 'quz qux', filters: { tag: [ 'foo', 'bar' ], sort: 'baz' } }

> q.parse('tag:foo tag:bar sort:baz quz qux', ['tag']);
{ text: 'sort:baz quz qux', filters: { tag: [ 'foo', 'bar' ] } }

> q.parse('tag:foo sort:baz quz qux', ['tag']);
{ text: 'sort:baz quz qux', filters: { tag: 'foo' } }

> q.parse('tag:foo sort:baz quz qux', []);
{ text: 'tag:foo sort:baz quz qux', filters: {} }
```

## LICENSE

Apache 2.0
