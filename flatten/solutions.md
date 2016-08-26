# [flatten](./README.md)

```js
import { isArrayLike } from 'ramda'

const flatten = ([x, ...xs]) => {
  if (!x) { return [] }

  return isArrayLike(x)
    ? [...flatten(x), ...flatten(xs)]
    : [x, ...flatten(xs)]
}

flatten(['abc', [1, 2]])                // returns ["abc", 1, 2]
flatten([[1, 2], [3, 4, [5]], [6, 7]])  // returns [1, 2, 3, 4, 5, 6, 7]
```
