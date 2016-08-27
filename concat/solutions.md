# `concat`

[home](../README.md) &gt; [`concat`](./README.md) &gt; solutions

It seems easiest to check if the first argument is a String, and, if not, to assume it's an Array. This could be improved, of course. But this works.

```js
import { flatten, head, join } from 'ramda'

const concat = (...args) => typeof head(args) === 'string'
  ? join('', args)
  : flatten(args)

concat('abc', 'def')                 // returns 'abcdef'
concat(['a', 'b', 'c'], [1, 2, 3])   // returns ['a', 'b', 'c', 1, 2, 3]
```
