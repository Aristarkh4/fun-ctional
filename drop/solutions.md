# `drop`

[home](../README.md) &gt; [`drop`](./README.md) &gt; solutions

```js
import { reduce } from 'ramda'

const drop = (n, c) => {
  return reduce(
    ([x, xs], v) => (x > 0) ? [x - 1, xs] : [x, [...xs, v]],
    [n, []],
    c
  )[1]
}

const a = [1, 2, 3, 4, 5]
const b = [6, 7, 8, 9]

drop(0, a) // returns [1, 2, 3, 4, 5]
drop(3, a) // returns [4, 5]
drop(9, a) // returns []
```
