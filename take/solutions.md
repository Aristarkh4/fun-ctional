# `take`

[home](../README.md) &gt; [`take`](./README.md) &gt; solutions

```js
import { reduce } from 'ramda'

const take = (n, c) => {
  return reduce(
    ([x, xs], v) => (x > 0) ? [x - 1, [...xs, v]] : [x, xs],
    [n, []],
    c
  )[1]
}

const a = [1, 2, 3, 4, 5]
const b = [6, 7, 8, 9]

take(0, a) // returns []
take(3, a) // returns [1, 2, 3]
take(9, a) // returns [1, 2, 3, 4, 5]
```
