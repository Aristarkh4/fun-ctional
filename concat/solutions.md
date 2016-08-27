# `concat`

[home](../README.md) &gt; [`concat`](./README.md) &gt; solutions

```js
import { flatten, head, join } from 'ramda'

const concat = (...args) => {
  return typeof head(args) === 'string'
    ? join('', args)
    : flatten(args)
}

concat('abc', 'def')                 // returns 'abcdef'
concat(['a', 'b', 'c'], [1, 2, 3])   // returns ['a', 'b', 'c', 1, 2, 3]
```
