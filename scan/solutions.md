# `scan`

[home](../README.md) &gt; [`scan`](./README.md) &gt; solutions

```js
import { last, multiply, reduce } from 'ramda'

const scan = (f, a, c) => {
  return reduce(
    (acc, v) => [...acc, f(last(acc), v)],
    [a],
    c
  )
}

var numbers = [1, 2, 3, 4]

scan(multiply, 1, numbers)  // returns [1, 1, 2, 6, 24]
```
