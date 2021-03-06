# binary-querystring

Query string parser, but computed values are binary, not strings.

> Because not all binary data is a valid string.

## Install

```bash
$ npm install binary-querystring
```

## Use

```js
const parse = require('binary-querystring')
const assert = require('assert')

const search = '?arg=some%20string&arg=%a3aacayeab%83%01%03%05ad%a1dffff%f4%00%01%02%03%04%05%06%07%08%09&stream-channels=true'

const qs = parse(search)

assert.deepEqual(qs, {
  arg: [
    Buffer.from('some string'),
    Buffer.from('a36161636179656162830103056164a16466666666f400010203040506070809', 'hex')
  ],
  'stream-channels': Buffer.from('true')
})
```

# License

MIT